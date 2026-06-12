---
title: "wintv-hvr -5525 analogue input capture device"
date: 2017-10-03
forum: General Help
---

### Post by liewjls on 2017-10-03
Hi,

I'm using Wintv-hvr-5525 HD TV card on my PC. I'm would like to video stream from analogue input from a camera. Would anyone able to point me to the right direction how to configure this capture card? I have go through the link [https://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-5525](https://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-5525), installing the driver. But I have nothing on /dev/video<x>/ but i have something on /dev/dvb/adapter0 and /dev/dvb/adapter1. 

[HTML] 
sudo lsmodModule                  Size  Used bysi2157                 16384  1
si2168                 20480  1 
m88rs6000t             20480  1 
a8293                  16384  1 cx23885               180224  0 
altera_ci              20480  1 cx23885 
tda18271               49152  1 cx23885
altera_stapl           32768  1 cx23885 
m88ds3103              32768  2 cx23885 
tveeprom               24576  1 cx23885
cx2341x                24576  1 cx23885 
videobuf2_dvb          16384  1 cx23885 
dvb_core              126976  4 m88ds3103,altera_ci,videobuf2_dvb,cx23885 
rc_core                28672  1 cx23885 
v4l2_common            16384  2 cx2341x,cx23885 
i2c_mux                16384  2 m88ds3103,si2168 
videobuf2_dma_sg       16384  1 cx23885 
videobuf2_memops       16384  1 videobuf2_dma_sg 
snd_hda_codec_hdmi     49152  1 
videobuf2_v4l2         24576  1 cx23885 
snd_hda_intel          36864  1 
snd_hda_codec         126976  2 snd_hda_intel,snd_hda_codec_hdmi 
snd_hda_core           81920  3 snd_hda_intel,snd_hda_codec,snd_hda_codec_hdmi 
videobuf2_core         40960  3 videobuf2_dvb,cx23885,videobuf2_v4l2 
snd_hwdep              16384  1 snd_hda_codec 
videodev              172032  5 cx2341x,v4l2_common,videobuf2_core,cx23885,videobuf2_v4l2 
media                  40960  2 videodev,si2157 
snd_pcm               102400  5 snd_hda_intel,snd_hda_codec,snd_hda_core,snd_hda_codec_hdmi,cx23885 

[/HTML]

What i have missing?


thanks.

---

