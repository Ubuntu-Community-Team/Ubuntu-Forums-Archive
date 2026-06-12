---
title: "I want to make a DVD that will play in a standalone player, using the following files"
date: 2008-03-28
forum: General Help
---

### Post by jonathan@orion on 2008-03-28
```
jonathan@sirius:~/Desktop/TV/House/Season 2/House - Season 2 [DVD 2]/VIDEO_TS$ ls
VIDEO_TS.BUP  VTS_02_0.IFO  VTS_04_0.BUP  VTS_05_1.VOB  VTS_07_0.VOB
VIDEO_TS.IFO  VTS_02_0.VOB  VTS_04_0.IFO  VTS_06_0.BUP  VTS_07_1.VOB
VTS_01_0.BUP  VTS_02_1.VOB  VTS_04_0.VOB  VTS_06_0.IFO  VTS_08_0.BUP
VTS_01_0.IFO  VTS_03_0.BUP  VTS_04_1.VOB  VTS_06_0.VOB  VTS_08_0.IFO
VTS_01_0.VOB  VTS_03_0.IFO  VTS_05_0.BUP  VTS_06_1.VOB  VTS_08_0.VOB
VTS_01_1.VOB  VTS_03_0.VOB  VTS_05_0.IFO  VTS_07_0.BUP  VTS_08_1.VOB
VTS_02_0.BUP  VTS_03_1.VOB  VTS_05_0.VOB  VTS_07_0.IFO
```

How would I go about doing that? I know the files are fine themselves, but I attempted to do so with K3b and failed rather abysmally. :(

Edit: Also, if it will help, I believe the problem to lie with K3b, because I have a perfectly good .iso I tried to burn that resulted in the same error.

---

### Post by jonathan@orion on 2008-03-28
I tried my sister's portable DVD player that claims to be region 1, and the first DVD I burned worked perfectly. I suppose it had to do with the player, rather than the burner. Still, I wonder if there is a way that could be avoided outright, allowed the burned disc to work on any player rather than just this particular one.

---

### Post by danwood76 on 2008-03-28
If you burn the disk yourself it shouldnt be region coded.
It might just be that your DVD player doesnt read DVD-Rs too well.

What DVD media are you using?
DVD-R's as opposed to +Rs tend to be more compatible with DVD players I have found, but also cheap media also plays a huge part.

---

### Post by jonathan@orion on 2008-03-28
I'm using Memorex DVD-R's, and I don't expect that they're the issue. I've tried several other DVD players now, and the only one that works is otherwise the worst out of the lot.

---

### Post by danwood76 on 2008-03-28
When you put the DVD in your ubuntu machine you should see the same directory structure as in your file above.
So on the DVD will be a directory called VIDEO_TS with all the VOB and IFO files in.

I have created many DVDs in linux, although all home authored ones, and I normally just create the directory structure manually with all my vobs and ifos in and burn it to the disk and it works.
Are you running GNOME or KDE?
If your running gnome you could try using Brasero, this is my prefered CD/DVD burning package and I have created DVDs using it aswell.

---

