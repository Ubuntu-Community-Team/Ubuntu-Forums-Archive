---
title: "VLC and DVDs"
date: 2007-01-22
forum: General Help
---

### Post by dnccnd on 2007-01-22
Hallo!

I have just bought a DVD player for my relatively old IBM laptop and I am experiencing some problems. I can play DVDs with Movie Player, but VLC doesn't work. When I select "Open Disc" from the "File" menu, VLC won't open the DVD, no matter whether I choose "DVD (menus)" or "DVD" in the "Disc Type" option. I can see that there is no name in the "Device name" option.

Any idea?

Thank you for your help!

---

### Post by FluffyElmo on 2007-01-22
You have to enter the device path, on my system I use /dev/hdc, depending on the number of drives in your system it may have a different path. From the top menu run *System->Administration->System Monitor* and you can see your mounted file systems on the *File Systems* tab. 

I'm attaching a screen grab of my VLC open disc dialog in case there are any other changes needed...Good Luck!

---

### Post by dnccnd on 2007-01-23
Thank you FluffyElmo!

It worked! Do you know how I can change the settings of VLC in order not to have to write the same name every time I want to open a DVD?

---

### Post by FluffyElmo on 2007-01-23
Glad it worked! I'm not sure how I did it, it may have happened automatically in my case. I think I know how you can fix it for you though. There is a hidden directory in my home directory ***.vlc*** containing a file ***vlcrc*** which seems to hold the default configuration. It's mostly commented out but near the end mine contains the following lines:

```
# DVD device (string)
dvd=/dev/hdc
# VCD device (string)
vcd=/dev/hdc
# Audio CD device (string)
cd-audio=/dev/hdc

```

If you add similar lines to yours it should work, they'll probably already be there but commented out. You can edit the file either by hitting ***Ctrl-H*** in a file browser window to show hidden files and navigating to it, or from a terminal window type:
```
gedit .vlc/vlcrc
```

Good Luck!

---

### Post by dnccnd on 2007-01-23
Thank you again!

This is what I have in the file you mentioned:

[INDENT]# DVD device (string)
#dvd=
# VCD device (string)
#vcd=/dev/cdrom
# Audio CD device (string)
#cd-audio=/dev/cdrom[/INDENT]

I have tried to add both '/dev/hdc' and '/dev/cdrom' after '#dvd=' but even if I save the file, every time I open VLC and every time I open the text file, my change disappears.

Can it be related to the fact that there is a '#' before 'dvd='? :confused:

---

### Post by FluffyElmo on 2007-01-23
Any line with a '#' in front of it is considered a comment. So just delete the # at the front  of those three lines and it should work...

---

### Post by dnccnd on 2007-01-27
Great! It worked!
Thank you again for your help.

---

### Post by Maestro23 on 2007-01-28
Glad I saw this thread as well.  Thanks guys.:D

---

