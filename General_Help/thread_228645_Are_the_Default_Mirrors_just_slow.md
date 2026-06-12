---
title: "Are the Default Mirrors just slow???"
date: 2006-08-03
forum: General Help
---

### Post by ScatterBrain on 2006-08-03
Is it me, or are the default Ubuntu Mirrors (mainly us.archive.ubuntu.com and security.ubuntu.com) just freaking slow today.  I've got a very fast line to internet (45Mb/s) and I'm only getting updates downloaded at around 10Kb/s.

Did I just pick a bad day to update/upgrade?

---

### Post by aceracer24 on 2006-08-03
I am actually suprised there is not more complaints, yes, something seems to be down, I was doing fine and then suddenly everything came to a screeching hault. There was one other post about it as well , I guess just be patient and hold off for now with upgrades :(

---

### Post by IYY on 2006-08-03
Mine is barely moving...

---

### Post by Chibi on 2006-08-03
Getting no connection at all to security. and archive. , bad timing for a server crash, I was just about to upgrade to edgy for testing. :|

---

### Post by mlind on 2006-08-03
Yup, This is a problem for me too..

/edit
I changed to another mirror, works well now [https://wiki.ubuntu.com/Archive](https://wiki.ubuntu.com/Archive)

---

### Post by Ramses de Norre on 2006-08-03
Working reasonable here.. I'm not using any countrycodes in my url's.

---

### Post by Riverside on 2006-08-03
gb.archive.ubuntu.com has been extremely slow today, with connections timing out frequently also.  Since this is it seems an issue affecting us.archive.ubuntu.com & security.ubuntu.com additionally, it is unlikely to be a server crash (the odds of three such servers crashing concurrently is somewhat remote).  Presumably, the volume of today's updates, and the number of Ubuntu users simultaneously downloading them, is overloading available resource.

A good issue for Ubuntu to have in one way, since it shows Ubuntu's popularity.  As the distribution grows further in popularity it is likely to get worse though, so more servers and/or bandwidth may need to be provisioned.

---

### Post by ba5e on 2006-08-03
I get this:

99% [Waiting for headers]


of security.ubuntu.com 

and can't find a mirror for this!

---

### Post by Turgon on 2006-08-03
In pure frustration over this slowness I compleatly destroyed my packagesystem:(](*,)

---

### Post by abandoned_hussam on 2006-08-03
I think most country codes actually redirect to two to three main servers.
```
hussam@LARS:~$ host ca.archive.ubuntu.com
ca.archive.ubuntu.com has address 82.211.81.182
hussam@LARS:~$ host lb.archive.ubuntu.com
lb.archive.ubuntu.com has address 82.211.81.182
hussam@LARS:~$ host archive.ubuntu.com
archive.ubuntu.com has address 82.211.81.182
hussam@LARS:~$ host gb.archive.ubuntu.com
gb.archive.ubuntu.com has address 82.211.81.182

```

---

### Post by nix4me on 2006-08-03
I've noticed the slowness too.

I use to be able to pull 1200K per second, now i get 45-90K.

Started a week or so ago.

nix4me

---

### Post by Danny Boy on 2006-08-04
Just noticed it today, installed Ubuntu on a laptop and updating from the CD install is really slow. 

I installed Automatix and am trying to install some stuff, I'm getting roughly 40 kb/sec I normally get over 500k.

I cannot complain though, it's the best operating system I've ever used and it's free.

---

### Post by wombat20 on 2006-08-04
Wouldn't it be great if we could all share our upgrades around in a bittorrenty kind of way, with only the checksums coming from the main servers?

Surely this sort of thing is the future and definately in line with the ubuntu philosophy.

---

### Post by mlind on 2006-08-04
You can always switch to alternative [mirror]("https://wiki.ubuntu.com/Archive"). Just replace *http://archive.ubuntu.com/ubuntu* url with one of the mirror url's.

---

