---
title: "Help!  Too many GRUB's"
date: 2008-02-17
forum: General Help
---

### Post by Vcount on 2008-02-17
Hi, I've been running Edgy 6.10 for a while, and I broke down my computer to component parts for a move.  When I got a new computer case on the other end of the move, I could only fit two out of my three internal hard drives in the case, and so left one of them out.  

However, now I've modified the case so I can have my third hard drive back, and have put it back in, but now my GRUB is all messed up.  

The hard drives are a 300gb one, a 250gb one, and a 200gb one.  The one I just put back in, and that messed up GRUB, is the 300GB one.  It has a Feisty installation on it.  The 200GB one is an IDE drive, and it has an old windows installation, an older Dapper installation, and is the boot master.  The 250GB one was my main drive that has all the data I care most about, and is the Edgy installation. 

What I want to do is boot into my Edgy kernel, 2.6.17-11-generic.  However, whenever GRUB comes up, it either comes up with only the very oldest Dapper kernels available and no later kernels than 2.6.15, or it will come up with all of the kernels, but when I go to the one I want (2.6.17-11-generic), it actually goes into the Feisty installation instead.  

Using Super Grub disk, I can boot directly into the kernel I want, my Edgy installation on (hd1,0).  I can even edit my menu.lst just fine from there, and to make sure I was actually making changes, I successfully added a splash screen to my GRUB menu.  

But whenever I decide not to boot directly using Super Grub disk, GRUB will just go back to either showing only the old Dapper kernels, or showing a list with the kernel I want but redirecting me to my Feisty installation instead.  It does have the splash screen during both of these instances I put in by editing my menu.lst file in my Edgy installation, so I know I can theoretically make changes successfully.  

Just going from the GRUB command line, I can root it in the hard drive I want (hd1,0), and I can point it to the kernel I want booted (/boot/vmlinuz-2.6.17-11-generic), but then whenever I tell it to boot after doing these things, it gives me a kernel panic.  

Does anyone have any ideas what I can do to fix my GRUB? 

I think my problem is I have too many GRUB's, and the computer is having a hard time figuring out what is pointing where.  Is there any way I can nuke every single GRUB instance on all the disks and start with a fresh one?  How would I build a fresh GRUB?  

Thanks!

---

### Post by jonny5tails on 2008-02-17
[FONT=Comic Sans MS]Hi [/FONT][Vcount]("http://ubuntuforums.org/member.php?u=127466"),
Here's a stupid question - Did you replace your hard drives in the exact order that you removed them? :confused:

---

### Post by Herman on 2008-02-17
> I think my problem is I have too many GRUB's, and the computer is having a hard time figuring out what is pointing where. Is there any way I can nuke every single GRUB instance on all the disks and start with a fresh one?:)  Nah!, you don't have very many GRUBs yet, look at this guy saikee in the JustLinux forums, he has 100 or 145 GRUBS and they all work fine together, [A grub menu booting 100+ systems of Dos, Windows, Linux, BSD and Solaris]("http://www.justlinux.com/forum/showthread.php?t=143973"), and [U][How to install and boot 145 operating systems in a PC]("http://www.justlinux.com/forum/showthread.php?t=147959").

[/U]All you need to do is *organize* your GRUBs.

Why don't you make one operating system in each hard disk be the main operating system for that hard disk. Then regardless of whether you have just one or many operating systems in that hard disk, have an entry for each one in your main operating system and have that operating system's GRUB installed to that hard disk's MBR.

Naturally, whichever operating system's GRUB is the first hard disk will be the Grand Master GRUB for that computer.
In the Grand Master GRUB, you make chainloader entries for booting the MBR of each of the other hard disks.

Chainloader entries for booting a second and a third hard disk would look like this,
```
  title        Chainload Second Hard Disk's MBR
root        (hd1)
chainloader    +1

 title        Chainload Third Hard Disk's MBR
 root        (hd2)
chainloader    +1

```Then try to boot each operating system and just fix any that won't boot by editing it's /boot/grub/menu.lst file.

Regards, Herman :)

EDIT: Before you do what I said, jonny5tails is probably right, so try  unplugging your 250GB and your 300GB hard drives from the motherboard if you can reach in there easily, and swap the cables around and plug them back into the opposite SATA ports. If you don't want to do it that way, just [ change the hard Disk Boot Priority]("http://www.users.bigpond.net.au/hermanzone/p1.htm#Changing_the_hard_Disk_Boot_Priority") in your BIOS.
See if that fixes it, probably that will fix it.

---

