---
title: "Adding New Hardware"
date: 2007-04-30
forum: General Help
---

### Post by Bill2003 on 2007-04-30
I am using version 7.04 and have installed it and it works fine. I have now added a TV card to my system but I can't find a way to get Ubuntu to detect it. In Window XP, I just go to Add Hardware and it will scan the computer and detect the new hardware. Is there a way to do this from within Ubuntu?

Bill

---

### Post by ceno-byte on 2007-04-30
hey there bill2003 what kind of tv card is it? and have you checked to see if it was compatible with linux before installing it? it may not be compatible with linux or you may have to see if there are linux drivers for it

---

### Post by Bill2003 on 2007-05-01
Hello ceno-byte,

I am using a Hauppauge WinTV 61295 Card based on the 878 Chip. On their web site they say that the drivers are all ready in any Kernel from 2.2 onwards. The web site address where I found this information is [http://www.hauppauge.com/pages/support/support_pci_878.html#win](http://www.hauppauge.com/pages/support/support_pci_878.html#win) The Linux info is near the bottom of the page.

I installed the card AFTER installing Ubuntu 7.04

When I start 7.04, is has not detected the card and I can find no reference to it within the system.

Kind regards

Bill2003

---

### Post by beerorkid on 2007-05-01
well i am using a hauppauge 250 so I might be able to give ya a few pointers.  Although I use it a bit differently than most would.  But it should at least let you know if yours is usable.

Good thing is the ivtv drivers are installed by [default in feisty]("https://help.ubuntu.com/community/Install_IVTV_Feisty").  All I had to do was install the utils to change the channel. ```
sudo apt-get install ivtv-utils
```

from [here]("http://hyams.webhop.net/mythtv/myth_ubuntu.html")  ( section 5.3)I use the commands to capture stuff but it is just a split off the output of my cable box so I cannot change channels.  although I need to switch to channel 3, so the utils help me here.  I do a:
```
ivtv-tune -c 3 -d /dev/video0
```

so get into a terminal and cd to the desktop and do a 
```
cat /dev/video0 > /tmp/test.mpg
``` hit control C to stop it.  And it should make a test file.  you might have to change to another device though.

not sure if it will help you, just trying to help.

---

### Post by gsimpson on 2007-05-02
Back to the original question. Is there a way to scan for added hardware?

I am trying to install an external modem in a friends computer. I am familiar with Mandriva but there is no obvious equivalent to hard drake of Mandriva.

---

