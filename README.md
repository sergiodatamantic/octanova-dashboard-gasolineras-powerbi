OCTANOVA
--------

Dashboard interactivo en Power BI de precios de carburantes en España, construido sobre los datos abiertos del MITECO. Encuentra la gasolinera mas barata dentro de un radio determinado desde tu ubicacion, pensado para camioneros, empresas con flota de vehiculos, y cualquier conductor que quiera ahorrar en cada repostaje.

Proyecto de portfolio, demo funcional, no un servicio en produccion. El archivo octanova.pbix es descargable y se abre con Power BI Desktop (gratuito): https://powerbi.microsoft.com/desktop/

Que resuelve
------------

Los precios de combustible en España varian bastante de una gasolinera a otra, incluso dentro de la misma zona. Octanova responde a una pregunta muy concreta: cual es la gasolinera mas barata cerca de mi, ahora mismo, y lo hace filtrando por tipo de combustible y por el territorio real donde te encuentras, incluyendo Baleares, Canarias, Ceuta y Melilla, no solo la Peninsula.

Funcionalidades
----------------

- Busqueda por radio: selecciona tu provincia/municipio de referencia y un radio en km; el informe calcula la distancia real a cada gasolinera (formula de Haversine) y muestra solo las que caen dentro de ese radio.
- Categorizacion de combustible: agrupa automaticamente decenas de variantes de producto (Gasolina 95, 95 E5 Premium, Gasoleo A, Adblue...) en categorias utiles (Gasolina, Diesel, Bio, Gases), para no tener que elegir entre 20 opciones casi identicas.
- Clasificacion geografica oficial: cada estacion se clasifica por Territorio (Peninsula / Baleares / Canarias / Ceuta / Melilla) a partir del codigo postal, y por isla concreta (Baleares/Canarias) cruzando el municipio con el nomenclator oficial del INE.
- Mapa interactivo coloreado por precio: visualizacion geografica (ArcGIS) donde el color indica el precio, sin depender de una escala roja/verde, para que sea legible tambien con daltonismo.
- Enlace directo a Google Maps por cada estacion, para abrir la ruta con un clic.
- Filtros con reinicio de un clic: botones de borrar seleccion por pagina, para cambiar rapido de zona o combustible sin tener que deseleccionar uno a uno.
- Pagina dedicada a fuera de Peninsula: busqueda especifica por isla para Baleares y Canarias, y por ciudad para Ceuta/Melilla.

Detalles tecnicos
------------------

Origen de datos: API publica del MITECO (Ministerio para la Transicion Ecologica), consultada via Power Query. https://www.miteco.gob.es/

Modelo de datos: tablas desconectadas para el patron punto de referencia + radio (evita que el filtro de distancia contamine el resto del modelo), y una tabla de referencia del INE (municipio a isla) integrada directamente en el pbix mediante Introducir datos, sin depender de ningun origen externo.

DAX: columnas calculadas con SWITCH y SEARCH para la categorizacion de combustible, LEFT y FORMAT sobre el codigo postal para la clasificacion territorial (con cuidado de no perder ceros a la izquierda en Baleares), LOOKUPVALUE para la isla, y Haversine completo para la distancia real entre coordenadas.

Diseno visual: paleta de color validada para daltonismo (separacion CVD verificada con herramienta propia), pensada para leerse con un vistazo rapido en carretera, funcional antes que decorativa.

Como verlo
----------

1. Descarga octanova.pbix de este repositorio.
2. Abrelo con Power BI Desktop (gratis).
3. Los datos se actualizan manualmente desde Power Query. Este es un proyecto de demostracion, no un servicio con datos en vivo.

Sobre el proyecto
------------------

Octanova es mi proyecto insignia dentro de mi transicion de Workforce Management / Real Time hacia un rol de datos y BI. Mas contexto sobre mi perfil y el resto de mi trabajo en datamantic: https://github.com/datamantic

Sergio Vilanova Salido
LinkedIn: https://www.linkedin.com/in/sergio-vilanova/
GitHub: https://github.com/datamantic


================================================================


OCTANOVA (English)
-------------------

Interactive Power BI dashboard for Spanish fuel prices, built on open data from MITECO (Spain's Ministry for Ecological Transition). Find the cheapest fuel station within a given radius of your location. Built for truck drivers, fleet-owning businesses, and everyday drivers looking for the best price.

Portfolio project, working demo, not a production service. The file octanova.pbix is downloadable and opens with Power BI Desktop (free): https://powerbi.microsoft.com/desktop/

What it solves
---------------

Fuel prices in Spain vary a lot from one station to another, even within the same area. Octanova answers one specific question: which is the cheapest fuel station near me, right now, filtering by fuel type and by the actual territory you are in, including the Balearic Islands, Canary Islands, Ceuta and Melilla, not just mainland Spain.

Features
--------

- Radius search: pick a reference province/municipality and a radius in km; the report calculates the real distance to each station (Haversine formula) and shows only the ones within that radius.
- Fuel type grouping: automatically groups dozens of product variants (Gasolina 95, 95 E5 Premium, Gasoleo A, Adblue...) into useful categories (Petrol, Diesel, Bio, Gas), instead of choosing between 20 near-identical options.
- Official geographic classification: each station is classified by Territory (Mainland / Balearic Islands / Canary Islands / Ceuta / Melilla) from its postal code, and by specific island (Balearic/Canary) by matching the municipality against Spain's official INE gazetteer.
- Interactive map colored by price: geographic visualization (ArcGIS) where color encodes price, without relying on a red/green scale, so it stays readable for color-blind users too.
- Direct Google Maps link for each station, to open directions in one click.
- One-click filter resets: clear-selection buttons per page, to switch zone or fuel type quickly without deselecting one by one.
- Dedicated page for outside mainland Spain: specific search by island for the Balearic and Canary Islands, and by city for Ceuta/Melilla.

Technical details
------------------

Data source: MITECO public API (Spain's Ministry for Ecological Transition), queried via Power Query. https://www.miteco.gob.es/

Data model: disconnected tables for the reference-point-plus-radius pattern (keeps the distance filter from affecting the rest of the model), and an INE reference table (municipality to island) embedded directly in the pbix via Enter Data, with no external dependency.

DAX: calculated columns using SWITCH and SEARCH for fuel type grouping, LEFT and FORMAT on the postal code for territory classification (careful not to lose leading zeros for the Balearic Islands), LOOKUPVALUE for the island, and a full Haversine formula for real distance between coordinates.

Visual design: a colorblind-validated color palette (CVD separation verified with a purpose-built tool), designed to be read at a glance while driving, function before decoration.

How to view it
----------------

1. Download octanova.pbix from this repository.
2. Open it with Power BI Desktop (free).
3. Data is refreshed manually via Power Query. This is a demo project, not a live data service.

About the project
-------------------

Octanova is my flagship portfolio project as part of my transition from Workforce Management / Real Time into a data and BI role. More context on my background and the rest of my work at datamantic: https://github.com/datamantic

Sergio Vilanova Salido
LinkedIn: https://www.linkedin.com/in/sergio-vilanova/
GitHub: https://github.com/datamantic**
