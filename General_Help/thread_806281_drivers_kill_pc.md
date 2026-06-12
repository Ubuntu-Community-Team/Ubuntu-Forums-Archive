---
title: "drivers kill pc"
date: 2008-05-24
forum: General Help
---

### Post by Rita G. on 2008-05-24
every time i install drivers for ati graphics card(radeon x1650 pcie)ubuntu 8.04
 
and reboot; screen goes black  
 
little white box says “no signal” 
 
..........then...........the total...... 
 
BLACK SCREEN OF DEATH! 
 
monitor shuts off (light turns orange), but computer power is still on. 
 
no keyboard response 
 
had to push and hold power button on box to reboot. 
 
will reboot to grub, and after selection continue about 20-25 seconds to a blank white screen w/mouse pointer functional, but no keyboard function.

had to hold power button to reboot.
 
tried ubuntu in recovery mode and tried all options:
resume.....brings it back to a blank white screen
dpkg.......brings it right back to recovery menu
xfix........also brings back to recovery menu
root........i entered dpkg-reconfigure xserver-xorg
and get the series of xserver questions and GET STUCK during keyboard configuration
and text reads:
xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/X11/xorg-conf.20080524190620                                                        
root@rgp-02:~#_

..so....what do i enter here?

---

### Post by cutout33 on 2008-05-24
You need to boot from the live cd and in terminal type
```
sudo gedit /media/disk/etc/X11/xorg.conf
```
note that "disk" may vary from time to time so check the name on yours.
then go and open the file
/media/disk/etc/X11/xorg-conf.20080524190620 
and copy it's content into the first one save and exit then restart your computer
it should work fine...(no guarantees)

for the ati driver to work try googling flgxr for ubuntu hardy.

---

### Post by Rita G. on 2008-05-25
doesn't work

ubuntu@ubuntu:~$ sudo gedit /media/disk/etc/X11/xorg.conf
ubuntu@ubuntu:~$

---

### Post by cutout33 on 2008-05-25
what doesn't work???
if the command opens an empty file this is due a wrong path "disk" s I explaind in my first replay you need to navegate to your original /etc/X11/xorg.conf not the one created when ubuntu launches from the live cd and it will be 
/media/"Something"/etc/X11/xorg.conf
so go and find "Something" by going to Places>Computer
and search inside the media folder for your path

---

### Post by RadarBat on 2008-05-25
Rita,  You have described my problem exactly. The only difference is that I have an ASUS M2A-VM motherboard with onboard ATI Radeon X1250 graphics.
May I join your thread? Ben

---

### Post by Rita G. on 2008-05-25
hi ben

join the party!

asus M2A-MVP    radeon x1650

are you thinking what i am?
-------------------------------
i forgot to mention:

same thing happens in opensuse & win xp

---

### Post by Rita G. on 2008-05-26
solved that problem.

went & got a nvidia card.

---

### Post by RadarBat on 2008-05-27
Ms. G.,
What nVidia card? And what effects do you now get that you couldn't before? Batty

---

