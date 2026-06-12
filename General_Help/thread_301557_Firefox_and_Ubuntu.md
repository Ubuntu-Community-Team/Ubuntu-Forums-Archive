---
title: "Firefox and Ubuntu"
date: 2006-11-17
forum: General Help
---

### Post by helliewm on 2006-11-17
ust changed distro from SUSE SLED to Ubuntu 6.10 yesterday however I have slight issue with Firefox when I scroll down the page it scrolls down in wavy lines. I tried reinstalling Ubuntu and have look at the mouse setting and firefox preferences but can't seem to get it to scroll without lots of wavy lines in the web page . Its really annoying.

Anyone any ideas?

Helen

---

### Post by strabes on 2006-11-17
Install your video card drivers. If you have ati try [this](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide).

if you have nvidia you would want the [beta drivers](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/nVIDIA).

let me know how it works.

---

### Post by helliewm on 2006-11-17
I do have nvidia graphics card.

I am stuck here:

Configure X.Org to use the new nVidia driver

Note: this step is only required if you did not have the proprietary nVidia drivers installed previously.

    * Edit /etc/X11/xorg.conf and change the driver to nvidia: 

Section "Device"
       Identifier      ...
       Driver          "nvidia"
       BusID           ...
EndSection


I have been into the File Browser to try and edit it and it will not save the it, its saying I do have the relevant permissions.

I have been into the Root Terminal but cant see how to change it Root at the command line.

How can I edit the driver as per the instructions and save it. It says I currently have a generic video card in etc/x11/xorg.conf  

Helen

---

### Post by taurus on 2006-11-17
Open a terminal, Applications -> Accessories -> Terminal, and type

```
gksudo gedit /etc/X11/xorg.conf
(That would be capital X and number eleven, X11...)
```

---

### Post by helliewm on 2006-11-18
Thanks ever so much everyone for your help. It is fine now my nvidia card is installed successful and I am loving Ubuntu.

Having also searched the forums this seems to a common problem with the nvidia graphics/video cards does this need to be a sticky?

Whilst I am new to Linux I am very IT literate ( but self taught!) and I just feel its these little annoying issues that put people off Linux may be simple stickies for these sorts of issues would help? 

Helen

---

