---
title: "Sudo is disabled and portable drives won't umount/mount."
date: 2008-01-29
forum: General Help
---

### Post by myke on 2008-01-29
> fusermount: option blkdev is privileged
FUSE mount point creation failed
Unmounting /dev/sdb1 (WDpassport)

I started out trying to fix the above error.  I could right click on my portable ntfs formatted hard drive to unmount it under my own login but could only get it remounted by going to system settings:disk & filesystems and re-enabling it.   Yet, if I logged in as root under the GUI, I could do both with a click of the mouse which is much much simpler and even can be done under WinXP.   This shouldn't be blocked.   So, when I tried to fix the above error, not only did it not fix the problem but now I can't access any package that requires a sudo login under my id such as synaptic or adept.   When I launch such a program, the icons will spin and spin but never prompt me for my password or launch and then they eventually just quit.

So what might I have done to cause sudo to be inactive?  It may also be of note that though I can still mount and remount my drives logging in under the gui as root, I can't access anything requiring a second login such as synaptic or the advanced tabs under system settings so I've messed up some file with the administrative login settings but I don't know what it was.  

This was dumb, I admit but it wouldn't be so necessary some times to tinker if every other simple option was blocked unless logging in as root.  I'm terribly tempted after fixing this to turn my root gui login into my main login just to avoid constantly being denied doing simple things that even Windows allows.  This is a sucky part of linux for any mildly competent user.   

BTW ... I'm currently using the KDE gui.  If I switched over the gui to Gnome for a bit, will it make unmounting/remounting drives any simpler or is it just as big of a deal there?   Of course, in order to install Gnome I have to get Sudo working again because I can't access synaptic or adept!

HELP!!!!

---

### Post by codesplice on 2008-01-29
I have no trouble mounting drives in Gnome, and even automounted a WD Passport yesterday :)  Do you have ntfs-3g installed?  It seems to make dealing with NTFS partitions a lot easier.  

But I'm afraid I can't help on your sudo issue :(

---

### Post by myke on 2008-01-29
I do have ntfs-3g installed but it seems to be fighting with "fuse" to mount the drives.  They actually do auto mount fine but occasionally I may need to unmount the passport portable drive and then plug it back in later.  That's where the problem was coming in.  I'd have to go all the way thru system settings to remount unless I restarted the whole computer with the thing plugged in.  Otherwise, if the computer was still on it wouldn't automount and wouldn't let me mount it with a mouse click.  I had to open the system settings control panel and re-enable the drive.    Unmounting --- fine .... Remounting ... not fine.

Now anyone know how to get sudo working again?  And really it's not just sudo as programs needing sudo under my normal login won't launch either under root gui login.   For example, I can't launch synaptic or adept under my login using sudo and can't launch them under root gui login at all either.  The icons just spin and spin and then just quit.

I'd try Gnome out for a while alongside KDE but I can't because of the inability to access any install method ... including thru apt-get in terminal mode as this is not working either.

IDEAS?

---

