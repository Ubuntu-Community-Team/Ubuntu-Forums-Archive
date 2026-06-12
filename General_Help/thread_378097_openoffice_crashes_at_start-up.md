---
title: "openoffice crashes at start-up"
date: 2007-03-06
forum: General Help
---

### Post by auditory on 2007-03-06
i am using ubunt 6.10
$ uname -a
Linux ubuntu 2.6.17-11-generic #2 SMP Thu Feb 1 19:52:28 UTC 2007 i686 GNU/Linux

and have openoffce install as default
$ ooffice --version
This is OpenOffice.org built with ooo-build-2.0.4

but when i try to launch openoffice (writer, spreadsheet and everything),
it crashes shortly just to show short splash at the beginning.

when launched on terminal with command, it gives following error message.
$ ooffice 
terminate called after throwing an instance of 'std::length_error'
  what():  basic_string::_S_create

** (process:12257): WARNING **: Unknown error forking main binary / abnormal early exit ...

what's the problem? and what should i do?

I have tried to reinstall ooffice packages by reinstalling
all packages which contain 'openoffice' in its name on synaptic pkg manager.
but the problem is not resolved at all.

---

### Post by Hagar Delest on 2007-03-08
Try to delete the OOo user profile ~/.openoffice.org2, OOo will create a new one.

---

### Post by thathatman on 2007-03-08
Moving my .openoffice.org2 folder did not solve the problem for me.
> 
** (process:16317): WARNING **: Unknown error forking main binary / abnormal early exit... 

It was working fine two days ago, now it fails to start... any help would be greatly appreciated.

---

### Post by Ek0nomik on 2007-03-08
[http://ubuntuforums.org/showthread.php?t=293081](http://ubuntuforums.org/showthread.php?t=293081)

I hope that helps!

---

### Post by aldeby on 2007-05-28
If you installed SCIM imput for non latin languages this fix done the job for me: 
> [http://ubuntuforums.org/showpost.php?p=2568329](http://ubuntuforums.org/showpost.php?p=2568329)
Hope it helps. It has been a very annoying bug.

---

