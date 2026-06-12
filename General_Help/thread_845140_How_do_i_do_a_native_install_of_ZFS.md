---
title: "How do i do a native install of ZFS?"
date: 2008-06-30
forum: General Help
---

### Post by tobycatlin on 2008-06-30
Hello Everybody,

I have been reading about ZFS and it seems perfect for a file server. Great tutorial for ZFS on open solaris: [http://breden.org.uk/2008/03/02/a-home-fileserver-using-zfs/](http://breden.org.uk/2008/03/02/a-home-fileserver-using-zfs/)

I have seen the fuse-ZFS project but everyone seems to think this is pretty much a hack and say the performance is slow. Also it is unsafe to have a file system managed by software in user space. 

As i understand it ZFS can't be bundled with Ubuntu due to licensing restrictions which seems a real shame but thats the way of the world. I would like to run ZFS native. As i understand it i am allowed to do it from license point of view. Correct?

I am no linux guru but i do have some skills and have successfully followed tutorials to compile kernel modules for other reasons. You have probably guessed what i am leading up to. Does anyone know of a guide on how to natively compile/install ZFS within Ubuntu Hardy. 

I'd like to build a ubuntu based file server in the same way Simon did it in his blog and i'd be happy to write up my experience.

thanks

toby

---

### Post by danwood76 on 2008-06-30
You cant run ZFS in linux at the moment but I dont see there is any real advantage to it.
A lot of what was in that document looked like marketing hype, theres nothing wrong with any of the filesystems available in linux.
The data redundancy in ZFS looks a bit iffy at best, they make some quite crazy claims and why if you are looking for redundancy you dont use something thats tried and tested (for 30 years or so) compared to something newer?

I would choose to use XFS for a file server personally.
You wouldn't see any difference in speed when using XFS or ZFS or any FS anyway as there are much greater things that will slow you down like your CPU/RAM/Disk Limits/Bus Limits.

To avoid data loss with disks dying and for speed you should run a RAID5 setup with LVM, this will also allow you to increase disk size by adding more later.

---

### Post by tobycatlin on 2008-06-30
danwood76 thanks for your reply. 
I have looked at various comparison's between file systems and their various pros and con's. There are many many posts on this and I have seen other people put forward the same argument as yours, along the lines of: 'You can do the same thing with LVM/Raid5/etc/etc so why bother with ZFS'

Fact is i didn't ask what is the best FS/setup for data redundancy. I don't care what other options are available, I'd like to try ZFS for myself. I'd like to run it natively otherwise i don't see the point.

If it isn't possible as you say i would like to know why. Is it a technical reason why it can't be run or a licensing issue? I understand why Ubuntu can't make it part of it's official distro. 

Do licensing incompatibilities stop me taking the source and compiling it for my own machine for my own use?

If not does anyone know how i can install ZFS natively on hardy heron 

thanks
t

(I have just read this back and i hope it doesn't come across badly, it's not meant to be aggressive)

---

### Post by bluepowder7 on 2008-06-30
why not just install and run Solaris if you want ZFS natively?  seems to be the most logical and "rugged" approach...

---

### Post by tobycatlin on 2008-06-30
It's deffo an option to use Solaris and if it turns out there is no way to install ZFS in Ubuntu then thats probably what i'll do. 

I'd rather use Ubuntu if possible. I use Ubuntu to learn about linux and a project like this would teach me a lot. Getting my TV card working properly taught me loads and took weeks of work (as it turned out i had bought a slight variant of the nova-t 500 that was incompatible with current drivers).

I don't mind if  at the end of the day it isn't reliable enough to use, i'd like to give it a go

---

### Post by danwood76 on 2008-06-30
Well it looks like you can run ZFS through FUSE, the only issue is that it is running in user mode and so is not really good for a server which is supposed to be running fast and stable.
Solaris is deffo the best way to do it as its obviously native there.

But if you want to give it a go I found this site earlier:
[http://zfs-on-fuse.blogspot.com/](http://zfs-on-fuse.blogspot.com/)
It looks like fuse-zfs is buggy and no way near 'stable' but its a starting point for something to play with.

---

### Post by bluepowder7 on 2008-06-30
wasn't ZFS also ported to FreeBSD not long ago?  that might be a third option...

---

### Post by Taxman415a on 2008-06-30
> **tobycatlin said:**
> 
If it isn't possible as you say i would like to know why. Is it a technical reason why it can't be run or a licensing issue? I understand why Ubuntu can't make it part of it's official distro. 

Do licensing incompatibilities stop me taking the source and compiling it for my own machine for my own use?


As I understand it yes, it is a licensing incompatibility. See [http://en.wikipedia.org/wiki/ZFS](http://en.wikipedia.org/wiki/ZFS)
But I do believe that is just a problem with distributing the code, so distributions like Ubuntu, etc can't port ZFS to Linux but you could run it yourself as long as you don't distribute it. Check with your lawyer of course. ;)

But porting a filesystem to a new kernel is a nontrivial task. In fact it's a very difficult one. Feel free to dig in and have fun seeing if you can do it though. If your goal is to learn, you would certainly learn a lot.

---

### Post by Habbit on 2008-06-30
In fact, using a FUSE filesystem can be the best approach for a server, since a hypothetical FS driver panic would not panic the kernel. If the failed FS driver is no the root FS, the system can be recovered just by remounting the appropiate volumes.

Regarding FUSE performance, no one tries to hide that this approach "greatly" increases overhead due to the large number of context switches required for each filesystem operation, but for storage server it would be _very_ difficult for the system to become CPU-bound due to FUSE instead of IO-bound due to the disks.

An example of a stable and performing FUSE driver is NTFS-3G: try it and you'll be surprised.

---

### Post by kwagner on 2008-07-05
Read my posts, starting on this page: [http://ubuntuforums.org/showthread.php?t=823855&highlight=zfs&page=2](http://ubuntuforums.org/showthread.php?t=823855&highlight=zfs&page=2)

---

### Post by tobycatlin on 2008-07-06
kwagner, thanks i have already read that thread and have installed ZFS under fuse.
I don't see where in that thread it talks about installing ZFS natively. 

I know what ZFS Fuse is and i understand it's limitations. I specifically asked how to install it natively as it says in the title and first posts.

Can anyone tell me how to install ZFS without fuse? 
I realise it is a hard task and if it is too complicated to list a blow by blow tutorial, what are the high level steps?

thanks

toby

---

### Post by kwagner on 2008-07-06
Hi Toby,

Are you sure you want to run ZFS without fuse?
I ask you, because in my opinion, running it under FUSE has several advantages that are not available when running in kernel mode.
For example, on FreeBSD, if you have a USB device running ZFS, and you pull it or abruptly eject it, if will cause a kernel panic, and the whole OS goes down.
The same applies to MacOS ZFS implementation, and on OpenSolaris, it leaves your system on a semi 'Limbo' state, which  eventually need a reboot!
As for performance, I am very pleased with my Ubuntu 8.04.1 and zfs-fuse right now. And I'm sure it's a matter of time (tunning) before it will be even  faster, just as NTFS-3g is, which is extremely fast on Linux.
And I have tried crashing ZFS by doing exactly what I mentioned above, and the only thing that happens is that the "Fuse Blows" :D but not the kernel, and I just re-run zfs-fuse again, and my /home directory appears as if nothing had ever happened. So I'm all for zfs on userland.

However, if you still want to try zfs in kernel mode, I haven't tried that yet, buy I would assume you need a /boot partition which will be ext3 to have your kernel boon normally and then load a zfs module, or compile zfs in-kernel, and I don't know if that's been done right now.
And this will probably never be available this way in any distro, due to the license conflict between ZFS license and GPL license.
Unless someone does it as a "User Compile" option, similar to how Codecs are installed *After* installation.
But then, if you think about it, how would ZFS be installed on a root filesystem after an instalation LOL :D 
One option I see is to have sort of a network bootstrap right after the CD is booted, and pull a ZFS kernel from some "Medibuntu" type of repository, and then continue the installation.
I'm sure this is probably the way ZFS  is going to be installed on Linux systems. Guerrilla style, that is! :lolflag:

Cheers!



> **tobycatlin said:**
> kwagner, thanks i have already read that thread and have installed ZFS under fuse.
I don't see where in that thread it talks about installing ZFS natively. 

I know what ZFS Fuse is and i understand it's limitations. I specifically asked how to install it natively as it says in the title and first posts.

Can anyone tell me how to install ZFS without fuse? 
I realise it is a hard task and if it is too complicated to list a blow by blow tutorial, what are the high level steps?

thanks

toby

---

### Post by Taxman415a on 2008-07-08
> **tobycatlin said:**
> I know what ZFS Fuse is and i understand it's limitations. I specifically asked how to install it natively as it says in the title and first posts.

Can anyone tell me how to install ZFS without fuse? 
I realise it is a hard task and if it is too complicated to list a blow by blow tutorial, what are the high level steps?

Toby, I basically told you the high level step. It's far too complicated a task to give you a detailed step by step, so if you want to learn how to do this you need to do some searching and reading. You don't just install something like this, you port it, or change the code to make it interact appropriately with the new system. Googling for porting filesystems gave these two links which would be very instructive if you'd like to try to learn how to do this. You're probably going to want a linux kernel internals book as well.

Porting ZFS file system to FreeBSD [http://2007.asiabsdcon.org/papers/P16-slides.pdf](http://2007.asiabsdcon.org/papers/P16-slides.pdf)

Porting the SGI XFS File System to Linux [http://oss.sgi.com/projects/xfs/papers/als/als.pdf](http://oss.sgi.com/projects/xfs/papers/als/als.pdf)

The first link gives the basic idea of what to do on the ZFS side, the second the basic idea on the Linux side, though old. Basically you're going to create a ZFS kernel module and enough of a compatibility layer for it to talk to the linux vfs or virtual filesystem layer. But again, those papers would be very illustrative.

---

### Post by tobycatlin on 2008-07-09
Thanks for your reply, 
right i am getting what you meant in your previous post, 'a nontrivial task'

I didn't realise a whole new kernel module was required. I thought one already existed and was being used by the fuse project. It was only license restrictions preventing it from being loaded directly into the kernel. 

it seems i have the wrong end of the stick

---

### Post by Taxman415a on 2008-07-09
> **tobycatlin said:**
> Thanks for your reply, 
right i am getting what you meant in your previous post, 'a nontrivial task'

I didn't realise a whole new kernel module was required. I thought one already existed and was being used by the fuse project. It was only license restrictions preventing it from being loaded directly into the kernel.

Unfortunately, nope, the way it works is FUSE is the kernel module and then the ported filesystem, ZFS in this case, talks to that from userspace. So ZFS is only ported to FUSE, not to the Linux kernel. No one is doing the work of porting it to the linux kernel (as far as I know) because of the licensing.

I honestly don't know that much about FUSE so I don't know how different it is to the regular filesystem interface, so perhaps most of the hard porting work has already been done.

A couple links that may help:
[http://en.wikipedia.org/wiki/Filesystem_in_Userspace](http://en.wikipedia.org/wiki/Filesystem_in_Userspace)
[http://fuse.sourceforge.net/](http://fuse.sourceforge.net/)

---

### Post by Nxion on 2009-12-07
Not sure if this thread is still open but another option is if you want the power of ZFS but still use Ubuntu, check this out. They do make a server and a desktop version.

[http://www.nexenta.org/]("http://www.nexenta.org/")

---

### Post by mm- on 2011-01-24
A tutorial for building and installing native ZFS packages (with POSIX layer) for Ubuntu and Fedora Linux is at [blog.vx.sk]("http://blog.vx.sk/archives/18-Tutorial-native-ZFS-on-Ubuntu-and-Fedora-Linux.html?user_language=en")

---

### Post by grausch on 2011-01-28
> **mm- said:**
> A tutorial for building and installing native ZFS packages (with POSIX layer) for Ubuntu and Fedora Linux is at [blog.vx.sk]("http://blog.vx.sk/archives/18-Tutorial-native-ZFS-on-Ubuntu-and-Fedora-Linux.html?user_language=en")

Hi,

Has anyone tested this?

Currently I am trying to get OpenIndiana to work for my fileserver, but I think going the Ubuntu route would be much easier.

Also, if anyone has tested this, how stable is the port?

Thanks,

Edit: Just found this: [http://www.phoronix.com/scan.php?page=article&item=kq_zfs_gold&num=1](http://www.phoronix.com/scan.php?page=article&item=kq_zfs_gold&num=1)

---

