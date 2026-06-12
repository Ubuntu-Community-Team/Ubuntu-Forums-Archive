---
title: "Asks me for root password when I boot the computer"
date: 2008-03-05
forum: General Help
---

### Post by Fixman on 2008-03-05
When I start the computer, the "ubuntu gauge" goes until half, and then a console appears, tells me something about fsck and asks me for root password, of ctrl-D to continue. If I press ctrl-D nothing happens (resumes booting normally), but if I put my root password then it opens a shell, and when I exit it resumes boot.

Any suggestions?

---

### Post by pointone on 2008-03-05
It's asking you to run fsck manually because it's encountered an error it cannot repair automatically. Run "fsck /dev/*d*#", where /dev/*d*# is the drive the automatic fsck failed at, such as /dev/sda1, /dev/hdb5, etc.

---

### Post by maxmanders on 2008-03-05
I suppose that depends on what it tells you about fsck.  My guess is that fsck or another process has detected an error with your hard disk and it is giving you the opportunity to run a file system check.  Perhaps next time this happens you could log in as root (this will put you in single-user mode I believe), and the run fsck and see what happens.

---

### Post by taurus on 2008-03-05
When you are in that shell, you should fsck your / because that it why it drops you into the shell.

```
fsck -y /dev/sda1
```
_Assuming_ /dev/sda1 is your / partition.

---

### Post by Fixman on 2008-03-08
> **taurus said:**
> When you are in that shell, you should fsck your / because that it why it drops you into the shell.

```
fsck -y /dev/sda1
```
_Assuming_ /dev/sda1 is your / partition.

```
WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.
```

Are you sure of that?

---

### Post by taurus on 2008-03-08
Do not run fsck with a mounted partition.  If you need to run it, run it from the LiveCD.

---

### Post by Fixman on 2008-03-10
> **taurus said:**
> Do not run fsck with a mounted partition.  If you need to run it, run it from the LiveCD.

I ran it from the Live CD, and told me the disk was OK, but nothing happenned (it still asks me for root password).

---

