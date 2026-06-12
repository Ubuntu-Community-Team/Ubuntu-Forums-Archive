---
title: "Holding down charcater keys freezes mouse pointer"
date: 2008-06-10
forum: General Help
---

### Post by macaholic on 2008-06-10
Whenever I hold down a character key (anything except for ctrl, alt, shift, etc) the mouse pointer will freeze in position until I release the key. This makes playing games such as Nexuiz and Savage 2 neraly impossible, and any help would be greatly appreciated.

---

### Post by Rhubarb on 2008-06-10
If you have mouseemu in your xorg.conf (or even if you don't), then this should fix up your problems:

```
gksu gedit /etc/default/mouseemu
```

So it looks like:
```
# Defaults for mouseemu initscript (/etc/init.d/mouseemu)
# These are the default values on PowerPC. On all other architectures
# middle and right click are disabled by default. 
# Key codes can be found in include/linux/input.h in the kernel headers
# or by using `showkey` in a console.


#MID_CLICK="-middle 0 87"         # F11 with no modifier
#MID_CLICK="-middle 125 272"      # Left Apple Key (LEFTMETA) + click
#RIGHT_CLICK="-right 0 88"        # F12 with no modifier
#RIGHT_CLICK="-right 29 272"      # Left Ctrl + click
#SCROLL="-scroll 56"              # Alt key
TYPING_BLOCK="-typing-block 000"  # don't block mouse after a keypress
```
Note the typing block has been reduced from 300ms to 0.
Then just restart X / Ubuntu and all should be good.

---

### Post by macaholic on 2008-06-10
Thanks, I changed the configuration, I'm compiling webkit atm so I can't restart X, but will when it is finished.

---

### Post by macaholic on 2008-06-10
Nope, that didn't seem to work. Where would I add it in xorg.conf?

---

### Post by Rhubarb on 2008-06-11
You shouldn't have to add anything to your xorg.conf
What you describe is something that effects you if you setup a nintendo wii remote in ubuntu on non-mac hardware.

So I'm not too sure now if this is the source of your problem, or whether it's something else.

(mouseemu is a program that allows you to emulate right mouse clicks on a mac - and for some reason also effects pressing keyboard buttons while moving the mouse).

This is the post that I referred to (which fixed up my problem when using the wiimote + keyboard / mouse tracking problems on my PC):
[http://ubuntuforums.org/showpost.php?p=4054517&postcount=85](http://ubuntuforums.org/showpost.php?p=4054517&postcount=85)

---

### Post by macaholic on 2008-06-11
Sorry I was wrong, changing the mouseemu conf file worked, just not after I restarted X, I had to restart my computer, which probably restarted the mousemu daemon. Thanks for the help.

---

### Post by Rhubarb on 2008-06-11
And thanks for your help too, I'll know to keep my eye out for that problem if I ever come across it on a mac in future.

---

