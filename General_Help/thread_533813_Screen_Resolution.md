---
title: "Screen Resolution"
date: 2007-08-24
forum: General Help
---

### Post by gmlinux on 2007-08-24
Only have a few months of Linux behind me, so please consider that in replies.
I just installed Ubuntu 7.04 I believe it is, and my screen resolution is 1024x768
I would like something higher, but there are none higher available.
Like 1280x1024 etc.
How can I change it or get more selections.
Thanks

---

### Post by PurposeOfReason on 2007-08-24
You can edit your xorg.conf file to include the resolutions you want. Open a terminal and

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak #backups are nice
sudo gedit /etc/X11/xorg.conf
Find the resolutions part under display
Look at how it's all formated.
Add the resolution you want to each depth while keeping the same format/spacing.

Then restart X (ctrl+Alt+Backspace) and see if the resolution is there.

---

### Post by Steve1961 on 2007-08-24
> **gmlinux said:**
> Only have a few months of Linux behind me, so please consider that in replies.
I just installed Ubuntu 7.04 I believe it is, and my screen resolution is 1024x768
I would like something higher, but there are none higher available.
Like 1280x1024 etc.
How can I change it or get more selections.
Thanks

Firstly, what type of video card do you have.  It may be necessary to install a driver to get the full resolution.  Just open a terminal and type:

lspci -v

to find out the make and model of the video card.  You can also try this:

sudo gedit /etc/X11/xorg.conf

Make sure that 1280x1024 is the first entry in the section that looks something like this:

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV43 [GeForce 6600 GT]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Save and close, and then restart x, or just reboot

---

### Post by gmlinux on 2007-08-24
OK  working good now.
Thank you.
I will probably be back for something else.

---

