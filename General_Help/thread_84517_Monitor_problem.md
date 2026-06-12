---
title: "Monitor problem"
date: 2005-10-31
forum: General Help
---

### Post by PenguinZdravko on 2005-10-31
I have installed Windows and Ubuntu both. In Ubuntu and Windows my screen is on 1024x768 85Hz. But when I start Ubuntu the image is out of the screen (it's too on right). How can I fix this?

---

### Post by frodon on 2005-10-31
Look at the end of the [heimo's guide]("http://ubuntuforums.org/showthread.php?t=83973"), he explains how adjust the position of the screen.

---

### Post by PenguinZdravko on 2005-10-31
I'm adjusting the position with the OSD of my monitor. It's now OK, but it's annoying that every time when I start Ubuntu or Windows, I must adjust the position.

---

### Post by 357Magnum on 2005-10-31
I am very much a Linux noob myself so I don't know if this is the problem or not BUT....

My screen was the same way (too far to the right) right after I loaded up Ubuntu 5.10. But I hadn't yet installed my video driver.

I have an NVIDIA 6800 GT. I did apt-get to install the NVIDIA driver and after re-boot the screen was perfectly centered. Are you sure your driver is installed and all of that?

---

### Post by frodon on 2005-10-31
[QUOTE=PenguinZdravko]I'm adjusting the position with the OSD of my monitor. It's now OK, but it's annoying that every time when I start Ubuntu or Windows, I must adjust the position.[/QUOTE]That's what the heimo's guide should allow you, to automatically adjust your screen position, it may solve your issue for ubuntu.
I give you the link again, the part which will interest you is at the end of the guide : [http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

---

### Post by PenguinZdravko on 2005-11-01
I'm scarried about the message that popups on the start of the app... Can it really do permanent damage to my monitor and videocard?

---

### Post by frodon on 2005-11-01
Yes, but if you strictly follow the heimo's guide you won't have any problem. It's not such a big deal.
However if you want more details you could simply post in the heimo's guide, i'm sure he will answer ;)

---

### Post by PenguinZdravko on 2005-11-07
I have tried to install the nVidia drivers from Synaptic. I've downloaded the files, changed the xorg.conf driver to be nvidia, but when I restart I get the white screen with nVidia's logo. To here is OK, but I wait 5 minutes, nothing happens. Only this white screen. Nothing loads, and I reset the computer. Using the recovery mode I make the drivers to be nv. But I want to use nVidia's drivers! What should I do?

---

### Post by frodon on 2005-11-07
Have you followed these steps to install nvdia driver ?
[http://ubuntuguide.org/#installnvidiadriver](http://ubuntuguide.org/#installnvidiadriver)

---

### Post by PenguinZdravko on 2005-11-07
Yes, I have followed them.

---

### Post by frodon on 2005-11-07
First, open your xorg.conf file and comment these lines if you have them, it's in the module section : ```
Load "Dri"
Load "GLcore"
```and check that you have the line **Load "glx"**, if not add it.
Add this option in the Device section to disable the nvidia logo : ```
Option "NoLogo"
```

---

### Post by PenguinZdravko on 2005-11-07
Same again. :( :( :(

---

### Post by frodon on 2005-11-07
Ok, could you post or attach in the next post your xorg.conf and xorg.log files ? 
You might need to do it in recovery mode using command line.

---

