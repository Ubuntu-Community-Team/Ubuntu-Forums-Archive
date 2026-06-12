---
title: "Can't run VMWare Player as user, only root"
date: 2007-05-03
forum: General Help
---

### Post by 50words on 2007-05-03
I know I saw this somewhere before, but I can't run VMWare Player unless I run it using "sudo vmware player".

I used this guide: [http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html](http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html)

Any ideas how I can run it without "sudo"?

---

### Post by scxtt on 2007-05-03
who owns (and what are the permissions?) the vmware player executable or the VMs (.vmx files) themselves?

---

### Post by 50words on 2007-05-03
I own them (vmdk and vmx) and have read/write permission on both. "Group" and "Others" have read-only permission.

---

### Post by 50words on 2007-05-03
Bigger problem now. I had a couple of failed VMPlayer sessions, and now when I boot, I get no GUI. The two problems must be related, but what can I do? I can't see anything on the drive now in Windows, either. Am I screwed? Not sure I want to start over with Ubuntu again.

---

### Post by Raptor45 on 2007-05-03
Sounds like someone got sudo-happy...

Chances are, you decided to start vmware with sudo at one point, and some config files got written as root... not allowing you to access them normally. Happened to me once by accident, vmware will probably complain about not being able to access file such-and-such, just chown them back to normal.

Starting random programs with sudo is not a fix-all solution.

---

### Post by scxtt on 2007-05-03
hard to say why you get no GUI when you boot, cause i'm not sure what you did to put you in that state ... do you know who owns the vmware-player executable? (might just be "vmware", do a **whereis** (vmware / vmware-player) to find the path, then an **ls -l** on that binary ...

---

### Post by 50words on 2007-05-03
I'm also read-only when I boot, unfortunately, so I can't seem to do anything. The filesystem apparently got mucked up, too.

---

