---
title: "Nvidia Resolution issues"
date: 2008-05-02
forum: General Help
---

### Post by troubledMind on 2008-05-02
I've been messing on and off with linux for years now and I really want to make the big leap and use it as my primary OS.  I downloaded and installed 8.04 AMD64.  I wanted compiz-fusion effects running so I installed the nvidia driver.  For some reason I can't get anything to allow for a higher resolution than 640x480.  I've tried just about everything that I can think of.  I've enabled the restricted driver.  I've tried using envyng to install the drivers.  I've also tried installing the nvidia driver manually.  The furthest progress I have made was to get it to boot into a virtual desktop with a 1280x1024 resolution but the true resolution was still 640x480.  I'll list my hardware here to see if anyone can help me with this.  I have a 7900GTX and I am using two Rosewill R913J monitors.  These monitors have a  Hsynch 30-79Hz and a Vsynch of 56-75Hz.  I've tried everything with the xorg.conf and still can't get it to work correctly.  I would greatly appreciate any help that can be given.

---

### Post by troubledMind on 2008-05-03
Anyone, I still can't get it to work.

---

### Post by DMK62 on 2008-05-03
Have you tried installing nvidia-settings and configuring your settings with it ?

sudo apt-get install nvidia-settings

to start it from the terminal

sudo nvidia-settings

Dale

---

### Post by troubledMind on 2008-05-03
Yeah I've tried that,  I can get nvidia settings to come up.  The problem is it only has the resolutions of 640x480 and 320x240 or whatever the smaller one is.  I've then tried editing the xorg.conf to make it 1280X1024 and then it will just give me a blank screen.  Like the monitor is out of range.  I can log in and hear the ubuntu log on sound from my headphones.  I've looked up the horizontal and vertical synch settings and made sure I set them up right.  Also when using the vesa drivers I am able to have 1280x1024 resolution.  The nvidia driver just doesn't seem to like it.

---

### Post by DMK62 on 2008-05-03
From your post I would assume it was never an issue with versions before Hardy Heron ? 

There seems to be several issues with nvidia cards and the new bulletproof x in Hardy. It might be that it is falling back to failsafe mode because of one of these issues. I recommended nvidia-settings as it usually works great with dual monitor configurations. 

Have you tried running

displayconfig-gtk

from the terminal 

Dale

---

### Post by troubledMind on 2008-05-03
Right now I am actually just trying to get one of my monitors to 1280x1024 using the nvidia driver.  I tried what you said, and changed the primary monitor to a generic LCD 1280x1024 since rosewill wasn't in there.  Interesting results what it did was make the logon screen into 1280x1024 but I could only view 640x480 of it. Once I logged in it went back to straight up 640x480.  An interesting side note, I tried running nvidia-settings from the terminal (before I was doing it from the taskbar)  and it gives me a series of errors about attributes and one that says it cannot open display 'troubledmind-desktop:0.0'.  The settings program still runs but all these errors are displayed in the terminal.  Thank you very much for helping I really appreciate it.

---

### Post by thorner on 2008-05-03
I was having a similar issue when first upgraded to Hardy.
I used Alberto Milone's "[EnvyNG]("http://www.albertomilone.com/nvidia_scripts1.html")" script and it *mostly* fixed my problem. (just a minor annoyance that I'm trying to fix... [link]("http://ubuntuforums.org/showthread.php?p=4875049#post4875049"))

I get 1280x1024 now and full compiz-fusion effects.

Hope that can help you.

Cheers

---

### Post by DMK62 on 2008-05-03
The nvidia-settings errors could be due to previous command writing to xorg.conf. 

You have to run nvidia-settings under sudo or gksu ( terminal ) or the settings will only keep for that session. You have to use sudo for the settings to be saved as your account only has read permission on that file.

sudo nvidia-settings 

then hopefully you can find the correct settings and then Apply and Save and Yes to save the changes to your xorg.conf file.

You may want to try searching the nvidia forums  at 

[http://www.nvnews.net/vbulletin](http://www.nvnews.net/vbulletin)

There is also Ubuntu thread for nvidia cards. Check the last few pages for the most recent issues.

[http://ubuntuforums.org/showthread.php?t=221313](http://ubuntuforums.org/showthread.php?t=221313)

I haven't been able to find the post or link but I remember reading something that some 7xxx cards would not work properly with the latest nvidia driver and bulletproof x. There may be info on that at nvnews.net.

I'll see what else I can find over the next day or two. You may want to also post in the Multimedia and Video category.

Dale

---

### Post by troubledMind on 2008-05-04
Thanks everyone for the help.  I figured it out.  For some reason Xorg couldn't read the EDID information off my monitors through the DVI cables.  I switched to vga cables and it works fine now.  Full compiz at the correct resolution.  I don't know if it's a problem with the monitors or with Xorg itself.  Thanks again everyone

---

### Post by DMK62 on 2008-05-04
You're welcome. Great to hear that you were able to get it working. It would be a good post for the nvidia thread I mentioned in my previous post.

Dale

---

### Post by Zorael on 2008-05-04
The X version in Hardy does a whole lot more automatically than the Gutsy (and earlier) version(s) did, which wanted stuff like resolutions explicitly defined in its settings. (/etc/X11/xorg.conf)

If you're an upgrader and you're having trouble with resolutions suddenly not working, that xorg.conf likely containts old definitions which Hardy doesn't agree with, and stuff will hopefully start working if you reset that settings file to Hardy's defaults. Of course, you'll lose extra videocard tweaks, but by making a backup and then comparing the new file to the old you can restore those. Also, you'll need to reenable any restricted drivers if you use those, which can also be done manually when you're comparing the new file to the old.

Obviously, no need to do this if you already have it working.


To reset:
```
$ sudo mv /etc/X11/xorg.backup0805
$ sudo dpkg-reconfigure xserver-xorg
```

To get Nvidia cards set up again, do this.
```
$ sudo nvidia-xconfig -d 24 --allow-glx-with-composite --add-argb-glx-visuals --randr-rotation
```
I don't know of any ATI command equavlients.

---

### Post by alzie on 2008-05-04
Zorael's instructions are spot on for me, the only thing I'd add is to check to see if your monitor is correct. I was only getting 800x600 until I changed my monitor with nvidia-xconfig.  Now I'm at 1280x1024 where I should be :)

---

### Post by brokenLockpick on 2008-07-15
> **troubledMind said:**
> Thanks everyone for the help.  I figured it out.  For some reason Xorg couldn't read the EDID information off my monitors through the DVI cables.  I switched to vga cables and it works fine now.  Full compiz at the correct resolution.  I don't know if it's a problem with the monitors or with Xorg itself.  Thanks again everyone

I was banging my head off of my desk till I read this. I'm using a pair of R913J monitors with a 7800gt but using the vga rather than dvi cables did the trick. Weird.

---

