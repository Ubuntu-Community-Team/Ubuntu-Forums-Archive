---
title: "Help with usplash"
date: 2008-01-07
forum: General Help
---

### Post by paranoiahax on 2008-01-07
Hi, I'm experiencing some trouble at my Usplash screen, I load grub as usual, select ubuntu, and it goes to the usplash screen, and loads marginally (like a bar of orange can be seen right at the beginning) but freezes. I check what's going on by pressent alt + ctrl + f1 and I get this:

> Starting up...
Loading, please wait...
usplash: Setting mode 1280x1024 failed
usplash: Setting mode 1152x864 failed
usplash: Using mode 1024x768

and it just stays there and doesn't do anything, so i have to hold down my power button until i restart my computer. i reckon it has something to do with my grub, because i have been changing and adding stuff to my grub recently, and it's done this before. so i chmod my grub directory to wr-r--r-- (644 i believe) and it's worked before, but this time it's not working. has anyone got any ideas?
I've tried the usual process of sudo grub, root (hd0,3) setup (hd0) etc. etc. but this has not worked. is there anyway to completely reinstall my grub?

thanks in advance, Para

---

### Post by spiderbatdad on 2008-01-07
the file you need to edit is /etc/usplash.conf```
gksu gedit /etc/usplash.conf
```
change the values to 1024, 768 respectively and save. Hope that helps you.

---

### Post by Tristam Green on 2008-01-07
whats your resolution?  

cat /etc/usplash.conf to check

edit woo someone's faster than i am.

---

### Post by paranoiahax on 2008-01-07
1024x768 i believe.. 

in my usplash.conf i have :

# Usplash configuration file
xres=
yres=

so do i do

# Usplash configuration file
xres= 1024
yres= 768

or is it the other way around?

I hope this works, i'll try both lol, and i'll let you know thanks for help

---

### Post by Perpetual on 2008-01-07
After you do what was stated above, make sure you do the following or it won't work.

```

sudo update-usplash-theme usplash-theme-ubuntu

```

---

### Post by spiderbatdad on 2008-01-07
> **paranoiahax said:**
> 1024x768 i believe.. 

in my usplash.conf i have :

# Usplash configuration file
xres=
yres=

so do i do

# Usplash configuration file
xres= 1024
yres= 768

or is it the other way around?

I hope this works, i'll try both lol, and i'll let you know thanks for help



yeppers but no space xres=1024 yres=768   Also...how are you booting? You're not reading that from the live cd are you...unless you've booted from the live cd and mounted your existing filesystem?

---

### Post by paranoiahax on 2008-01-07
right that didn't seem to work, i did it without the spaces. 

because i'm using the live disk "sudo update-usplash-theme usplash-theme-ubuntu" won't work. I've mounted it to /media/disk so i can't run any commands that would directly effect my ubuntu partition because of the fact i'm using live.

how would i edit the /boot/initrd.img-2.6.22-14-generic on my hard drive?

---

### Post by paranoiahax on 2008-01-07
anybody? sorry if i seem impatient but i've been trying to fix this all evening! and it's really annoying me, i've had no end of problems with Ubuntu in the past month

---

### Post by spiderbatdad on 2008-01-07
i believe your system will boot to do the edits, but it takes about 5-6 minutes of waiting. Have you checked the beginner's forum? There is generally much better response, due to higher participation.

---

### Post by paranoiahax on 2008-01-09
okay thanks, i got rather impatient with waiting for it, is that the safe mode alternative? and thanks for that advice, i'll use that forum instead.

i'll get back to you lol

---

### Post by paranoiahax on 2008-01-11
nope, the recovery mode didn't work, i was greeted with a shell that i couldn't do much with. i left the screen loading up for a good 10 minutes and then it just gave me the recovery mode shell from there and it was rather useless for this...

how anyone with any ideas how to fix this?

---

### Post by cwgannon on 2008-02-03
If you can get to a shell, use

```
sudo nano /path/to/file
```

From there, edit the file as needed (using your keyboard).  To save and exit and whatnot, press Ctrl and the corresponding letter indicated at the bottom of the screen.

Good luck.

---

