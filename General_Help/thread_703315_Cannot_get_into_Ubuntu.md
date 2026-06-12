---
title: "Cannot get into Ubuntu"
date: 2008-02-21
forum: General Help
---

### Post by ilych on 2008-02-21
I finished the Wubi installation and was hoping to get into Ubuntu after another restart, but after I see the Ubuntu splash screen loading, I get all these command lines printed out:

> File system check failed
A log is being saved /var/log/fsck/checkfs if that location is writable.
Please repair the file system manually.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and resume system boot.
bash: no job control in this shell
...etc...
The program 'apt-get' is currently not installed. You can install it by typing: apt-get install apt

I tried typing apt-get-install apt but it returned "command not found". In any case, it seems like I need to do something about the file system?

Thanks for any help. I really appreciate it. I'm trying out Linux for the first time!

EDIT: I pressed ctrl+alt+delete, and I somehow into Ubuntu's GNOME desktop. So do I ignore the above messages? After I logged in, a balloon message still told me that I am using a restricted driver...that cannot easily be changed to fix any future problems. What do I need to do? Would using LPVM fix this problem? Thanks.

---

### Post by ago on 2008-02-21
What version of wubi was that? With what ISO?

1) Uninstall Wubi without backing up downloaded files (and remove any ubuntu ISO you may have)
2) Runc chkdsk /f within windows
3) grab Wubi 8.04 rev 431
4) Let it download the ISO and finish the installation

---

### Post by ilych on 2008-02-21
I used *Wubi-7.04.04* and *ubuntu-7.04-alternate-i386.iso*.

1) Done
2) Done
3) Is the following still true? "(rev411+ do NOT work at the moment, use 410)"
4)

Thanks for your help!

---

### Post by ago on 2008-02-21
> **ilych said:**
> Wubi-7.04.04
ubuntu-7.04-alternate-i386.iso

1) Done
2) How do I run chkdsk /f?

Open a dos terminal, change directory to the drive where you want to install wubi, run

chckdsk /f

> 3) Is the following still true? "(rev411+ do NOT work at the moment, use 410)"

The new ISOs are fixed now, but apparently (as of this morning) there are other issues with the new builds (independent of wubi). Those should be fixed in Alpha5 (due today). So best bet is to wait for alpha 5 and then try wubi rev 431 (which should also be on the CD by the way).

---

