---
title: "accidently chmod 777 on root with -R"
date: 2018-03-03
forum: General Help
---

### Post by koene2 on 2018-03-03
HI all,

I accidently did a chmod on / with recursive flag. I stopped it after a second but seems like I did some damage.
I can no longer sudo:
```
sudo -i
sudo: error in /etc/sudo.conf, line 0 while loading plugin `sudoers_policy'
sudo: /usr/lib/sudo/sudoers.so must be only be writable by owner
sudo: fatal error, unable to load plugins

```
So I'm trying to fix these permissions, but I have to be root for that...

I tried booting in root shell te become root in order to change back the permissions but I can't access the recovery mode screen (I wiped off windows so there is no grub loader installed).
So this won't work.. [https://askubuntu.com/questions/92556/how-do-i-boot-into-a-root-shell](https://askubuntu.com/questions/92556/how-do-i-boot-into-a-root-shell)

Is there another way to gain root access?

---

### Post by deadflowr on 2018-03-03
It'a a pain to fix even with recovery.
Since many different permissions apply to many different parts.
it is unclear how far along it got, so it would be unclear which files need to be reset.
And you would also need to know what those files permission setting should be.
Very daunting in my opinion.
Reinstall is easier.

But for the sake of methods of recovery.
There are 2 methods to access the grub menu.

1) you tried, and that is the shift key.
this method applies to legacy BIOS systems.

2) Use the ESC key instead of the shift key.
This applies to newer UEFI systems.

If both fail,
another recovery method is a chroot from a live cd (dvd/usb)
[https://help.ubuntu.com/community/LiveCdRecovery]("https://help.ubuntu.com/community/LiveCdRecovery")


But I stand by my original assessment of a reinstall.

---

### Post by #&amp;thj^% on 2018-03-03
> **koene2 said:**
> HI all,

I accidently did a chmod on / with recursive flag. I stopped it after a second but seems like I did some damage.
I can no longer sudo:
```
sudo -i
sudo: error in /etc/sudo.conf, line 0 while loading plugin `sudoers_policy'
sudo: /usr/lib/sudo/sudoers.so must be only be writable by owner
sudo: fatal error, unable to load plugins

```
So I'm trying to fix these permissions, but I have to be root for that...

I tried booting in root shell te become root in order to change back the permissions but I can't access the recovery mode screen (I wiped off windows so there is no grub loader installed).
So this won't work.. [https://askubuntu.com/questions/92556/how-do-i-boot-into-a-root-shell](https://askubuntu.com/questions/92556/how-do-i-boot-into-a-root-shell)

Is there another way to gain root access?
Unfortunately there is no quick way to restore filesystem permissions on Ubuntu if this occurs. 
and to my knowledge there is no good answer to an out-of-control chown/chmod, other than to restore from backup or rebuild. 
Sorry I don't mean to sound harsh just the facts. :(
Dang I must be super slow today Ninjed by deadflowr :D

---

### Post by QIII on 2018-03-03
Hello!

To answer the question you are certainly asking yourself:  "Isn't there an easy way to do this?  Maybe just chmod them all to xyz?"

Unfortunately, no.

There are literally thousands of files, each of which has to to have a particular permissions setting for your system to work properly.  Although many do, they are not necessarily supposed to all have xyz permissions.  To fix this (a recursive chmod is going to happen very, very quickly, so "a second" to stop the process may be too late) would require that for each of those thousands of files you know the specific permissions each file should have.  That's probably an impossible task for any single developer at Canonical, even.

Probably your only recourse is to have your data backups handy and reinstall.  If you do not do regular backups (and this is exactly the sort of occasion that reinforces the idea that you should), then you may be able to use a Live session to transfer your important files to external media and reinstall.  You may be able to take a chance and reinstall while leaving your /home undisturbed when you re-partition, but that is no guarantee.

We have all don't things like this.  Anyone who says they haven't is lying.  :)

I'm sorry none of us has any better news for you.

---

