---
title: "cant get gui to load"
date: 2007-09-19
forum: General Help
---

### Post by driectly3d on 2007-09-19
can't figure out what to do.....
 
running:
amd64 4000+
dual geforce 6800 in sli
2 gb ram
dell trinitron monitor (should support damn near any resolution  i would think)

while installing ubuntu 7 desktop, i was unable to get the main installation interface working, the ubuntu splash screen would appear and load perfectly fine. then the screen would go black and i would hear what i am assuming is the ubuntu start noise. I was finally able to get it working with the alternate install disk

Figuring i was in the clear i boot......... same thing happens..... can get to the rescue mode..... but im completely new to linux any instruction or information on what i might try would be much appreciated

---

### Post by driectly3d on 2007-09-19
ok got further...... changed some bios settings....... now it pops up with a blue screen saying 

"x-server (your graphical user interface) failed to load, this could be because x-server is not configured properly would you like to see the x-server output so you can debug?"

not sure how to debug configure the x-server.....

---

### Post by driectly3d on 2007-09-19
ok.... read topic:

[http://ubuntuforums.org/showthread.php?t=83973&highlight=configuring+xserver](http://ubuntuforums.org/showthread.php?t=83973&highlight=configuring+xserver)

went through the auto configuration using

sudo dpkg-reconfigure xserver-xorg

getting errors:

no screen detected

---

### Post by Lord Illidan on 2007-09-19
Exactly what bios settings did you configure?

---

### Post by driectly3d on 2007-09-19
finally got it!....... had to go into "advanced" when configuring the monitor, the vertical refresh rate was off. It says that below 50 is extremely rare, mine happens to be 48

[http://www.microsoft.com/isapi/redir.dll?prd=ie&pver=6&ar=msnhome](http://www.microsoft.com/isapi/redir.dll?prd=ie&pver=6&ar=msnhome)


wow..... these forums are helpful! :KS

---

### Post by Lord Illidan on 2007-09-19
> **driectly3d said:**
> finally got it!....... had to go into "advanced" when configuring the monitor, the vertical refresh rate was off. It says that below 50 is extremely rare, mine happens to be 48

[http://www.microsoft.com/isapi/redir.dll?prd=ie&pver=6&ar=msnhome](http://www.microsoft.com/isapi/redir.dll?prd=ie&pver=6&ar=msnhome)


wow..... these forums are helpful! :KS

Can't figure out what MS has to do with it though :P

---

### Post by driectly3d on 2007-09-27
Lol sorry, the microsoft link was supposed to be a link to my monitor's specifications

[http://support.dell.com/support/edocs/monitors/p1110/En/specs.htm](http://support.dell.com/support/edocs/monitors/p1110/En/specs.htm)

still have default homepage on the xp machine i was using for internet access while troubleshooting, somehow that url got copied instead

---

