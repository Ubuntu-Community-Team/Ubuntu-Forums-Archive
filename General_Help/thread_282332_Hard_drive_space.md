---
title: "Hard drive space?"
date: 2006-10-22
forum: General Help
---

### Post by DougieFresh4U on 2006-10-22
A few simple questions, for some. When I put ubuntu on this machine (there was nothing ever on before) I didn't partition. I gave the whole mess to ubuntu when promted at the question. Now how do I know how much of my 40 GB hard drive is used and how much of my RAM space is being used up?. I primary use the machine for music:: amarok, Listen, totem, rhythmbox, online radio and some web surfing. Also E-mails and Gaim. I also play the games that came with ubuntu. I want google earth but have alot of problems getting stable picture (another whole mess). Am I wasting a decent machine on so little bit of use(no programing)? I have a few post on the google thing but have not gotten any useful answers.  Thank for any input and help.

---

### Post by taurus on 2006-10-22
To see how much space is or or left, open a terminal (Applications -> Accessories -> Terminal) and type

```
df -h
```
And to see about your RAM and swap, run

```
free
```

---

### Post by DougieFresh4U on 2006-10-22
Hi taurus! I guess Ihave alot of space and nothing to do with it, Thanks!!                                                                                             dougie@DougiesToyBox:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              37G  5.1G   31G  15% /
varrun                125M   96K  125M   1% /var/run
varlock               125M  4.0K  125M   1% /var/lock
procbususb             10M  100K   10M   1% /proc/bus/usb
udev                   10M  100K   10M   1% /dev
devshm                125M     0  125M   0% /dev/shm
lrm                   125M   18M  107M  15% /lib/modules/2.6.17-10-386/volatile
dougie@DougiesToyBox:~$ free
             total       used       free     shared    buffers     cached
Mem:        255068     249584       5484          0       4088     103296
-/+ buffers/cache:     142200     112868
Swap:       746980      80124     666856

---

### Post by DougieFresh4U on 2006-10-22
can some one explain a little bit for me?

---

### Post by DougieFresh4U on 2006-10-24
maybe I can repartition to add puppy linux? How?

---

### Post by CatKiller on 2006-10-24
> **DougieFresh4U said:**
> maybe I can repartition to add puppy linux? How?

I've never used any other distro, but you can boot from the Ubuntu disc and use GParted to resize your existing partition. Then you can optionally make a new partition in the space you made, or leave that to the Puppy installer.

---

### Post by DougieFresh4U on 2006-10-24
Thanks catk. I tried before and puppy and ubuntu didn't play nice and broke my system. (maybe operator errorr Ha Ha!) so I am a little reluctant to let puppy installer do the work. I am gonna read about partitioning with ubuntu disc, with a 40 GB hard drive I should be doing some thing w/it instead of having all that empty space, right?

---

### Post by CatKiller on 2006-10-24
> **DougieFresh4U said:**
> with a 40 GB hard drive I should be doing some thing w/it instead of having all that empty space, right?

That's what Creative Commons films are for :mrgreen: And you listen to music, surely?

---

### Post by DougieFresh4U on 2006-10-24
most definitly!!

---

### Post by CatKiller on 2006-10-24
> **DougieFresh4U said:**
> most definitly!!

Well, it is convenient to have your cd collection available as .oggs to listen to without getting up. And any number of bands and record labels have mp3s available on their sites to download. Go wild - I'd love to have an extra 40 Gigs available.

---

### Post by DougieFresh4U on 2006-10-24
Understood. Will do! Thanks :cool: Maybe you could look at mt other thread on pg.2  about google earth?

---

