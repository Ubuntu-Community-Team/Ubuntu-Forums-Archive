---
title: "Boot problem --- &quot;/bin/sh: can't access tty; job control turned off&quot; \ (initramfs)"
date: 2007-06-16
forum: General Help
---

### Post by tefflox on 2007-06-16
I get this message now that I've installed a second hdd in my new xps 410 to load xp pro on the second drive.  it was all working fine until this morning when i accidentally shut down xp with a U3 flash drive plugged in.  I then booted up Ubuntu and it gives me this error

> Built-in shell (ash)
Enter 'help' for a list of built-in commands

/bin/sh: can't access tty; job control turned off
(initramfs)it gives this error for any of the grub boot options, including recovery mode.

plz help !

---

### Post by micmox on 2007-06-16
Hi !
Just thought I'd pass my experience on fixing a booting problem
with installing ubuntu, on a system that a neighbour of mine had
after building the tower and mobo himself.

Initially he couldn't get the ram system to even find the hard drive, so I "effwond" (f1) into a shell to looked at /etc/fstab. 

My! isn't ubuntu strange under the bonnet. 
The only things that fstab had listed were /proc and something else
I can't remember now but that's not important.

Looking at cdrom and media directories were also empty.
So now I am wandering around without a map.
"ls -al ing" here there and everywhere so I could orient myself with recognisable system stuff(a bit like looking for the ignition system in a car you've never driven that has broken down on the side of the road, it should be there somewhere).

I then came across init, and ls told me that it wasn't a directory.
so I executed it at the command prompt, "effsevened" (f7) back into the gui
and bingo! we could now do an install.

That done we went to boot into a system via the hard drive.

All went well until after a long wait at the first screen, the gui disappeared and a shell command prompt came up with the message "/bin/sh can't access tty". 
After googling for similar problems we saw a post that prompted my neighbour to mention the fact that he had changed the bios to boot from the cdrom 1st, hard drive 2nd and he'd  disabled the floppy drive as the system didn't have one on it(as you would).

He asked me if we booted with the floppy enabled would that help?

Being a bit doubtful, I said it wouldn't hurt to enable it but would doubt it would get the system up and running.

How wrong could I be!

TO SUM UP 
If you are doing a dual system install with windows XP and ubuntu 7.04, try nipping into the bios setup and enable the floppy to be seen.

I'm sorry to say that my neighbour wouldn't let me reproduce the fix  and I quote "now that the system is working". 

Can't say I argued the philanthropic point of view with him either.

A few other hiccups with unrecognised user and password errors were also encountered namely, the system changing the installed setup entries to *all* upper or lowercase instead of leaving them as typed.

Hope this helps.
micmox.

---

