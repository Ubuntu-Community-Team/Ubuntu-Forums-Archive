---
title: "sudoers kicked me out"
date: 2016-09-02
forum: General Help
---

### Post by holiday2 on 2016-09-02
16.04 running in virtual box on windows 7 host.

This has happened twice. Each time it is after spending a couple hours installing what I need for work. 
I enter my sudo password and receive 
<user> is not in the sudoers file. 

I don't see anyway around it. I'll have to install again? Won't be Ubuntu. 

I have tried booting from the iso hoping to edit the sudoers but of course that does not access the VM

I'm screwed right?

---

### Post by &amp;KyT$0P# on 2016-09-02
> **holiday2 said:**
> This has happened twice. 
How did you fix it the first time?

> Each time it is after spending a couple hours installing what I need for work.
What are you installing?  Where are you getting this software, how are you installing it?

Is it a specific software that triggers this?  Install the softwares one by one, log out and log back in after each installation and check if you have sudo rights.  That should point to the exact software(s) that's causing the problem.

> I'll have to install again?
Did you make a snapshot of the VM?  Doing so will make the VM environment somewhat disposable as all you have to do to "fix" anything, is shut down the VM and then restore the snapshot.
So I recommend you get the VM in a "known-good" state, then shut it down and make a snapshot, before trying this again.

> I have tried booting from the iso hoping to edit the sudoers but of course that does not access the VM
The words "of course" makes no sense in that context.  If you boot the VM from the ISO then you can mount the VM's hard disk in the live environment.
In terms of accessing it and such, you might have to use sudo more because the live environment uid doesn't match the uid of your user account on your installed system, but it should still work.

Can you please be more specific about what you can't seem to access?

---

### Post by steeldriver on 2016-09-02
A reinstall should NOT be required

You should be able to reboot the VM into Recovery Mode from the grub bootloader, drop to a root shell, remount the filesystem in read-write mode, then re-add yourself to the sudo group

```

mount -o remount,rw /

gpasswd --add *username* sudo

```

If you don't have root access in Recovery Mode (for example, if you have enabled root login, then forgotten its password) then there are alternate methods involving a live ISO

---

