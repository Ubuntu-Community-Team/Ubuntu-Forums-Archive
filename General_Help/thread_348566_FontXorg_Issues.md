---
title: "Font/Xorg Issues"
date: 2007-01-28
forum: General Help
---

### Post by JoshHendo on 2007-01-28
Hello.

When I boot up my computer, it goes to GDM as it should most of the time (I am having trouble with broken partitions that break the boot process occasionally, but that is currently the least of my worries). When I attempt to login, it just refreshes to the GDM screen after going to a black screen.

When I go Ctrl - Alt - F1, I am able to get to a command line. When I run "startx" from there, after removing the lock file (/tmp/X0-lock or something similar), I get the following error message.

```
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
    It is a directory

Error opening /dev/wacom: No such file or directory
Could not init font path element /usr/share/fonts/X11/TFF/, removing from list
Could not init font path element /usr/share/fonts/X11/OTF, removing from list
Could not init font path element /usr/share/fonts/X11/CID/, removing from list

Waiting for X server to shut down FreeFontPath: FPE "/usr/share/fonts/X11/misc
refcount is 2, should be 1; fixing.
```

What could I do to fix this? Thanks!

---

### Post by JoshHendo on 2007-01-30
This is a very unique problem. It is unique as in a re-install of Ubuntu didn't fix it!

I thought the easiest way would be just to re-install Ubuntu, and so I did, and when it booted up again, the same thing happened.

I guess it has something to do with either my home parition (becuase it is on a seperate partition and it isn't formatted every install) or my hardware.

---

### Post by 0x29a on 2007-02-04
Hi!

The critical thing that I see in your error messages is regarding /usr/share/fonts/X11/misc

Edit this line to read
```

/usr/share/X11/fonts/misc

```

Here is my font section from my xorg.conf file as a reference:
```

Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
#        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

```

I commented out the cyrillic font path because it doesn't exist and was giving me the "could not init" error.

The rest of it is a pretty common issue, actually. Even with other distros. If you try to navigate either using Konqueror, Nautilus, or from the command line you'll find that the X11 directory does not exist. But you knew that I'm sure ;-)

The best way to stop getting the error is the comment out the corresponding lines in /etc/X11/xorg.conf. It won't hurt anything and these warnings are just that: warnings. There is, however, the font path /usr/share/X11/fonts, but you'll notice that the directories TTF, OTF, and CID od not exist either. That's why I'd suggest just commenting out those paths.

You've also noticed the errors for a non-existent Wacom tablet, also. Again, it is safe to comment out the corresponding lines of xorg.conf.

All of these lines are just Ununtu's way of anticipating user needs. I actually have a Wacom tablet so the lines being included in xorg.conf is cool.

Hope this helps. Good luck!

Andrew

---

### Post by kerry_s on 2007-02-04
If your using edgy just delete or comment out all the font paths in /etc/X11/xorg.conf there always wrong. The new xorg auto scans for fonts.

```
Could not init font path element /usr/share/fonts/X11/TFF/, removing from list
Could not init font path element /usr/share/fonts/X11/OTF, removing from list
Could not init font path element /usr/share/fonts/X11/CID/, removing from list
```
 
Is because there not there i created links to the fonts i wanted, also some fonts are missing the fonts.scale and fonts.dir, this is what i went with.

TTF> i linked to msttcorefonts
OTF> linked to ttf-dejavu
CID> linked to Type1

Let me know which fonts you choose to link to, if i have them i can zip up the fonts.scale and fonts.dir and attach them for you, then you just unzip them and put them in the fonts directory.

---

