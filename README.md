# Rice Seedling Detection

This notebook detects rice seedlings from the input UAV images.
> For each input image, output: 
> 1. Four result images with the detected rice seedlings drawing on the image.
> 2. .csv files with the position of detected rice seedlings.

##### Example
`input image`

<img src="./demo_img/demo.png" width=300>

`output images`
<table style="text-align: center;" cellpadding="0" border='0'>
    <tr>
        <td> 
            <img src="./demo_img/Gray_blob.jpg"  alt="1" width = 300px>
            <p>Preprocess: grayscale</p>
        </td>
        <td> 
            <img src="./demo_img/CLAHE_blob.jpg"  alt="2" width = 300px>
            <p>Preprocess: CLAHE grayscale</p>
        </td>
    </tr>
    <tr>
        <td> 
            <img src="./demo_img/TGI_blob.jpg"  alt="3" width = 300px>
            <p>Preprocess: TGI</p>
        </td>
        <td> 
            <img src="./demo_img/VARI_blob.jpg"  alt="4" width = 300px>
            <p>Preprocess: VARI</p>
        </td>
    </tr>
</table>

`output csv files`

<img src="./demo_img/csv.png">



### Acknowledgement
    The images used in the research were provided by GEOSAT Aerospace & Technology Inc.

### Data Acquisition
**Camera**: `Sony a7`
The camera was mounted on an UAV to fly along the designated route. 

**Captured date**: `6th, April, 2017`

**Image resolution**: `6000*4000 pixels`

**GSD**: about `0.72 cm/pixel`

**Flight place**: **TYDARES**, Taoyuan District Agricultural Research and Extension Station (`24°57'07.6"N, 121°01'41.8"E`)

**Flight path**:

 <img src="./demo_img/path.png" width=300>

### Test Field
 <img src="./demo_img/field.png" width=400>

`./input/`

 <img src="./demo_img/input.png" width=w100>

## Rice Seedling Detection

**1. Paddy Field Extraction**
To extract paddy field, the superpixel image was generated by SLIC. Each superpixel was then labeled as paddy or NOT paddy, and the set of superpixels with paddy label were the extracted paddy field.
**2. Generating preprocessing images**
Preprocessing images: grayscale image, CLAHE grayscale image, TGI image, and VARI image.
**3. Blob detection**
Blob detection was applied on the extracted paddy field with different preprocessing images to test the performance on rice seedling detection.

**Flowchart of rice seedling detection:**

<img src="./demo_img/detection.jpg" width="300">

#### 1. Creating folders
![img](./demo_img/foldertree.png)

#### 2. Building the dataset for paddy field extraction
The dataset consisting of different pre-labeled images is used for paddy field extraction.

The labeled binary images in `./dataset/mask/` should be named as **`labelName`\_`imgName`.jpg**.
White pixels in a labeled image represent the labeled area.

`./dataset/mask/`

 <img src="./demo_img/dataset_mask.png" width=w100>

`./dataset/img/`

 <img src="./demo_img/dataset_img.png" width=w100>


#### 3. Import packages
    * numpy
    * matplotlib.pyplot
    * cv2
    * skimage
    * os
    * csv
    * time

### For each input image
#### Paddy Field Extraction
 <img src="./demo_img/paddy field.png" width=300>

#### Generating the preprocessing images

`The preprocessing images:`
<table style="text-align: center;">
    <tr>
        <td> 
            <img src="./demo_img/gray.png"  alt="1" width = 300px>
            <p>Grayscale image</p>
        </td>
        <td> 
            <img src="./demo_img/clahe.png"  alt="2" width = 300px>
            <p>CLAHE grayscale image</p>
        </td>
    </tr>
    <tr>
        <td> 
            <img src="./demo_img/tgi.png"  alt="3" width = 300px>
            <p>TGI image</p>
        </td>
        <td> 
            <img src="./demo_img/vari.png"  alt="4" width = 300px>
            <p>VARI image</p>
        </td>
    </tr>
</table>

#### Blob detection
 <img src="./demo_img/blob.png" width=100%>
