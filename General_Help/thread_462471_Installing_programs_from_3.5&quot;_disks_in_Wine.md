---
title: "Installing programs from 3.5&quot; disks in Wine"
date: 2007-06-02
forum: General Help
---

### Post by echomikeromeo on 2007-06-02
I'm trying to install (and play) an old Windows game on my Ubuntu machine, using Wine. The game is on four 3.5" disks, all of which have to be inserted sequentially in the installation process. The problem is that Ubuntu doesn't seem to let me unmount one disk and mount the next while the program using them (i.e. Wine) is running. Is there a way to get around this so that I can install the game?

---

### Post by yabbadabbadont on 2007-06-02
Some floppy based game installers will work if you copy all of the files from each floppy into a temp directory and then install the game from there.  You might try that and see if it will work.

---

### Post by echomikeromeo on 2007-06-02
Thanks very much! I managed to get the game installed. That, of course, has engendered another question, though: upon trying to run it I get the message that it "requires support for 256 colors." 

I'm completely clueless.

---

### Post by yabbadabbadont on 2007-06-02
That most likely means that you will need to switch your xorg session to use an 8 bit color depth...  I could tell you how to do it by editing your /etc/X11/xorg.conf file, but I doubt that is what you want to do every time you wish to play the game....  ;)

---

### Post by echomikeromeo on 2007-06-02
I found a handy script that makes it easy to switch back and forth between multiple xorg.conf files, so I'm going to try doing that -- is all I need to do in the xorg.conf file to change the DefaultDepth from 16 to 8?

---

### Post by yabbadabbadont on 2007-06-02
Sounds right.

---

### Post by echomikeromeo on 2007-06-02
No luck. It still says I need support for 256 colors.

---

### Post by yabbadabbadont on 2007-06-02
Try running winecfg and check the various settings.  Maybe there is something in there that needs to be enabled?

---

### Post by echomikeromeo on 2007-06-02
Hmmm, it doesn't seem like it. I tried a few things but none had any effect.

---

### Post by yabbadabbadont on 2007-06-02
Search the wine appdb for your game.  Perhaps there is information there on how to get it to work.  (or at least information telling you that it won't work)

Edit: [http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by echomikeromeo on 2007-06-03
Hmm, no luck. It's pretty obscure, though -- embarrassed though I am to admit it, the game is "Spelling Jungle" -- my absolute favourite when I was six years old. 

I have come to accept, though, that it is more unusual to get a program to successfully run under Wine than not.

---

