---
title: "Root filesystem read only!!! HELP"
date: 2005-09-19
forum: General Help
---

### Post by Cud on 2005-09-19
Hi folks... I hope this is the right category, there wasn`t one for "Total Dork Manuvers"
I cant boot linux cause I get a message that dev/hda is mounted read only and then that I should remount it read/write which would be great except that the I thought SU password and root password were the same thing but when I type in my SU password it says LOGIN INCORRECT and then I am left with the only option of rebooting with ctrl-D. I got my self into this mess when I was trying to improve hdrive performance and I
1 Changed the dma mode from udma3 to udma9
2-set 32-bit IO_SUPPORT (# hdparm -c1 /dev/hda)
3-unmasked irc support (# hdparm -u1 /dev/hda)
4- Set multsect to max of 16

So I was in way over my head and then .. mozilla started acting wierd.
I rebooted thinking that all the hdparm changes wouldn`t take effect.
Grub is OK.
Is there anyway out of this mess or should I chalk it up to character building?
Thanks, Jess

---

### Post by Xian on 2005-09-19
[QUOTE=Cud]I thought SU password and root password were the same thing but when I type in my SU password it says LOGIN INCORRECT and then I am left with the only option of rebooting with ctrl-D.[/QUOTE]
You can always set or re-set your root (UNIX) password with the passwd command. Now if you are having a problem with your sudo pass then another fix would be required.

```
$ sudo passwd root
Password:
Enter new UNIX password:
Retype new UNIX password:
passwd: password updated successfully
```

---

### Post by Cud on 2005-09-19
Thanks for the Answer. Unfortunatly my description of the problem maybe wasnt so great. I´ll try again. When I boot I get grub, select Ubuntu and then Everything proceeds as normal until I get:

Checking root file system
/dev/hda2 contains a file system with errors, check forced...
(Then at around 3% of the check I get:)

/dev/hda2: Unexpected inconsistency, run fsck maually
 (i.e. without -a or -p options)

*fsck failed please repai maually & reboot. Please note that the root filesystem *is currently mounted read only. To remount it read-write:
* #mount -n -o remount rw /

*Control-D will exit from this Shell and REBOOT the system

Give root password for maintenance (or type Ctrl-D to Continue):

When I type my Sudo passwrd here it says

Login incorrect

I am not getting the cute $ sign (or anyother) to be able to execute any commands. 

So I hope that makes my problem a little clearer. Also I have my windows remnants in the first partition.
Thanks in advance... User forums rule,.
Jess

---

### Post by Xian on 2005-09-19
Option 1: Try to use your sudo passwd to reset a root passwd as described, login for a maintenance session, mount the partition as rw and then run fsck as required.

Option 2: At the grub menu edit the kernel line for /hda2 using the 'e' key on your board, then remove (as I'm assuming it is there) the 'ro' notation which is making that space read only.

---

### Post by Cud on 2005-09-19
Thanks for being patient w/me Xian..

> Option 1: Try to use your sudo passwd to reset a root passwd as described, login for a maintenance session, mount the partition as rw and then run fsck as required.

-I tried this, but every time I give my sudo passwd I get 
Login incorrect
Give root password for maintenance (or type Ctrl-D to Continue):

> Option 2: At the grub menu edit the kernel line for /hda2 using the 'e' key on your board, then remove (as I'm assuming it is there) the 'ro' notation which is making that space read only.

Okay I got to grub where I can select an OS, and pressed esc and then the -e- button, but nothing happened. Then I noticed with a sinking sensation the text at the bottom saying I should press P for further options. Did it, and I got another demand for a Password. My sudo passwd didn`t function here either.
I think that might be cause I was trying to be a smart alec security nerd and I disabled grub menu options.
The one thing I could think of was putting the Ubuntu boot CD in and booting in rescue mode. I got to the point where I was in a shell. and my root directory should be the "target directory" but when I ls this directory nothing looked familiar. I tried remounting as RW using the commands that the boot-up shell suggested, but when I rebooted normally, I got the same string of error messages.
So......
Any hope? :wink:

---

### Post by Xian on 2005-09-19
You could use a [RecoveryCD](http://www.tux.org/pub/people/kent-robotti/looplinux/rip/) or similar and mount hda2 as rw.
Then perform the fsck check in that environment.

---

