---
title: "No Compiz Ati X1300 and Edgy"
date: 2006-10-29
forum: General Help
---

### Post by aldrlandon on 2006-10-29
Hi. I am new to linux, but I installed the ati fglrx drivers for my radeon x1300, via the ubuntu help guide, and followed this guide for installing compiz: ([http://ubuntuforums.org/newthread.php?do=newthread&f=131)](http://ubuntuforums.org/newthread.php?do=newthread&f=131)), and I can start beryl manager, but sometimes my computer wont even get to the login screen before it crashes or, when I login, beryl manager starts and I select Beryl for the window manager. The problem though, is that it sticks with metacity as the window manager after I have selected beryl. I have verified that the drivers are installed correctly because when I do fglrxinfo, it says my card is an ati X1300 and the drivers are the fglrx. Any help would be greatly appreciated. Right now, when I start my computer, it gets to the ubuntu splash screen, and then blue and green lines appear under the loading bar.

---

### Post by llamakc on 2006-10-29
Your link doesn't work for me.

If you're using fglrx you have to use Xgl, and not the built-in AIGLX, or use the 'radeon' driver w/AIGLX.

---

### Post by aldrlandon on 2006-10-29
I have also tried this guide: [http://forum.beryl-project.org/topic-4863-howto-xgl-and-beryl-how-for-gnome](http://forum.beryl-project.org/topic-4863-howto-xgl-and-beryl-how-for-gnome)

Which didn't work either and caused my screen to wig out before the login window appeared, as described in the last post. Any other ideas why it wouldn't even get to the login screen before crashing with the fglrx drivers? By the way, I'm using 8.28.8

---

### Post by llamakc on 2006-10-29
Nope: I'm glad you mentioned the problem though. I was just getting around to trying Xgl after I upgraded my fglrx driver. 

If you don't mind the 'radeon' driver, aiglx ran w/Beryl perfectly for me.

---

### Post by aldrlandon on 2006-10-29
how do you install the radeon driver?

---

### Post by llamakc on 2006-10-29
Just change the line with "fglrx" in /etc/X11/xorg.conf to "radeon" and restart the X server.

---

### Post by aldrlandon on 2006-10-29
so you install the fglrx driver, then change fglrx to radeon in the xorg.conf?? Sorry, I'm a newb at linux :)

---

### Post by llamakc on 2006-10-29
No, you don't need the fglrx driver at all if you want to use the "radeon" driver.

---

### Post by aldrlandon on 2006-10-29
So how do you exactly obtain the radeon driver. Is it included with Edgy Eft, or do I have to apt-get it? Sorry, I just don't know linux very well yet. Is there a guide anywhere? Thanks for all of your help so far!

---

### Post by llamakc on 2006-10-29
You do as I suggested and edit the file /etc/X11/xorg.conf

You already have the driver. It was probably what you were using before installing fglrx.

---

### Post by aldrlandon on 2006-10-29
Oh, OK. Thanks so much!

---

### Post by aldrlandon on 2006-10-29
Ok, so I changed it to radeon, but then it again, crashes before the logon screen (at the ubuntu flash screen, right before it switches to the login screen, blue and green lines appear under the loading bar), just like with the fglrx drivers.

---

### Post by llamakc on 2006-10-29
At this point you're going to want to post your /etc/X11/xorg.conf so people smarter than me can peek at it.

---

### Post by aldrlandon on 2006-10-29
My current problem is that I can't even get into ubuntu to look at/ change the xorg.conf. I can only get into the recovery console (basically a terminal), so what am I supposed to do from there?

---

### Post by llamakc on 2006-10-29
When you tried Beryl did you use Xgl?

---

### Post by aldrlandon on 2006-10-29
One time I used XGL, but after that didn't work and I found out that edgy came with aiglx, I just installed beryl and did the tweaks that the guide I referred to earlier said to do.

---

### Post by kickehy on 2006-10-31
Aldrlandon: don't think you're the only one having this problem....I get the EXACT same problems that you've mentioned above and have no idea how to fix it. Here's my xorg.conf as is (right after my fresh install):

Section "Device"
        Identifier      "ATI Technologies, Inc. ATI Default Card"
        Driver          "vesa"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Dell E193FP"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. ATI Default Card"
        Monitor         "Dell E193FP"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
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
EndSection

Section "DRI"
        Mode    0666
EndSection


I figured you didn't want all the tablet pc, keyboard, and mouse stuff so this is everything from "Device" down. Hope this helps you and me.

Oh and all you need to do is boot into recovery mode and revert back to your original xorg.conf that you had before you edited it for beryl.

---

### Post by agentstewie on 2006-11-16
hmm... i am having trouble with this exact issue.... i think the radeon driver doesnt work because the x1300 isnt supported by aiglx, but the older cards are. try updating to the new current ati driver.. 8.31.5

i am intrested to see if you can get an answer .. because i have an x1300 card... and i would perfer aiglx by far.

---

### Post by rwabel on 2007-02-11
indeed x1300 is not supported by the open source driver "radeon"

---

### Post by cabez0n on 2008-05-07
> **llamakc said:**
> Your link doesn't work for me.

If you're using fglrx you have to use Xgl, and not the built-in AIGLX, or use the 'radeon' driver w/AIGLX.

Actually latest ati proprietary driver provide built-in support so you don't need xgl. I use debian and there's no xgl for debian, so I was hoping this would finally let me run compiz.. but still couldn't get it working...

---

