---
title: "Grub error 21 at startup. Need help :("
date: 2007-04-29
forum: General Help
---

### Post by jamesjdk on 2007-04-29
Hey everyone, I'm new to Ubuntu and Linux and have just installed Ubuntu 7.04 on a partition on an external hard drive. The idea behind this was so I could try out Ubuntu and all it's features but with out risking damage to my main XP system. Now it's installed I can't boot into either Ubuntu or Xp and always get the following message when I try to. 

Grub loading stage 1,5
Grub loading. please wait...
Error 21

the screen then freezes and all I can do is restart by either pressing ctrl-alt-del or push the on off switch at which point the exact same thing happens. I've tried booting with the external hard drive unplugged or by changing boot order by holding esc at start up and it doesn't work.

I've googled this problem and have tried following the solutions given but haven't been able to  fix it. Could someone please please provide an idiot proof solution to this problem. I've recently backed up so re-installing windows isn't too much of a problem if need be.

Thank you so much

James

---

### Post by jamesjdk on 2007-04-29
Just thought i'd add that booting with the Ubuntu cd still works and the ubuntu partition is expendable is deleting that would help.

Thanks again

---

### Post by confused57 on 2007-04-29
What happened is that grub was installed to the internal drive's mbr...you'll need to fire up the Window's install cd and restore the mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

Before you do this...boot up the Ubuntu cd, open a terminal(Applications---Accessories---Terminal), enter:
```
sudo grub
find /boot/grub/stage1
```
this will show where your root partition is, e.g "root (hd1,x)
then enter:
```
root (hd1,x)
setup (hd1)
quit
```

Then remove the live cd, reboot, but set your external drive to boot before your internal drive...you should get a grub menu...if you do, highlight your Ubuntu entry, press "e", change root from (hd1,x) to (hd0,x), then press "b" to boot.

You'll still need to repair your Window's drive mbr before you can boot your pc without the external drive connected.

---

### Post by jamesjdk on 2007-04-29
Great thanks, i'll give that a try. Only problem is i'm at Uni and the cd is at home, typical :)

---

### Post by vladverzeni on 2007-05-02
Hi there.

So yesterday I was laying on my bed looking at my music when suddenly my computer turned off.  When I turned it back on I too got the Error 21 for GRUB.  This is very disconcerting as I do not have a Live CD for Ubuntu or XP and currently don't have a way to get them (mainly thinking of XP).

Is there anyway to do this without those CDs?


Also, on my GRUB screen I had two options for XP, the first of which always started the proccess of reformatting.  This was OK, I had a sign on my computer warning of it and it was just never a problem.  My worry though is that this might complicate things, right now I would really not like to have to reformat that drive.

kk

gatta go back to work, !thank !you

---

