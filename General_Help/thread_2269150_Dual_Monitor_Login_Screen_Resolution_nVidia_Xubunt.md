---
title: "Dual Monitor Login Screen Resolution nVidia Xubuntu 14.04.2"
date: 2015-03-13
forum: General Help
---

### Post by manuleka on 2015-03-13
Platform:
 Screens:
 1.1920x1080
 2.1280x1024

 GPU: nVidia GTX 770 4GB DVI-I,DVI-D,HDMI,DP

 OS: Xubuntu 14.04.2

I'm wanting to set the resolutions correctly on the login screens, both connecting through DVI (I and D) At the moment both screens are on 1280x1024. 

thanks for any help

---

### Post by manuleka on 2015-03-29
I manage to solve this by installing nVidia Proprietary driver for Linux
```

sudo apt-get install nvidia-current

```

it loads up on boot with correct resolutions

---

