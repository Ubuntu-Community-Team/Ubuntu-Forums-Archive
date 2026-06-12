---
title: "Why does my Raspberry Pi 4 camera stop after 'starting camera' and not show an image?"
date: 2023-05-28
forum: General Help
---

### Post by memogor on 2023-05-28
hello guys i have a 2 big problem with camera screening from my raspberry pi 4(Ubuntu MATE 22.04 OS)!

1 : i installed libcamera successfully and its showing in my folder and ls but i cant run it everytime i want to run it shows me the error "command not found". i tried to reinstall it like 5 times!!

2 : when i run my command to launch on my roboter the camera launch its shows me until starting camera but it sends me no image on my dev machine!!

[INFO] [1685308312.016667854] [v4l2_camera]: Driver: bm2835 mmal
[INFO] [1685308312.017127366] [v4l2_camera]: Version: 331618
[INFO] [1685308312.017204633] [v4l2_camera]: Device: mmal service 16.1
[INFO] [1685308312.017255898] [v4l2_camera]: Location: platform:bcm2835-v4l2-0
[INFO] [1685308312.017306847] [v4l2_camera]: Capabilities:
[INFO] [1685308312.017353852] [v4l2_camera]:   Read/write: YES
[INFO] [1685308312.017401506] [v4l2_camera]:   Streaming: YES
[INFO] [1685308312.017468031] [v4l2_camera]: Current pixel format: YUYV @ 640x480
[INFO] [1685308312.018461025] [v4l2_camera]: Available pixel formats: 
[INFO] [1685308312.018520142] [v4l2_camera]:   YU12 - Planar YUV 4:2:0
[INFO] [1685308312.018569925] [v4l2_camera]:   YUYV - YUYV 4:2:2
[INFO] [1685308312.018618208] [v4l2_camera]:   RGB3 - 24-bit RGB 8-8-8
[INFO] [1685308312.018663639] [v4l2_camera]:   JPEG - JFIF JPEG
[INFO] [1685308312.018708496] [v4l2_camera]:   H264 - H.264
[INFO] [1685308312.018755223] [v4l2_camera]:   MJPG - Motion-JPEG
[INFO] [1685308312.018801876] [v4l2_camera]:   YVYU - YVYU 4:2:2
[INFO] [1685308312.018845992] [v4l2_camera]:   VYUY - VYUY 4:2:2
[INFO] [1685308312.018890052] [v4l2_camera]:   UYVY - UYVY 4:2:2
[INFO] [1685308312.018934075] [v4l2_camera]:   NV12 - Y/CbCr 4:2:0
[INFO] [1685308312.018978006] [v4l2_camera]:   BGR3 - 24-bit BGR 8-8-8
[INFO] [1685308312.019021955] [v4l2_camera]:   YV12 - Planar YVU 4:2:0
[INFO] [1685308312.019065774] [v4l2_camera]:   NV21 - Y/CrCb 4:2:0
[INFO] [1685308312.019109834] [v4l2_camera]:   RX24 - 32-bit XBGR 8-8-8-8
[INFO] [1685308312.019156487] [v4l2_camera]: Available controls: 
[INFO] [1685308312.019217068] [v4l2_camera]:   Brightness (1) = 50
[INFO] [1685308312.019276222] [v4l2_camera]:   Contrast (1) = 0
[INFO] [1685308312.019333599] [v4l2_camera]:   Saturation (1) = 0
[INFO] [1685308312.019394827] [v4l2_camera]:   Red Balance (1) = 1000
[INFO] [1685308312.019452259] [v4l2_camera]:   Blue Balance (1) = 1000
[INFO] [1685308312.019506635] [v4l2_camera]:   Horizontal Flip (2) = 0
[INFO] [1685308312.019562993] [v4l2_camera]:   Vertical Flip (2) = 0
[INFO] [1685308312.019616980] [v4l2_camera]:   Power Line Frequency (3) = 1
[INFO] [1685308312.019670912] [v4l2_camera]:   Sharpness (1) = 0
[INFO] [1685308312.019726177] [v4l2_camera]:   Color Effects (3) = 0
[INFO] [1685308312.019780683] [v4l2_camera]:   Rotate (1) = 0
[INFO] [1685308312.019840671] [v4l2_camera]:   Color Effects, CbCr (1) = 32896
[ERROR] [1685308312.019909919] [v4l2_camera]: Failed getting value for control 10027009: Permission denied (13); returning 0!
[INFO] [1685308312.019962776] [v4l2_camera]:   Codec Controls (6) = 0
[INFO] [1685308312.020020708] [v4l2_camera]:   Video Bitrate Mode (3) = 0
[INFO] [1685308312.020078529] [v4l2_camera]:   Video Bitrate (1) = 10000000
[INFO] [1685308312.020134368] [v4l2_camera]:   Repeat Sequence Header (2) = 0
[ERROR] [1685308312.020191430] [v4l2_camera]: Failed getting value for control 10029541: Permission denied (13); returning 0!
[INFO] [1685308312.020240843] [v4l2_camera]:   Force Key Frame (4) = 0
[INFO] [1685308312.020331982] [v4l2_camera]:   H264 Minimum QP Value (1) = 0
[INFO] [1685308312.020415213] [v4l2_camera]:   H264 Maximum QP Value (1) = 0
[INFO] [1685308312.020476219] [v4l2_camera]:   H264 I-Frame Period (1) = 60
[INFO] [1685308312.020535466] [v4l2_camera]:   H264 Level (3) = 11
[INFO] [1685308312.020591676] [v4l2_camera]:   H264 Profile (3) = 4
[ERROR] [1685308312.020647052] [v4l2_camera]: Failed getting value for control 10092545: Permission denied (13); returning 0!
[INFO] [1685308312.020695743] [v4l2_camera]:   Camera Controls (6) = 0
[INFO] [1685308312.020751711] [v4l2_camera]:   Auto Exposure (3) = 0
[INFO] [1685308312.020808217] [v4l2_camera]:   Exposure Time, Absolute (1) = 1000
[INFO] [1685308312.020864186] [v4l2_camera]:   Exposure, Dynamic Framerate (2) = 0
[INFO] [1685308312.020918933] [v4l2_camera]:   Auto Exposure, Bias (9) = 12
[INFO] [1685308312.020974124] [v4l2_camera]:   White Balance, Auto & Preset (3) = 1
[INFO] [1685308312.021028667] [v4l2_camera]:   Image Stabilization (2) = 0
[INFO] [1685308312.021195962] [v4l2_camera]:   ISO Sensitivity (9) = 0
[INFO] [1685308312.021268822] [v4l2_camera]:   ISO Sensitivity, Auto (3) = 1
[INFO] [1685308312.021333199] [v4l2_camera]:   Exposure, Metering Mode (3) = 0
[INFO] [1685308312.021393742] [v4l2_camera]:   Scene Mode (3) = 0
[ERROR] [1685308312.021457842] [v4l2_camera]: Failed getting value for control 10289153: Permission denied (13); returning 0!
[INFO] [1685308312.021509088] [v4l2_camera]:   JPEG Compression Controls (6) = 0
[INFO] [1685308312.021569094] [v4l2_camera]:   Compression Quality (1) = 30
[WARN] [1685308312.024481365] [v4l2_camera]: Control type not currently supported: 6, for control: Codec Controls
[WARN] [1685308312.024844385] [v4l2_camera]: Control type not currently supported: 4, for control: Force Key Frame
[WARN] [1685308312.025328714] [v4l2_camera]: Control type not currently supported: 6, for control: Camera Controls
[WARN] [1685308312.025656767] [v4l2_camera]: Control type not currently supported: 9, for control: Auto Exposure, Bias
[WARN] [1685308312.025929314] [v4l2_camera]: Control type not currently supported: 9, for control: ISO Sensitivity
[WARN] [1685308312.026256978] [v4l2_camera]: Control type not currently supported: 6, for control: JPEG Compression Controls
[INFO] [1685308312.026435330] [v4l2_camera]: Starting camera


i changed the /boot/firmwware/config.txt file to camera_auto_detect=0 and added start_x=1 but still it detected that camera and everything but when i want to launch it it just goes until starting camera and stops and shows no image

pls if you have any ideas help me

i tried to reinstall libcamera like 5 times also the driver and everytime by the driver everything is working only the launch not

---

