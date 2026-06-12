---
title: "GeForce 7600 GS problem"
date: 2007-08-03
forum: General Help
---

### Post by CroEragon on 2007-08-03
I discovered Ubuntu around a month before release of edgy, and i love it.

However, i had some heavy problems with my integrated graphic card and its drivers, and i decided to return to Windows till some better time. I checked out fiesty when it was relesed, problem presisted, so i returned to windows. Now i got new Graphic card (nVidia GeForce 7600 GS) and im willing to give Ubuntu another go.

However, i encountered problems and need help. When i after many month choose Ubuntu 6.10 in GRUB menu i threw me into shell. I know few basic commands and thats it. I typed "startx" and it returned error 104 no screen detected, probably connected to fact that there is no mention of nVidia card in my x.org. So i typed "sudo dpkg-reconfigure xserver-xorg" choose "nv" drivers, and all other options best i could guess, and still nothing. startx still returns same error. I suspect that its now name of bus i left on default in reconfiguration, but im not sure. I have no idea what to do next. Please, help me!

Note:
Reinstall of either Ubuntu or Windows is not an option. I must keep same installations.

---

### Post by Steve1961 on 2007-08-03
Just an idea.  Why not boot with an Ubuntu live CD and copy the CDs xorg.conf file tto the installed system's /etc/X11/xorg.conf.

---

### Post by Computer-Slave on 2007-08-03
U can visit [http://users3.nofeehost.com/computerzone/login/memetest.asp](http://users3.nofeehost.com/computerzone/login/memetest.asp) goto linux downloads and download Easyubuntu it'll do ur nVidia drivers automatically.

---

### Post by 1337noob on 2007-08-05
i'm haveing the same problem as the guy who started this thread. I am also using fiesty fawn and it worked fine until i rebooted after installing my graphics drivers. it would boot up then kick me to a shell

---

### Post by h3hound on 2007-10-10
I ran into that issue with the new 7600 GS pci exp.

Here is what I did to install the card in feisty:

1 - disable Beryl
2 - install envy
3 - shutdown
4 - install video card but didnt connect to monitor
5 - restart and enter bios and set to PCI
6 - shutdown and connect monitor to card
7 - boot into ubuntu and I got kicked out to the terminal session
8 - ran the X reconfigure thing and let it auto detect the video card ("nv")
9 - restarted and I was able to log in and update the drivers with envy
10 - enable Beryl


Now all I need are tips on settings for this card.  I hear GLXGEARS is not a benchmark but i thought i could get better the 75 fps!


-b

---

### Post by xOriginalNinjax on 2007-10-10
My 6200LE was giving me fits, I just got it all working last night and did a write up of how I got mine going.  Yours may not be EXACTLY the same issue, so you may have to change/edit some steps, but this should more than likely get you close to running properly...[nVidia driver installation]("http://ubuntuforums.org/showpost.php?p=3506744&postcount=35").  I almost gave up on it too, but every time I ran a new step (if you read the whole thread, it took me three days to get it all done) it got closer, and I knew it would work in the end, so I stayed with it and am LOVING it.  I'm soooo much happier with Ubuntu with Wine than I was with Windows.  period.

---

### Post by Arizon_Dread on 2007-10-25
I also have a problem with my new graphics card.
it's a GeForce 7600 GS AGP card. I have gutsy installed. 

I've tried with the driver from NVIDIA's page, and I've tried with selecting the one specified in the Restricted Drivers Manager. I get the low-graphic-warning dialogue after the X-server fails to start on bootup. I am able to set my monitor model from the "Screens and Graphics"-menu and by that I can run ubuntu in 1280x1024 but it's really slow and the cube doesn't work. 

I used to have a GeForce FX 5200 before this card, which worked well with the cube and everything, but it SUCKS to play CSS with that card...

:confused:

I don't know what to do really, I've tried with reinstalling xorg and stuff but it won't work..

suggestions will be greatly appreciated.

---

### Post by Arizon_Dread on 2007-10-26
It's leaning towards reinstalling Gutsy next week if I can't get it working..

Will I get the restricted drivers working if I reinstall?

---

