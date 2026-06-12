---
title: "One too many xorg.cong files....."
date: 2005-07-18
forum: General Help
---

### Post by astronerd on 2005-07-18
Hi all, to make a long story short I lost the ability to use my mouse scroll wheel when I had to mess with my xorg.conf file.  I didnt touch anything in the mouse section, but when I restarted xorg.conf it just shut off the scroll wheel.  Anyway, I have been looking on here and other place on how to get it to work again, but every time I edit the file and save it, it just makes another xorg.conf file and adds ~ to the end of it.  Here is my ls /etc/X11/   result.

pp-defaults             rstart      xorg.conf~~     Xsession
cursors                  sysconfig   xorg.conf~~~    Xsession.d
default-display-manager  X           xorg.conf.copy  Xsession.options
fonts                    xinit       xorg.conf.old   xsm
gdm                      xkb         Xresources      Xwrapper.config
rgb.txt                  xorg.conf~  xserver

So I dont know what the deal is, or if this is part of the reason why my mouse isnt working.  Which xorg.conf file is it using?  Should I just delete them all and then just save one as xorg.conf with the "correct" mouse settings in it?  I have looked all over, but cant find anything.  I can print out the mouse part of (I guess anyone) the xorg.conf files.  And its just a normal dell 2 button mouse with scroll wheel.  
Thanks, 
Charles

---

### Post by Nimefurahi on 2005-07-18
Hmmm... that's a bit confusing. It appears to me that you have:> xorg.conf~
xorg.conf~~
xorg.conf~~~
xorg.conf.copy
xorg.conf.old I see 5 configuration files, but nowhere do I see a viable xorg.conf.

Assuming that xorg.conf.old was the working configuration before your experimentation, you may want to: ```
cd /etc/X11
sudo cp /etc/X11/xorg.conf.old  /etc/X11/xorg.conf
```Mind you, that is assuming xorg.conf.old was the best that you originally had.
Then just follow (with minor embellishment) the code as published in xorg.conf:
```
cd /etc/X11
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
sudo dpkg-reconfigure xserver-xorg
``` You'll be building your new xorg.conf. Pay close attention to _Emmulate 3 button mouse_ <YES>
and _Enable scroll events from mouse wheel_ <YES>.
Pay no attention to the yellow smoke coming out of your disk drive bay, and let me know how this works.

---

### Post by astronerd on 2005-07-18
See, I think that the xorg.conf.old was the original one.  It all happened cause I couldnt get my screen resolution the way I wanted so I messed with that, and eventually had to do the 

sudo dpkg-reconfigure xserver-xorg

command to restart everything.  And when I did that I made sure to use the enable scroll button.  And thats when it stopped working and making replicate copies.  They are pretty much all exactly the same.  I think one is different cause I tried to used the differnent ATI drivers, but I hadnt touched the mouse section in any of em.  I can print that part out if necessary.  Is there any other way besides building a new xorg.conf again?  I just seem to be losing things every time I try and make a new one....  If thats the only way to do it, then I guess I will though.....

---

### Post by Nimefurahi on 2005-07-18
The "mouse" section of my xorg.conf looks like:```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection
```
I have an USB mouse, so the device is /dev/input/mice. You may see /dev/psaux instead.

If you sudo dpkg-reconfigure xserver-xorg, be very attentative to your responses and make record of these on a scratch pad. Sometimes, in the additional call for more of your cerebral resources, (writing down what your doing whilst responding to the configuration wizard) an error or omission may pop out at you, and you'll wonder how you've overlooked this before.

---

### Post by astronerd on 2005-07-20
So I went ahead and did the
 sudo dpkg-reconfigure xserver-xorg

command and reconfigured my xorg.conf.  First I did what was suggested earlier

malespin@malespin:/etc/X11$ sudo cp /etc/X11/xorg.conf.old  /etc/X11/xorg.conf
Password:
malespin@malespin:/etc/X11$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custommalespin@malespin:/etc/X11$ sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'

then did the reconfigure.  I made sure to check all my answers and then I did ls again in /etc/X11 after it was done to see what I got....

xserver-xorg  postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.200507192321
malespin@malespin:/etc/X11$ ls
app-defaults             sysconfig    xorg.conf~~~            Xsession
cursors                  X            xorg.conf.200507192321  Xsession.d
default-display-manager  xinit        xorg.conf.copy          Xsession.options
fonts                    xkb          xorg.conf.custom        xsm
gdm                      xorg.conf    xorg.conf.old           Xwrapper.config
rgb.txt                  xorg.conf~   Xresources
rstart                   xorg.conf~~  xserver

so now I have an xorg.conf without a ~ along with a couple new ones.  And it still doesnt work!  Did I miss something or mess somethign up?  and my xorg.conf has this in it for the mouse section...

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Any ideas!!
Thanks, Charles

I forgot to add that when I push the middle button down to auto paste a highlighted area, that works fine still.  just not the scrolling up/down

---

### Post by Nimefurahi on 2005-07-20
Thanks!

I feel  better knowing that you have a new /etc/X11/xorg.conf.

May I see it, please.

---

### Post by astronerd on 2005-07-20
Well its the weirdest thing.... I booted up this morning and I get a message that says  "Your X keyboard settings are different from your gnome settings.  Which settings would you like to use?"   So I thought, great more problems.  But it turns out that my mouse works now and everything is back to normal!  So problem resolved.  Thanks for all the help everyone!

---

