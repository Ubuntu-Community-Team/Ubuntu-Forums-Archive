---
title: "GRUB: Boot directly into windows from ubuntu"
date: 2007-03-27
forum: General Help
---

### Post by misfit138 on 2007-03-27
I'm just wondering if there's a way to tell grub to reboot my computer (from ubuntu) and then automatically boot into windows XP, so I don't have to sit there and scroll down to the bottom and select Win XP from the boot menu before Ubuntu automatically loads after 15 seconds. 

Anyone know?

Thanks.

UPDATE: (moved from page 2)

So you want to boot directly into windows (or another OS) from ubuntu? Here's what you do:

```
sudo gedit /boot/grub/menu.lst

```

change "defaultnum" to 'saved':

```
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         saved
```

Make sure update-grub is set to 'false' (it should be this way by default)

```
## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false


```

Now, in your menu.lst file you should see a list of all the operating systems that come up under the grub boot menu. Starting from 0, count all entries until you find the OS you want to boot into. Make sure you count all entries, including ones like the following:

```

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root

```

Now do the following:

```
sudo grub-reboot [entry number]
```

where [entry number] is the entry number of the OS you want to boot into. For instance, in the following list:

```

title		Ubuntu, kernel 2.6.15-28-686
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-28-686 root=/dev/hdc2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-28-686
savedefault
boot

title		Ubuntu, kernel 2.6.15-28-686 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-28-686 root=/dev/hdc2 ro single
initrd		/boot/initrd.img-2.6.15-28-686
boot

title		Ubuntu, kernel 2.6.15-27-686
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-686 root=/dev/hdc2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-686
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-686 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-686 root=/dev/hdc2 ro single
initrd		/boot/initrd.img-2.6.15-27-686
boot

title		Ubuntu, kernel 2.6.15-23-686
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-686 root=/dev/hdc2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-686
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-686 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-686 root=/dev/hdc2 ro single
initrd		/boot/initrd.img-2.6.15-23-686
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdc1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

Windows XP, the very last entry, is 8.

so 

```
sudo grub-reboot 8 
```

Will automatically highlight Windows XP upon reboot, and after the timeout grub will boot into XP.

Thanks to bollix47 for pointing out grub-reboot, and everyone else who posted on this thread for their assistance.

---

### Post by floke on 2007-03-27
Edit your grub/menu.lst file so that it points to XP rather than Ubuntu.
See here for steps etc.

[http://ubuntuforums.org/showthread.php?p=2360250#post2360250](http://ubuntuforums.org/showthread.php?p=2360250#post2360250)

Remember to set the 'default' to the number in the list that XP is - count starts with ZERO!

Hope this helps

---

### Post by Jonne on 2007-03-27
edit  /etc/boot/menu.lst

( sudo gedit /etc/boot/menu.lst ).

Just change the order of the entries

---

### Post by mahy on 2007-03-27
In any case, you can press Page Down instead of scrolling :)

---

### Post by misfit138 on 2007-03-27
Actually, I think you misunderstood. I don't want Windows XP to be the default on GRUB, I actually use Ubuntu more. but occasionally, when I want to boot into Windows XP, I'd rather just hit restart and go to the bathroom or something, and then come back and have XP ready, rather than have to wait to select it. I tried writing my first script:

```

#!/bin/sh
sudo reboot
[password]
c
root (hd0,0)
savedefault
makeactive
chainloader +1
boot

```

in order to do this, but I don't know how to test for the condition that the grub boot menu is even open, nevermind the fact that i'm sure the script won't still be running after the computer reboots.

---

### Post by floke on 2007-03-27
I suppose one way to do this would be to write a script that altered the default line on grub/menu.lst before rebooting. you could then have a startup script that altered it back...??

No idea how you would do this though. Maybe get the source code for GrubEd and see how that tinkers with Grub (GrubEd available around here - just do a search in the forum search box and you'll find it).

---

### Post by zvacet on 2007-03-27
This is not exactly what are you looking for but I think you should give it try.
[http://ubuntuforums.org/showthread.php?t=380699&highlight=physical+windows]("http://ubuntuforums.org/showthread.php?t=380699&highlight=physical+windows")

---

### Post by bollix47 on 2007-03-27
Have a look at:

```
man grub-reboot
```

---

### Post by misfit138 on 2007-03-27
It looks like grub-reboot *should* do the trick. Unfortunately, I can't seem to get it to work. Supposedly, I simply run ```
sudo grub-reboot [entry number] 
```

where [entry number] is how far down my OS occurs in menu.lst, counting from 0, and seemingly not counting alternative versions of the same kernel. 

However, even if I run```
sudo grub-reboot 0
``` (which should boot me into Ubuntu) I still get the grub menu upon reboot! 

Here's my menu.lst file, can you guys spot anything out of place? 
I changed "default num" from '0' to 'saved' to see if that would fix it, but no luck.

```

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         saved

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry# (normally the first entry defined).
timeout         10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/hdc2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title           Ubuntu, kernel 2.6.15-28-686
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-28-686 root=/dev/hdc2 ro quiet splash
initrd          /boot/initrd.img-2.6.15-28-686
savedefault
boot

