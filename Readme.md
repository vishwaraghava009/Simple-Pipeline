# Audio Driven Talking Heads

This repository provides a simple pipeline for generating audio-driven talking heads using two models:

1. **AdaSR Talking Head**: For motion transfer or pose transfer, which includes transferring expressions, eye-blinks, and head movements.
2. **MuseTalk**: For lip synchronization.

## Steps to Run the Pipeline


### Instructions

1. **Login to the profile: `iby_vishwa`.**

2. **Open the directory `Documents/AdaSR` through VSCode.**

3. **Open a new terminal in VSCode.**

4. **Upload an image and an audio file (.wav) of your choice** into the `DEMO` subdirectory of the `AdaSR-TalkingHead` directory.

5. **Edit the `run_demo.sh` file:**
   - Open `run_demo.sh` in the `AdaSR-TalkingHead` directory.
   - Edit the image and audio file names according to your uploaded files.

6. **Run the following commands to perform motion transfer:**

    ```sh
    conda activate adasr_env
    cd AdaSR-TalkingHead
    conda activate mesh-video
    bash run_demo.sh
    ```

    - The motion transfer video will be saved in the same directory.

7. **Deactivate the conda environments:**

    ```sh
    conda deactivate
    conda deactivate  # Yes, deactivate twice
    cd ..
    ```

8. **Run the first inference of MuseTalk:**

    ```sh
    conda activate musetalk_env
    cd MuseTalk
    bash infer.sh
    ```

    - The results will be saved under the directory `Musetalk/results/avatars/avator_1/vid_output`.

### Note

- The first inference might take some extra time to create avatars (facial volumetric features). These can be saved beforehand to reduce inference time for subsequent runs.

## Directory Structure

.                                                                                                                                              
├── AdaSR-TalkingHead                                                                                                                          
│   ├── DEMO                                                                                                                                   
│   │   ├── <your_image>.jpeg                                                                                                                  
│   │   ├── <your_audio>.wav                                                                                                                   
│   ├── run_demo.sh                                                                                                                            
│   ├── ...                                                                                                                                    
│                                                                                                                                              
├── MuseTalk                                                                                                                                   
│   ├── configs                                                                                                                                
│   │   ├── inference                                                                                                                          
│   │   │   ├── realtime.yaml                                                                                                                  
│   ├── scripts                                                                                                                                
│   │   ├── realtime_inference.py                                                                                                              
│   ├── infer.sh                                                                                                                               
│   ├── ...                                                                                                                                    

Make sure to replace `<your_image>.jpeg` and `<your_audio>.wav` with your actual files in the `DEMO` directory and `run_demo.sh`.

## Troubleshooting

If you encounter any issues, please ensure that:
- The paths in your scripts are correctly set.
- The conda environments are correctly activated.
- The necessary dependencies are installed.
