---
title: "Missing screen resolutions"
date: 2006-07-24
forum: General Help
---

### Post by Ketrel on 2006-07-24
I installed Ubuntu on my laptop and after finially getting ATI drivers to work, I noticed that it doesn't go higher than 1024x768.

I do however know that I am capable of doing so, how can I make these available?

---

### Post by ahaslam on 2006-07-24
Now that you've installed the correct drivers, just add the desired resolutions to your xorg.conf file. Upon booting your system should then select the highest compatible resolution from the list. While in xorg.conf make sure that the correct driver is in use, the vesa driver limits to 1024x768.

Tony.

---

### Post by TripleE on 2006-07-24
> **Ketrel said:**
> I installed Ubuntu on my laptop and after finially getting ATI drivers to work, I noticed that it doesn't go higher than 1024x768.

I do however know that I am capable of doing so, how can I make these available?


Try this from the command line:
```
sudo dpkg-reconfigure xserver-xorg
```
Just select the defaults until you get to the resolutions.  Then select the ones you want.

---

### Post by Ketrel on 2006-07-24
After doing that

```

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. Radeon R250 Lf [Radeon Mobility 9000 M9]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection

```


My options are still
640x480
800x600
1024x768

I restarted the x server with ctrl+alt+backspace.

---

### Post by Ketrel on 2006-07-24
I also just rebooted.  It also did not help.

---

### Post by ahaslam on 2006-07-24
Check that you've got hardware accel (type **glxinfo** in terminal) you're looking for "*direct rendering: Yes*" near the top. 

Tony.

---

### Post by Ketrel on 2006-07-24
I have to have that cuz tuxracer is running at around 60fps here.  It does say Direct Rendering: yes anyhow.

---

### Post by ahaslam on 2006-07-24
Try changing your default colour depth to 16 (in xorg.conf). Some monitors can only use high resolutions in lower colour depths.

Tony.

PS. A reboot will also be required.

---

### Post by Ketrel on 2006-07-24
That's no good.  I need 32bit for some of the graphics work I do.
I have a dell inspiron laptop, maybe you know offhand if this is the case?

---

### Post by Ketrel on 2006-07-25
I set my xorg.conf to use 16
Upon rebooting, X failed to start saying that fglrx does not support 16.

In addition, I was unable to get my xorg.conf back because it wouldn't let me rename my back to xorg.conf due to some strict subs setting.

I have no idea how to get around that other than booting into recovery mode which I did and was able to restore my backup.

---

