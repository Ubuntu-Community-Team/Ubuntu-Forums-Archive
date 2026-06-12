---
title: "Network shares try to mount before network is up"
date: 2005-06-09
forum: General Help
---

### Post by blixel on 2005-06-09
I have a few network shares setup in my /etc/fstab and I want them to automount when I boot.  The problem is the system tries to mount them before my network is available.  I have an 802.11b Orinoco PC-Card.

I see that pcmcia is set to start as S20 in the default runlevel (2).  I know I can lower that value to make pcmcia start sooner, but I'm not sure how soon it needs to start.

Also - I would prefer an alternative method to modifying the runlevel scripts if there is another way.

---

### Post by Takis on 2005-06-09
Yeah things could go funny if you edit runlevel stuff - what happens if pcmcia relies on something being loaded before it, and by editing the order they run you pre-empt it? No fun there.

What you might want to do is edit your /etc/fstab line and set that network mount to 'noauto', e.g.:
```
/dev/fd0        /media/floppy0  auto    rw,user,[COLOR=Blue]noauto[/COLOR]  0       0
```
And then create a script with runlevel > 20, say 'S21blixels_script', which has the mount command.

---

### Post by Abhi Kalyan on 2006-11-06
> **blixel said:**
> I have a few network shares setup in my /etc/fstab and I want them to automount when I boot.  The problem is the system tries to mount them before my network is available.  I have an 802.11b Orinoco PC-Card.

I see that pcmcia is set to start as S20 in the default runlevel (2).  I know I can lower that value to make pcmcia start sooner, but I'm not sure how soon it needs to start.

Also - I would prefer an alternative method to modifying the runlevel scripts if there is another way.
Hi,
Could you please help me with sutomounting using fstab.
Tried searching but no catch.
I have a windows share which i want automounted during boot, usinf the fstab,
Could you please help me with this. If it is not much of trouble.
Thank you
Sincerely
Abhi Kalyan

---

