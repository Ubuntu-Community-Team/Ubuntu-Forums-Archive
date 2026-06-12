---
title: "Ubuntu Feisty booting in read-only filesystem"
date: 2007-06-18
forum: General Help
---

### Post by k31k0 on 2007-06-18
Hi.

I have Ubuntu Feisty installed on my HP nx7400 laptop. Everything was working perfectly but since 3 or 4 days it started booting in read-only state without X (it says something about X server encounter some kind of error). After couple of restarts it boots normally, but I'm concerned about my data. Are those signs of faulty hard disk (I bought laptop 10 months ago) or is it a software error?
My guess is that it's a software error because after couple of restarts it boots normally.

Please help...

Regards, Sasha.

---

### Post by ukripper on 2007-06-18
I don't think it is a hardware error. You probably need to reconfigure your xserver. try following when your system boots up and then select terminal console:

```
sudo dpkg -reconfigure xserver-xorg
```

and follow the steps.

---

### Post by k31k0 on 2007-06-18
Thnx for advice, but I don't think it's an X server error. I think X is not started because of read-only mode that file system is mounted in.
However, I will try your advice when I'm at home.

If anyone else has any idea - you are welcome to reply :)

---

### Post by christhemonkey on 2007-06-18
I had this happen to me yesterday,

i ran an "fsck -f /dev/hda2" (my / partition) and it encountered a lot of errors so i fixed them all an now im a happy bunny!

---

### Post by k31k0 on 2007-06-18
I did that yesterday. It found a lot of errors but they were all fixed. I thought today everything will be OK, but it's the same :(

---

### Post by ukripper on 2007-06-18
Probably this could help :

[http://ubuntuforums.org/showthread.php?t=180779](http://ubuntuforums.org/showthread.php?t=180779)


Check it out

EDIT:

I would highly recommend you to backup your existing data before trying anything in filesystem.

---

### Post by christhemonkey on 2007-06-18
Also could you boot up in recovery mode and tell us exactly where it gets to when it fails and what it prints to screen.

---

