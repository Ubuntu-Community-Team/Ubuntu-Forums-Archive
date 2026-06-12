---
title: "HELP !!! Can't boot to desktop"
date: 2006-10-14
forum: General Help
---

### Post by jaytu on 2006-10-14
Hi all

I can't boot to my desktop (ubuntu)... I was having trouble with the screen savers freezing the system, so I removed some screen saver setting from within synaptic manager. And after a restart the system will only boot to the user text prompt.

What have I done ??? and can I fix it ???

Any help would be appreciated. Thanks

---

### Post by PriceChild on 2006-10-14
You may have removed your gdm.

Log in then on the command line type
```
sudo apt-get update
sudo apt-get install ubuntu-desktop
sudo /etc/init.d/gdm start
```

---

### Post by taurus on 2006-10-14
Or you may need to reconfigure your X again with

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by jaytu on 2006-10-14
PriceChild: Thanks for the quick reply...I did as you suggested and it work great, I' now back to where I was. thankyou again !

Taurus: Thankyou also for your fast replyalso, I didn't get a chance to try your suggestion, but it would have been interesting as I'm sure i do remember seeing something about 'xserver' which  may have been removed at the time...hmmm. good to know for next time ! Thankyou

---

### Post by divali on 2006-10-21
Well, I had a similar problem: Logged in but, desktop would not start.

I did        >   sudo startx
and I got    > remove /tmp/something.d  (cant remember what). and restart.

It worked for me.

---

### Post by divali on 2006-10-22
Actually, removing XO.lock (for this is the message I recieved) isnt strictly true, it only worked once and now I'm stuck again no matter how many times I remove it, and I cant boot into the desktop again.

I tried your recommendations Taurus and Pricechild without any luck.
Maybe I could upgrade to edgy, but I'm a bit apprehensive. Its a rather 
big step for me to take.
Any suggestions?

---

