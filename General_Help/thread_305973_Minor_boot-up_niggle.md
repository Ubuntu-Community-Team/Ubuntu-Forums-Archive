---
title: "Minor boot-up niggle"
date: 2006-11-24
forum: General Help
---

### Post by John E on 2006-11-24
I already asked this question in the beginners forum but no-one seemed to have an answer...:(

PROBLEM: When I boot into Ubunto I see a progress list at the bottom of my screen which increments as different things get loaded and/or tested. Eventually, I see these 3 entries:-

[B]Setting up LVM Volume Groups                      [OK]
Setting up Enterprise Volume Management System    [OK]
Checking all File Systems[/B]

When the third line comes up, my display suddenly switches to an old fashioned, DOS-style window where it continues for the rest of the boot sequence. Is there a way to prevent this? It looks as though it might be supposed to happen if an error gets detected but no errors show up on the display.

I think it might be a timing thing because that particular stage (**Checking all File Systems**) seems to take a lot longer than the other stages. It doesn't happen if I boot up from the live CD.

---

### Post by jazzgossen on 2006-11-24
It is a timing thing. I think this behaviour is supposed to change in Feisty.

---

### Post by John E on 2006-11-24
Feisty..???

---

### Post by biodiesel-bri on 2006-11-24
Feisty Fawn is the next version of Ubuntu.  Current is Edgy Eft, previous was Dapper Drake, etc.  Actually the silly names are pre-release.  Once they are officially released they become year/month.  Thus Edgy became 6.10, Dapper 6.06.

---

### Post by dca on 2006-11-24
Are you running a dual-boot system w/ Windows XP???
 
Not that this helps but that was the only time I've seen that on a system...  However, it still worked/performed fine, it just switched to a loader like what you see when SuSE or other distros first start-up.  Simple ASCII text indicating what start-up step is loading.

---

### Post by John E on 2006-11-27
Yes, I'm dual booting (in fact, triple booting!) with Ubuntu, XP and Win2K.

Oddly enough, it doesn't happen when I boot from the live CD. Although in that case, the 3rd stage ("**checking all file systems**") is over in about 2 seconds!

I suspect that the checks don't really get done when booting the live CD.

Is it possible to set Ubuntu so that it doesn't check my Windows hard drives?

---

