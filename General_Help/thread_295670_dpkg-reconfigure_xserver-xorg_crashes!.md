---
title: "dpkg-reconfigure xserver-xorg crashes!?"
date: 2006-11-08
forum: General Help
---

### Post by roots on 2006-11-08
hi, i'm having quite a few probs getting an external tft display running with my laptop under ubuntu dapper drake at the proper resolution, see [http://ubuntuforums.org/showthread.php?t=295663](http://ubuntuforums.org/showthread.php?t=295663) for this issue.

however, i tried to reconfigure the x server using 
```

dpkg-reconfigure xserver-xorg

```
but when i chose automatic display detection X crashes and (in the best case)  i'm put back to the gdm login prompt.

anyone knows how to solve this?


cheers,
roots

---

### Post by an.echte.trilingue on 2006-11-08
press ctrl+alt+F1, log in and run the command from a "real" virtual terminal, then go back to your GUI on ctrl+alt+F7

---

### Post by roots on 2006-11-08
thanks! ok i did and i could choose 1280x1024. however, after an Xserver restart i got back to 1024x768. i was able to switch to 1280x1024 via system-preferences-screenres. but the the visible screen area got resized to two thirds of the screen width and was totally blurred.

funny thin is, i could just get gnoppix (x version 6.8.2 as opposed to 7.0.0 i am running) working like a charm with 1280x1024!

any suggestions?

---

### Post by an.echte.trilingue on 2006-11-08
```
sudo gedit /etc/X11/xorg.conf
```

find the section:

```
Section "Screen"
        Identifier      "Default Screen"
        Device          "S3 Inc. VT8375 [ProSavage8 KM266/KL266]"
        Monitor         "Generic Monitor"
        DefaultDepth    16
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection
```

In those rows of screen resolutions, the first one is the default.  You can simply remove the resolutions you don't want or you can put the resolution you want first, as in mine, save and exit and then restart your Xserver with CTRL+ALT+BACKSPACE (this will kill your login so save everything first!)(all the rows have to be the same!)

Good Luck!

-mat

---

### Post by roots on 2006-11-08
hi, 
well, picking the resolution is not the problem anymore, but the way the display content is messed up: it shifted to the right and blurred.
it cant be moved to the proper position using the monitors adjustment button!

---

### Post by an.echte.trilingue on 2006-11-08
That is strange.  Are you sure that you are using the right driver for your card?  Are you sure you have the proper resolution for your screen?

I can help you with these if you need...

---

