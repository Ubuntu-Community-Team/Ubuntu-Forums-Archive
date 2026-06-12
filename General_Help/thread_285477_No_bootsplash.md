---
title: "No bootsplash"
date: 2006-10-26
forum: General Help
---

### Post by alekz on 2006-10-26
Hi, since i upgrade to Edgy i have problems with the bootsplash, after grub boots ubuntu there's no bootsplash anymore as i had on dapper, after several minutes the login screen appears, and same qhen i turn off the system, no splash, only black screen and then turns off, anyone knows what is happending here?

Thanks.

---

### Post by chippy99 on 2006-10-26
Try reinstalling the splash screen with sudo apt-get install usplash

Failing that try running sudo update-alternatives --config usplash-artwork.so. Which may (or may not) let you choose the ubuntu splash screen.

---

### Post by dpike619 on 2006-10-26
I'm having the same problem.  If I hit ctrl-alt-F1 while this is going on, I get this error message:

usplash setting mode 1920x1440 failed

---

### Post by alekz on 2006-10-27
hey! i tried to to that, i chose ubuntu splash, but is not working yet :( any other idea?

---

### Post by autocrosser on 2006-10-27
The new usplash has problems with certain screen resolutions--I bet you've been caught by this one---There were several threads about usplash about a month ago & there is a really neat little program called Usplash-Switcher -- I use it to change to a couple of different images people have done. My guess for your prob would be to edit your /etc/usplash.conf--i'm running 1024x768---I don't remember what settings do work---do a usplash search & it should turn up real quick---

---

### Post by mohn3310 on 2006-10-27
You may have to pass in the 'vga' parameter to the kernel. I was having the same problem where the bootup, shutdown screens as well as the virtual terminals were blank. After reading [this]("http://www.ubuntuforums.org/showthread.php?p=1541970") HOWTO, I made the change in grub and it started working.

HTH

---

### Post by dpike619 on 2006-10-27
> **autocrosser said:**
> The new usplash has problems with certain screen resolutions--I bet you've been caught by this one---There were several threads about usplash about a month ago & there is a really neat little program called Usplash-Switcher -- I use it to change to a couple of different images people have done. My guess for your prob would be to edit your /etc/usplash.conf--i'm running 1024x768---I don't remember what settings do work---do a usplash search & it should turn up real quick---

I tried this and now, I'm getting a splash screen when I shut down, but not when I boot up.  It still tells me "usplash setting mode 1920x1440 failed".

---

### Post by alekz on 2006-10-27
Well guys =( any of ur ideas has worked :( i've been spending 4 hours or more per day just to fix this and i can't find the solution? any other idea? ANYTHING!!! :P

Thanks.

---

### Post by chippy99 on 2006-10-27
What does it say in your /etc/usplash.conf file ?
Mine looks like this

# Usplash configuration file
xres=1600
yres=1200

---

### Post by alekz on 2006-10-27
Mine is this:


# Usplash configuration file
xres=800
yres=600


Should i change it ?

Thanks.

---

### Post by alekz on 2006-10-28
Hi, i've just solved the bootsplash problem, i just added the vga=773 option to my kernel grub line ( /boot/grub/menu.lst ) , i had to play with all the values that i found in [this]("http://www.ubuntuforums.org/showthread.php?p=1541970") howto that mohn3310 posted =).

Here is the tabble:

[HTML]Colours   640x400 640x480 800x600 1024x768 1152x864 1280x1024 1600x1200
--------+--------------------------------------------------------------
 4 bits |    ?       ?      770       ?        ?        ?         ?
 8 bits |   768     769     771      773      353      775       796 
15 bits |    ?      784     787      790      354      793       797 
16 bits |    ?      758     788      791      355      794       798 
24 bits |    ?      786     789      792       ?       795       799 
32 bits |    ?       ?       ?        ?       356       ?[/HTML]


Thanks a lot guys.

---

