---
title: "Nvidia Drivers"
date: 2007-04-11
forum: General Help
---

### Post by leveliv on 2007-04-11
I followed the guide on Ubuntuguide.org for installing the Nvidia Drivers..
[http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Graphics_Driver_.28NVIDIA.29]("http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Graphics_Driver_.28NVIDIA.29")

It says to open my Xorg.conf and changed "nv" to "nvidia" then to restart so I did that. then I was told that my xorg.conf wasn't configured correctly. so now what do I do? (it brought me to blue screen that asks if you want to run to see the output...then you can either say OK or Cancel)

---

### Post by spankymasterc on 2007-04-11
sudo dpkg-reconfigure xserver-xorg

that will promt a window that will reconfigure your xorg......

follow all stepes and in the beggining instead of vesa scroll up and choose nvidia

---

### Post by leveliv on 2007-04-11
now after I reconfigure it...what does that do like...would that make me able so I can actually use the drivers?

---

### Post by spankymasterc on 2007-04-11
if u installed the drivers correctly it should use them automatically...... nothing for you to do ... after... cept install them then configure xorg...... cant think of anything after your done do this 

ctrl  + alt + backspace it will send u to log in screen 

that will basically restart xorg and then if u see splashscreen of nvidia mean you did it right 

::cheers:::

if you need anything else feel free to add me on messenger check profile for Screen name :D

---

### Post by leveliv on 2007-04-11
thank you, I will try that...yeah maybe I will have to give you a shout :D

---

### Post by spankymasterc on 2007-04-11
also if u cant even log in try to start in recovery mode then do the command

sudo dpkg-reconfigure xserver-xorg and configure it there might be useful then when its done type start x if it start then restart computer and try to start your ubuntu again 

:::cheers:::

---

### Post by leveliv on 2007-04-14
k I reconfigured and it still doesn't work :| still says that same thing.

---

### Post by Josey on 2007-04-14
I would try this

```
sudo apt-get remove nvidia-glx
```

then

```
sudo apt-get install nvidia-glx
```

I think that fixed it for me when I was in your shoes.

---

### Post by leveliv on 2007-04-14
nope im installing 6.10 or 7.04 in a bit so im not even going to worry about this anymore.

---

