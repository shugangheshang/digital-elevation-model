# Digital Elevation Model Tools

This is the **Python** implemented tools of processing **Digital Elevation Model (DEM)**.

### Important Terms and Abbrevations:

| Term                                   | Abbrevation | Remark 
| -------------------------------------- | :---------: | :----: 
| Digital Elevation Model                | DEM         | 
| Geographic Coordinate System           | GCS         | [Longitude, Latitude, Elevation] on 3D spheriod 
| Projected Coordinate System            | PCS         | [X-axis, Y-axis, Elevation] on 2D plane 
| Georeferenced Tagged Image File Format | GeoTIFF     | DEM image/data format (.tif) 
| World Geodetic System 1984             | WGS-84      | GCS, approximating the spheriod of earth 
| Web Mercator or Pseudo Mercator        | -           | PCS of WGS-84 
| Ordnance Survey Great Britain 1936     | OSGB-36     | GCS, approximating the spheriod of Britain   
| British National Grid                  | BNG         | PCS of OSGB-36 
| European Petroleum Survey Group        | EPSG        | EPSG codes define different GCSs and PCSs 

### Functions:

1. **Transforming** DEM from current GCS (e.g., WGS-84) to another GCS (e.g., OSGB-36).

2. **Projecting** DEM from current GCS (e.g., WGS-84/OSGB-36) to the corresponding PCS (e.g., Web Mercator/BNG).

3. **Visualising** DEM in PCS as 2D image.

4. **Reading** elevation of specific location from DEM in GCS.

### Limitations:

1. Can not visualize 3D land surface.


## DEM Dataset - ASTER GDEM

The Advanced Spaceborne Thermal Emission and Reflection Radiometer (ASTER) Global Digital Elevation Model (GDEM), i.e., ASTER GDEM or ASTGDEM, is a product of the Ministry of Economy, Trade, and Industry (METI) in Japan and the National Aeronautic and Space Administration (NASA) in United States. The source data were collected by the **Advanced Spaceborne Thermal Emission and Reflection Radiometer** on the NASA spacecraft **Terra**. The ASTGDEM version 1 (ASTGDEMv1) dara were released on 2009 and the ASTGDEM version 2 (ASTGDEMv2) data were released on 2011. The ASTGDEMv2 data are used in this code (reasons are explained below).

### Data Characteristics

The ASTGDEMv2 is comrised of 22702 tiles covering land surfaces between **83°N** and **83°S**. Each tile is a **1°x1°** block of earch surface that contains at least 0.01% land area. Thus, tiles which contain only ocean area are missing. [*Remark: The advantage of using 1°x1° tiles is that its much more efficient for geographic data processing in a small region. For example, covering the main area of London requires only two tiles.*]

The ASTGDEMv2 is distributed in **GeoTIFF (.tif)** image/data format. The data are posted on a **1 arc-second (1"~30m at the equator)** grid. The size of each tile is 1°x1° or **3601"x3601"**. [*Remark: The four edges of each tile are overlapped with its four adjacent tiles. Users should remove overlapped elements and merge the related tiles when more than one tile is used.*]

The ASTGDEMv2 data are referenced in **WGS-84 GCS**. In this case, the [**column**, **row**] of image/data array of one tile represents the [**longitude**, **latitude**] of a specific location on the earth. [*Remark: The WGS-84 is used to approxiate the earth rather than a specific region. Thus, it might be not accurate in local regions. This is why we transform WGS-84 GCS to OSGB-36 GCS, which is more accurate for describing locations in Britain [Ref](https://communityhub.esriuk.com/geoxchange/2012/3/26/coordinate-systems-and-projections-for-beginners.html).*]

### Download

ASTGDEMv2 data can be downloaded from [EarthExplorer](https://earthexplorer.usgs.gov/) (recommanded) or from [NASA Earthdata Search](https://search.earthdata.nasa.gov/search?q=ASTGTM%20V002).

For EarthExplorer users, 




















