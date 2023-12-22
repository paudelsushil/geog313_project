### Packages that are used in this workflow

```         
    1.  planetary_computer v0.5.1
    2.  datetime  
    3.  stackstac v0.4.3 
    4.  odc v0.3.6
    5.  pystac v1.7.3
    6.  pystac_client v0.7.1
    7.  shapely v2.0.1
    8.  json v2.0.9
    9.  cartopy v0.21.1
    10. pyproj v3.6.0
    11. rasterio v1.3.7
    12. rioxarray v0.14.1
    13. xrspatial v0.3.5
    14. matplotlib v3.7.1
    15. boto3 v1.26.76
    16. geopandas v0.13.2
    17. dask_geopandas v0.3.1
    18. pandas 2.0.2
    19. numpy 1.24.3
    20. xarray 2023.5.0
```

### Analyses undertaken

User should use following functions and methods to perform the analyses.

1.  **Functions under Images class:-**

    -   prefire_items()\
        returns list of items for prefire images

    -   postfire_items()\
        returs list of items for postfire images

    -   prefire_asset_urls()\
        returns list of urls of selected asset for prefire images

    -   postfire_asset_urls()\
        returns list of urls for selected asset for postfire images

    -   prefire_asset_url_to_dataset()\
        returns dataset for prefire images

    -   postfire_asset_url_to_dataset()\
        returns dataset for postfire images

2.  **Functions under Index class:-**

    -   prefire_items()\
        returns list of items for prefire images

    -   postfire_items()\
        returs list of items for postfire images

    -   prefire_asset_urls()\
        returns list of urls of selected asset for prefire images

    -   postfire_asset_urls()\
        returns list of urls for selected asset for postfire images

    -   prefire_asset_url_to_dataset()\
        returns dataset for prefire images

    -   postfire_asset_url_to_dataset()\
        returns dataset for postfire images

3.  **Functions for analysing building footprints datasets:-**

    -   get_keys()\
        returns all the S3 keys associated with a country_code from the Google and Microsoft Open Building Dataset on Source Cooperative

    -   read_geoparquet()\
        receives the path to a geoparquet file from the Google-Microsoft Building Footprints dataset and returns a dask_geopandas DataFrame of the data

    -   create_presigned_url()\
        Generate a presigned URL to share an S3 object

4.  **Functions for analysing climate datasets:-**

    -   climate_items()\
        returns list of items

    -   read_geoparquet()\
        receives the path to a geoparquet file from the Google-Microsoft Building Footprints dataset and returns a dask_geopandas DataFrame of the data

## User input variables

In this section, user needs to insert the required variables as stated below.

1.  **API_url** We do have two major API as a image sources i.e. Microsoft planetary computer and [aws API](https://earth-search.aws.element84.com/v1). I found variations in the output from both the sources. That's the reason I used [Microsoft API](https://planetarycomputer.microsoft.com/api/stac/v1).

2.  **collections** This is the types of satellite platforms like sentinel, [Landsat Collection 2 Level-1 and 2](datasets/landsat-c2/landsat-c2-example.ipynb%5D) and [Sentinel-2 Level-2A](datasets/sentinel-2-l2a/sentinel-2-l2a-example.ipynb)

3.  **area_of_interest** User should enter the list of minimum and maximum coordinate as bounding box. I have used bounding box of Washington states as a case study. For other USA states [bounding box coordinate](https://observablehq.com/@rdmurphy/u-s-state-bounding-boxes)

4.  **prefire_start_datetime, prefire_end_datetime** User should enter the numeric year, month, day separated by comma as shown in code chunk for prefire image. You can entered same date for both start and end if you do not want the interval.

5.  **postfire_start_datetime, postfire_end_datetime** User should enter the numeric year, month, day separated by comma as shown in code chunk for postfire image. You can entered same date for both start and end if you do not want the interval.

6.  **Credential for Source cooperative** In order to use the google and microsoft building footprints users must have credentials, for this you can register as new users in [Source Coperative](https://beta.source.coop/auth/registration/). After registering as a users, login to the application then [Generate Credentials](https://beta.source.coop/repositories/vida/google-microsoft-open-buildings/download/) to get the information needed to access data.

7.  **country_code** This is the ISO three digits country code (A-3) which can be [find](https://en.wikipedia.org/wiki/List_of_ISO_3166_country_codes) on wikipedia.

8.  **climate_collection** The [ERA5 dataset](https://confluence.ecmwf.int/display/CKB/ERA5%3A+data+documentation) from the ECMWF, converted to Zarr by [PlanetOS](https://planetos.com/) data on weather.

9.  **climate_datetime** starting and ending datetime climate datasets.

## Future research

1\. We can scaleup the process to select the prefire and postfire image using machine learning techniques and live fire detection methodologies.

2\. We can scaleup the process to isolate forest land cover from landsat images to use as wildland area instead of using prepared landuse landcover map.

3\. There is possibility of doing further research to relate climate change with the occurrence of wildland fire more precisely using deep learnig techniques.

## Difficulties and Lesson Learnt

1\. I think I choose ambitious research questions and tried to do project on several vauge topics instead of focusing in precise research question.

2\. I felt, in most cases, relied on bogus website article to come up with the results. After learning alot to come up with the analysis, this project work really change my way of doing research especially in making the workflow.

3\. Unsolved research question will be my future research question which I will scale up and reproduced in deep learning course in Spring 2024.

4\. I was unable to create an outline of wildland cover map to use as AOI for clipping fire severity map which was crucial to calculate total burned area during user entered time interval.

5\. I was unable to create buffer of building footprints inorder to calculate proximity from fire severity map due to large file size (i.e. \>10.5GB). I tried by generating preassign url but it crashed my notebook every time.
