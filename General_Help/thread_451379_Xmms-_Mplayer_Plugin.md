---
title: "Xmms- Mplayer Plugin"
date: 2007-05-22
forum: General Help
---

### Post by CheeseQueen452 on 2007-05-22
I installed the mplayer plugin for Xmms, but videos won't play. The plugin is enabled, but nothing happens when I try to play a video. What do I do?

---

### Post by JSThePatriot on 2007-05-22
It sounds like you dont actually have mplayer. Open your Synaptics Package Manager, and search for mplayer. Install it. You can also install the Mozilla plugin, and I find it quite useful.

I hope this is helpful,
JS

---

### Post by bung33 on 2007-05-22
MPlayer also has a UI of it's own. Take a look at [www.mplayerhq.hu](www.mplayerhq.hu) for more information. I have found in the past, that although I use XMMS a lot for audio, I will typically use MPlayer's UI for playing videos. However, MPlayer can handle just about any audio file you throw at it too, providing you have the right plugins installed. All of the information you need can be found on the home page above...

---

### Post by CheeseQueen452 on 2007-05-22
I have mplayer installed, but I get an error that says "Error opening/initializing the selected video_out (-vo) device". It happens with every video I try to play. Maybe this is why the xmms plugin doesn't work?

> **bung33 said:**
> MPlayer also has a UI of it's own. Take a look at [www.mplayerhq.hu](www.mplayerhq.hu) for more information. I have found in the past, that although I use XMMS a lot for audio, I will typically use MPlayer's UI for playing videos. However, MPlayer can handle just about any audio file you throw at it too, providing you have the right plugins installed. All of the information you need can be found on the home page above...

---

### Post by bung33 on 2007-05-28
OK... Let's see if we can't get this working. What kind of video card do you have? Are OEM or generic drivers installed? What kind of video file are you trying to play? Do you have the proper codecs installed? Give me some more detailed information and I think I'll be able to help you...

---

### Post by CheeseQueen452 on 2007-05-28
I have an Nvidia video card. I didn't install any drivers, so I assume it's using the generic ones that came with the OS. Any video I try to play won't work. I believe I have the right codecs installed, but I'll take a look & see if there's something else I may need.

> **bung33 said:**
> OK... Let's see if we can't get this working. What kind of video card do you have? Are OEM or generic drivers installed? What kind of video file are you trying to play? Do you have the proper codecs installed? Give me some more detailed information and I think I'll be able to help you...

---

### Post by bung33 on 2007-05-29
To get the drivers for your Nvidia card, type the following command in the terminal...

```
sudo apt-get install nvidia-glx
```

After that, you will need to install the gstreamer plugins to play file types like MP3, AVI, MPEG, etc...

---

### Post by CheeseQueen452 on 2007-05-29
Well, since I can play videos in KMplayer(not Mplayer), I think I'll leave it as is. Thanx, anyway.

> **bung33 said:**
> To get the drivers for your Nvidia card, type the following command in the terminal...

```
sudo apt-get install nvidia-glx
```

After that, you will need to install the gstreamer plugins to play file types like MP3, AVI, MPEG, etc...

---

### Post by rsg17187 on 2007-12-22
trying 
mplayer -vo $VO $filename

might help

$VO being one of
x11,
fbdev
fbdev2
xmga
xv

Mplayer is capable of using the X drivers, direct renedering as in fbdev and so on.

---

