
---

### Notes on Installation (follow instruction of Repo)
- cd video-retalking
- conda create -n video_retalking python=3.8
- conda activate video_retalking
- conda install ffmpeg
- create ENV for the repo
- git clone https://github.com/vinthony/video-retalking.git

### TOP ISSUES ON INSTALLATION
- Please follow the instructions from https://pytorch.org/get-started/previous-versions/
- The biggest issues are : torch==1.9.0+cu111 torchvision==0.10.0+cu111
- set PYTHONPATH=%PYTHONPATH%;C:\\Users\\bryan\\videoretalkingENV\\lib\\site-packages
- downgrading to numpy==1.23.1

### This installation command only works on CUDA 11.1
- pip install torch==1.9.0+cu111 torchvision==0.10.0+cu111 -f https://download.pytorch.org/whl/torch_stable.html
- Successfully installed torch-1.9.0+cu111 torchvision-0.10.0+cu111
- pip show torch
- pip show torchvision
- pip show numpy
- pip install -r requirements.txt

### Paths Are Important (highly recommend ENVs)
- set PYTHONPATH=%PYTHONPATH%;C:\\Users\\bryan\\videoretalkingENV\\lib\\site-packages
- import sys
- print(sys.path)

### Launching After Installation
- cd C:\Users\bryan\video-retalking\ && C:\Users\bryan\videoretalkingENV\Scripts\activate.bat
- set PYTHONPATH=%PYTHONPATH%;C:\\Users\\bryan\\videoretalkingENV\\lib\\site-packages
- python webui.py

### Checking Python Versions & Launching WebUI
- python --version
- python3 --version
- python webui.py
- python3 webui.py

### Video Cleanup & wav to mp4
- ffmpeg -i input.mp3 output.wav
- ffmpeg -i input.mp3 -b:a 16k -ac 1 output.wav
- ffmpeg -i c:\users\bryan\desktop\PixelWorks.mp4 -vf "deblock,hqdn3d,minterpolate='fps=30'" c:\users\bryan\desktop\video_fixed.mp4
- ffmpeg -vcodec mpeg4 -b:v 7561k -qscale:v 2 -acodec aac -ac 2 -async 1 -strict experimental c:\users\bryan\desktop\video_fixed.mp4 -threads 0 -i c:\users\bryan\desktop\PixelWorks.mp4
- ffmpeg -i c:\users\bryan\desktop\PixelWorks.mp4 -af "pan=stereo|c0=c0|c1=c0" c:\users\bryan\desktop\video_stereo.mp4
- .wav and .mp4 >>> name the same.

### IF HAVING ISSUES CHECK OUT THIS ISSUE AND DOWNGRADE NUMPY (CRITICAL)
- https://github.com/OpenTalker/video-retalking/issues/35#issuecomment-1542944601
- downgrading to numpy==1.23.1 fixed it without having to replace any text as stated above

### Troubleshooting (Using CLI)
- python inference.py --face temp/video\1.mp4 --audio temp/audio\1-0-100.wav --outfile results/64993_0.mp4
- (videoretalkingENV) C:\Users\bryan\video-retalking>python inference.py --face temp/video\3.mp4 --audio temp/audio\1-0-100.wav --outfile results/pixel_0.mp4

### Batch File for Your Desktop
- @echo off
- echo https://github.com/OpenTalker/video-retalking
- echo Python311
- echo Python311-32
- echo Python38
- echo Python39-32

- echo Opening Explorer...
- start sndvol
- start explorer "C:\Users\bryan\video-retalking"
- timeout 5

- echo Opening Task Manager / Resource Monitor...
- start taskmgr
- start resmon
- timeout 5

- echo Activating Virtual Environment...
- call "C:\Users\bryan\videoretalkingENV\Scripts\activate.bat"

- echo Starting Video-Retalking Application...
- cd "C:\Users\bryan\video-retalking\"
- "C:\Users\bryan\videoretalkingENV\Scripts\python.exe" "C:\Users\bryan\video-retalking\webui.py"

- exit

---
