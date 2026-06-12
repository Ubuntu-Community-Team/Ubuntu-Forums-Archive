---
title: "HUGE Problem; Can't start Ubuntu; can't even chroot!!"
date: 2008-03-13
forum: General Help
---

### Post by aephoenix on 2008-03-13
I have no idea what happened, but last night at about 11:50 my entire system stopped working.

It started with not being able to restart firefox without getting a segfault. Then I couldn't start gedit because of a segfault. Or.. anything else.

So I rebooted, ...but no application could start. The little usplash text was mostly "OK" but the NFS utilities failed.. if that's a sign of something.

I've tried recovery mode. I've tried every kernel I have.

Fortunately I still have a backup of my old system, but it's really old..

I **can't even chroot into my system.**

It gives me this error:
```
root@ubuntu:/bin# chroot /media/sda8 /bin/bash

malloc: unknown:0: assertion botched
free: called with unallocated block argument
last command: rm hchapman_blech/ -r
Aborting...Aborted (core dumped)

```
(hchapman_blech is some folder I removed like two days ago)

If it makes a difference, I am using the hardy alpha. Should I have posted this in the dev forum instead?

Either way, if anyone has had any prior experience with this kind of issue, please help. I really don't want to reinstall.

Thank you.

EDIT:
Apparently this is a known issue with hardy after the last libc6 upgrade.
I'm a forum nubcake, is there a way to delete this?

---

### Post by Oldsoldier2003 on 2008-03-13
> **aephoenix said:**
> I have no idea what happened, but last night at about 11:50 my entire system stopped working.

It started with not being able to restart firefox without getting a segfault. Then I couldn't start gedit because of a segfault. Or.. anything else.

So I rebooted, ...but no application could start. The little usplash text was mostly "OK" but the NFS utilities failed.. if that's a sign of something.

I've tried recovery mode. I've tried every kernel I have.

Fortunately I still have a backup of my old system, but it's really old..

I **can't even chroot into my system.**

It gives me this error:
```
root@ubuntu:/bin# chroot /media/sda8 /bin/bash

malloc: unknown:0: assertion botched
free: called with unallocated block argument
last command: rm hchapman_blech/ -r
Aborting...Aborted (core dumped)

```
(hchapman_blech is some folder I removed like two days ago)

If it makes a difference, I am using the hardy alpha. Should I have posted this in the dev forum instead?

Either way, if anyone has had any prior experience with this kind of issue, please help. I really don't want to reinstall.

Thank you.

EDIT:
Apparently this is a known issue with hardy after the last libc6 upgrade.
I'm a forum nubcake, is there a way to delete this?

check the thread in the Hardy Alpha forum... oh the joys of playing with an Alpha OS  :)

---

