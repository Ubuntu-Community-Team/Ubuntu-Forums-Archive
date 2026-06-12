---
title: "samba traffic"
date: 2005-04-07
forum: General Help
---

### Post by mrt on 2005-04-07
I mount a samba share via smbfs in fstab.  I have the System Monitor in the top bar, which shows this on again/off again network traffic:
[IMG]http://miket.sixbit.org/images/samba.png[/IMG] 
The first box is cpu usage, the second is network activity.  The activity is like that all the time.
Why is it doing that (I'm sure its the samba share)?
Here is the line that mounts it:
```
//server/shared /media/shared   smbfs credentials=/root/.smbcredentials,dmask=777,fmask=777  0 0
```

---

### Post by dataw0lf on 2005-04-16
This is probably an issue with the System Monitor network traffic utility, rather than Samba itself.  Have you looked at the network traffic with a decent utility yourself? (iptraf, ntop, etc)

---

### Post by tkiesel on 2005-05-07
I've been experiencing the same issue ever since upgrading to Hoary. Exploration with iptraf revealed that it was indeed traffic to port 445 on my wife's XP computer. Unmounting all mounted shares eliminated the traffic.

I doubt that this level of traffic will cause serious issues for me (small home network, not really heavily loaded) but it was amounting to a couple hundred packets a second, and about 130 kbps (local) bandwidth use, and the constant flickering of my network traffic panel indicator. A little annoying, to say the least.

---

### Post by skirkpatrick on 2005-09-03
I may have figured out when this is triggered to start happening but I'm not sure what to do about it.  I setup a new computer and mounted a Samba share from my server.  I've copied files from it and no weirdness.  Tonight, I wrote a couple of files to the Samba share and now the Network Connection applet shows a constant small amount of traffic.  If I unmount the Samba share, it stops but starts up again when I remount it.  I've got noatime as one of the options in fstab.  Anybody got a clue as to why this stupidity is happening and how to stop it?

---

