---
title: "Totem Help With MPG Files"
date: 2005-08-03
forum: General Help
---

### Post by Mith on 2005-08-03
I'm just running a standard .mpg file and for some reason Totem is saying I need to download a decoder. I am using an nVidia GeForce 4MX and did that sudo thing to use the driver. I also have an Envy24HT-S chipset sound card that is getting sound. I do not have Internet access at home so I can't really download things. I am a major newb so compiling from source... I don't know anything about that. Are there any steps I can take?

---

### Post by bored2k on 2005-08-03
[QUOTE=Mith]I'm just running a standard .mpg file and for some reason Totem is saying I need to download a decoder. I am using an nVidia GeForce 4MX and did that sudo thing to use the driver. I also have an Envy24HT-S chipset sound card that is getting sound. I do not have Internet access at home so I can't really download things. I am a major newb so compiling from source... I don't know anything about that. Are there any steps I can take?[/QUOTE]
 1. [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)
2. sudo apt-get update
3. sudo apt-get install totem-xine w32codecs gstreamer0.8-plugins --force-yes -y

You need internet for that. I guess you could download the packages and save them on a disc or something.

---

