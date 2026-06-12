---
title: "Read only file system error!"
date: 2007-05-14
forum: General Help
---

### Post by xardas on 2007-05-14
I've been using Ubuntu 6.06 dual booting with Windows XP for some months now. And this kind of error has not popped up until now. All the files on the linux drive have become read only for some reason and whenever I try to change any it gives an error 'read only filesystem'. The same error is popped up when I log in and it tries to change some configuration files in my home directory. After a while the system hangs and I have to restart. Any idea whats going on?

---

### Post by songamericadj on 2007-05-14
Did you, at any point, try to access Ubuntu from Windows, on purpose or accidentally?

---

### Post by xardas on 2007-05-14
Yeah I've been doing that for quite some time now without any problem. I think I used a utility for that which showed my linux partition as a normal partition to me in windows. I regulary write files on the linux partition from windows. It hasn't happened before. What should I do now?

---

### Post by xardas on 2007-05-14
Sooo anyone?

---

### Post by xardas on 2007-05-15
No one's got anything to say?

---

### Post by xardas on 2007-05-16
No one at all?

---

### Post by xardas on 2007-05-18
I think the reason may be some error in the filesystem. Can anyone tell me how to repair that?

---

### Post by Absorbed on 2007-11-16
I had a similar problem. After installing XP on my computer, my ubuntu partition became read-only. I fixed it using fsck.

```
sudo fsck -a /dev/hda2
```

/dev/hda2 is my linux partition. You can find yours by doing the following:

```
sudo fdisk -l
```

---

### Post by zaphod777 on 2007-11-16
did you modify /save files as root?

---

### Post by chrisccoulson on 2007-11-16
> **Absorbed said:**
> I had a similar problem. After installing XP on my computer, my ubuntu partition became read-only. I fixed it using fsck.

```
sudo fsck -a /dev/hda2
```

/dev/hda2 is my linux partition. You can find yours by doing the following:

```
sudo fdisk -l
```

I have to stress - **do not do this on a mounted partition. Unmount first!!** If the partition cannot be unmounted (such as, if it is the root filesystem, then you can force a filesystem check at the next boot by creating a file 'forcefsck' at the root of the partition. So, if you want to check your root partition:
```
sudo touch /forcefsck
```

Then reboot. Alternatively, you could run fsck from the live CD.

A read only filesystem could be caused by a filesystem error, or disk failure. A normally read-write file system may be re-mounted read-only after an error has occurred to prevent the filesystem becoming completely hosed. This is something that happens automatically.

---