title           Ubuntu, kernel 2.6.15-28-686 (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-28-686 root=/dev/hdc2 ro single
initrd          /boot/initrd.img-2.6.15-28-686
boot

title           Ubuntu, kernel 2.6.15-27-686
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-27-686 root=/dev/hdc2 ro quiet splash
initrd          /boot/initrd.img-2.6.15-27-686
savedefault
boot

title           Ubuntu, kernel 2.6.15-27-686 (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-27-686 root=/dev/hdc2 ro single
initrd          /boot/initrd.img-2.6.15-27-686
boot

title           Ubuntu, kernel 2.6.15-23-686
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-23-686 root=/dev/hdc2 ro quiet splash
initrd          /boot/initrd.img-2.6.15-23-686
savedefault
boot

title           Ubuntu, kernel 2.6.15-23-686 (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-23-686 root=/dev/hdc2 ro single
initrd          /boot/initrd.img-2.6.15-23-686
boot

title           Ubuntu, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdc1
title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

---

### Post by Rhombuss on 2007-03-27
I'd be interested to know the resolution to this as well.  Having it boot directly into Windows would save valuable seconds for me :).

---

### Post by misfit138 on 2007-03-28
Allright! So I've figured it out. Actually, with my menu.lst as above, I think it was already working, I just didn't realize how. Apparently grub-reboot doesn't bypass the menu, it just highlights the entry number you selected so that when the timer runs out, that OS is booted. I suppose you could always modify the timer in menu.lst to 0 if you cared. 

The numbering does start from 0, but it doesn't skip any entries, which includes this one: ```

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root

```

Which isn't an operating system at all. So in my menu.lst file, Windows XP is actually 8.

It *is *necessary to change "default" to saved:
```
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         saved
```

I think this is how grub-reboot actually works, by temporarily changing your default to whatever you feed it. However, you *don't* want to change "updatedefaultentry" to 'true,' you want to leave it false:

```
## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false


```

otherwise the next time you restart your computer normally, the default will still be set to Windows (or whatever you used grub-reboot for last time)

Hope this helps anyone who was trying work this out for themselves.

---

### Post by vav on 2007-04-06
That wiki page makes it clear... but it would be nice to have a little UI around it, either as a panel applet or directly integrated into the restart button... so that you dont have to type anything and more importantly dont need to remember the *number* of the OS to boot...

The time it takes me to figure that out and type out those commands is almost the same as just hitting reboot and waiting for grub.

---

### Post by lssl on 2007-04-09
I'm not using Windows but i think this should work with Win too.
I'm using [bootnext]("http://www.dcheng.members.sonic.net/friends/jspaar/pub/bootnext/") to boot directly into another system without changing the default one.
Here is what you have to do:
1. Edit your menu.lst
- set default value to saved```
default saved
```
- set some low value for timeout (for example 2 or 3)```
timeout 2
```
- remove ```
title Other operating systems: 
root
```
- add savedefault option to every entry> title Ubuntu, kernel 2.6.17-11-generic 
root (hd0,1) 
kernel /boot/vmlinuz-2.6.17-11-generic root=/dev/hda2 ro quiet splash 
initrd /boot/initrd.img-2.6.17-11-generic 
quiet 
[COLOR="Red"]savedefault[/COLOR] 
boot 

title Ubuntu, memtest86+ 
root (hd0,1) 
kernel /boot/memtest86+.bin 
quiet 
[COLOR="Red"]savedefault[/COLOR]
boot 

### END DEBIAN AUTOMAGIC KERNELS LIST 

title Ubuntu Feisty 
root (hd0,3) 
kernel /boot/vmlinuz-2.6.20-13-generic root=/dev/sda4 ro vga=792 
initrd /boot/initrd.img-2.6.20-13-generic 
[COLOR="Red"]savedefault[/COLOR]

2. Create bootnext file
```
sudo gedit /usr/bin/bootnext
```
and paste this
```
#!/usr/bin/python 

# bootnext: Tell GRUB what kernel to boot for the next boot only, and reboot 
# 
# Allows user to choose which OS to reboot into for next reboot only. 
# Useful for folks who dual-boot another OS occasionaly but don't want to 
# permanently change the default. 
# 
# Default menu choice is set to match expression DEFAULT_TITLE_RE. 
# Must be run with superuser priveleges. 
# The menu is graphical, and requires that X be running. 
# 
# Written by Jack Spaar <jspaar-at-myrealbox-dot-com> 
# Released under the terms of the GNU General Public License. 
# 
# Changelog: 
# Wed Feb 11 20:01:30 PST 2004 -- Created. 
# Wed Mar  3 18:05:05 PST 2004 -- added OK/Cancel prompt. 
# Sun Mar 14 22:28:07 PST 2004 -- use zenity to choose grub title to boot. 
# Fri Jun 11 14:04:33 PDT 2004 -- use --batch with grub. 
# Tue Nov 30 20:47:31 PST 2004 -- use --no-floppy to avoid probe hang on FC3. 
# Thu Jan 27 22:32:41 PST 2005 -- allow a regex for finding default title 
# Wed Feb  2 19:56:11 PST 2005 -- allow default title on command line 
# Tue Aug 23 18:42:37 PDT 2005 -- packaged as rpm 
# Sat Dec  2 00:00:34 PST 2006 -- use absolute path for zenity, tweak win width 
# 
# v0.10 

import re, os, sys 

progName = "bootnext" 

# Edit the following to set the default menu selection 
DEFAULT_TITLE_RE = "(?!.*Ubuntu)"    # match first non-Ubuntu title. 

GRUB_CONFIG = "/boot/grub/menu.lst" 
GRUB_PATH =  "/sbin/grub --batch --no-floppy" 
DIALOG_TEXT = "Select which OS to boot:" 

ZENITY_PATH = "/usr/bin/zenity" 
ZENITY_WIDTH = 320 
ZENITY_HEIGHT = 325 

def grub_title_list(): 
    f = open(GRUB_CONFIG, 'r') 
    lines = f.readlines() 
    f.close() 

    p = re.compile('^\s*title\s*(.*)') 
    tlist = [] 

    for line in lines: 
        m = p.match(line) 
        if m : 
            tlist = tlist + [ m.group(1) ] 

    return tlist 


## MAIN 

if (len(sys.argv) > 1) : 
    default_title_re = sys.argv[1] 
else: 
    default_title_re = DEFAULT_TITLE_RE 

titles = grub_title_list() 

# form a zenity command to allow user to select from the grub title list 
zen = '%s --width %d --height %d --list --radiolist --title "%s" --text "%s" --column "Selected" --column  "Boot Title"  ' % (ZENITY_PATH, ZENITY_WIDTH, ZENITY_HEIGHT, progName, DIALOG_TEXT) 

p = re.compile(default_title_re) 
default_found = 0 
for title in titles: 
    # Turn on radio button for 1st title matching DEFAULT_TITLE_RE 
    if ((not default_found) and (p.match(title))): 
        zen += " TRUE "        
        default_found = 1 
    else: 
        zen += " FALSE " 
    zen += "\"%s\"" % (title) 

# run zenity and grab the user's choice 
pipe = os.popen(zen, 'r') 
choice = pipe.read().strip("\n") 
okCancel = pipe.close() 
if (okCancel != None): 
    print "Cancelled." 
    sys.exit(okCancel) 

# convert the title to a grub index number 
num = 0 
for title in titles: 
    if (title == choice): 
        break 
    num += 1 

# Now tell GRUB we want that other OS for the next boot only 
grubCommands ='savedefault --default=%s --once\nquit\n'%(num) 

pipe = os.popen(GRUB_PATH, 'w') 
pipe.write(grubCommands) 
pipe.close() 

# Now reboot 
os.system('/sbin/shutdown -r now &') 

sys.exit(0)
```
line ```
GRUB_CONFIG = "/boot/grub/menu.lst" 
``` should point to your menu.lst

save the file and make it executable
```
sudo chmod +x /usr/bin/bootnext
```

3. Create a menu entry
```
sudo gedit /usr/share/applications/BootNext.desktop
```
and paste
```
 [Desktop Entry] 
Version=1.0 
Encoding=UTF-8 
Name=BootNext 
Type=Application 
Terminal=false 
Exec=gksudo /usr/bin/bootnext 
Icon=/usr/share/icons/gnome/48x48/apps/gnome-session-reboot.png 
Categories=Application;System;
```
Save and exit.

Now go to Applications->System Tools->BootNext and have fun.

One more thing. With option 'default saved' every time you chose a system manualy to boot in grub menu (not bootnext) it will be saved as a default system to boot.

sorry for my english ;)

---

### Post by Rhombuss on 2007-04-24
I just tried the solution posted by the OP on the first post.  All I did was changed the default to "saved" and entered the grub report [x] command, and now it's having problems starting up Ubuntu.

I get this error message on all the non-recovery Ubuntu kernels:

**Error 18: Selected cylinder exceeds maximum supported by BIOS**

I've searched around and it usually is the result of some boot partition issue, however the only thing I changed was the "saved" in the menu.lst.  Consequently, I changed it back to the "defaultnum" and no dice, it still gives me this error.

Any help or insight is appreciated!

---

### Post by JoeCool1986 on 2007-07-01
You forgot one step that might trip someone up (it did me) in this little how-to:

[B]All the entries that you want to be able to boot into with grub-reboot need to have the "savedefault" command in them.
[/B]

Otherwise, grub will keep booting into that same entry after you use grub-reboot on it until you manually select a knew one by hitting Esc.

However, though this works, it doesn't make sense because savedefault should only technically be used once in your menu.lst to show grub the normal, default entry, right? And using it more than once means that grub just goes to your first entry since it can't figure out which one you wanted it to default to. But, in the end, this is the only way to get a single reboot into another OS using grub-reboot that I know of.

Does anyone know why this is?

---

