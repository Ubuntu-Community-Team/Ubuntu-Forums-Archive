---
title: "Mdadm help! How do I create a raid device?"
date: 2006-11-12
forum: General Help
---

### Post by cheuschober on 2006-11-12
Hi. I have two drives that used to be in an older system as raid 0 stripes configured with mdadm.

I have a new edgy installation that I'd like to bring these drives online. How do I initialize these drives in the new system without creating a new device and wiping out my data in the process?

As always your help is appreciated!
~Chad

---

### Post by cheuschober on 2006-11-12
midday bump.

---

### Post by iq_ali on 2007-01-26
Hi apologies for hijacking this post with my problems, but haven't worked out how to add a new thread.

I am a newbie to Linux and Ubuntu and am trying to install RAID using mdadm - possibly not a good idea but I like a challenge.

I have a 256MB RAM 1.3 GHz Intel machine. I am using one 80GB HDD for my OS, and two 320GB HDDs set up as RAID 0, or RAID 5 (I have tried both with the same problems).

1) I installed Xubuntu 6.06 without too many hitches (though I had to use IRQPOLL to boot the CD). 

2) I installed mdadm and used mdadm --create --level=0 --devices=2 /dev/hde /dev/hdg --auto=yes to set up RAID

3) Using cat /proc/mdstat I check the progress, and RAID is being built. However, the computer freezes after a while. When this happens, Xubuntu needs to be reinstalled.

I have used the following cards separately (to rule out the controller cards being the problem) 

a) SIL680 IDE Controller card
b) Promise FastTrak TX4 100 4 port IDE controller

Can anyone help me? I have no idea why this doesn't work.

Iqbal

---

### Post by matthewstory on 2007-01-26
to your initial question i don't know if you can create a superblock withouit wiping each drive once . . . at least with RAID 1 you can't, don't know about RAID 0, what i would do is back up your stuff, and then create the superblock and reload it.

---

