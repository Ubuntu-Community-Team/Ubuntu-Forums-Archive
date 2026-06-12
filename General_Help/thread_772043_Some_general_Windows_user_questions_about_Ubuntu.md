---
title: "Some general Windows user questions about Ubuntu"
date: 2008-04-28
forum: General Help
---

### Post by marcosscriven on 2008-04-28
Hi

Just moved to Ubuntu 7.10 (waiting for 8.10 to become stable and installable on my computer)

Few questions:

1) Where's the conventional place to install apps that you don't get from apt-get? I ended up putting the JungleDisk binary in ~/JungleDisk/. But I don't suppose that's a good idea

2) When I installed, on a separate HD, my Windows HD appears on the desktop, but my Ubuntu one doesn't (although it does of course in Places->Computer)

3) How do I get rid of the floppy drive in Places->Computer?

4) Where's the best place to put auto-starts (ie so JungleDisk starts on boot)?

5) More general Linuxy stuff, can you recommend a really god book or online guide that goes through the average linux distro directory structure, variations therefore, the reasons, and even why they ended up getting names like /var /etc and so forth.?

6) Kind of a tagent this, but if you're running Ubuntu on Amazon's EC2 cloud, you actually have to use a Fedora core. Is that because the core is the only way to put drivers for virtual machines?

Marcos

---

### Post by Patsoe on 2008-04-28
1) The conventional place is either /opt or /usr/local, by the Filesystem Hierarchy Standard, see [http://www.debian.org/doc/packaging-manuals/fhs/fhs-2.3.html](http://www.debian.org/doc/packaging-manuals/fhs/fhs-2.3.html)
2) Yes, so you're Windows disk is treated as removable I guess. I'm not sure how to change that, I don't really know my way around in Gnome (all this stuff that happens automagically, it's like Windows ;))
3) I don't know how it's supposed to be done, but I know how I did it: in /etc/fstab I placed a # in front of the line that declares the floppy drive, and I removed the floppy directory from /media. Actually I also removed the floppy drive physically, otherwise this would make less sense of course.
4) I guess I'd think of an init script, but there must be more user friendly options, so maybe wait for someone else's advice.
5) See point 1. Lots of other nice stuff at [http://www.debian.org/doc/](http://www.debian.org/doc/) too. The Ubuntu documentation is of course also worth seeing, as is the Gentoo stuff.
6) No idea what you're talking about, sorry :)
7) By the way, Ubuntu 8.04 has been officially released. But check for hardware issues before you upgrade.

---

### Post by justleen on 2008-04-28
1)  depends.. normally Optional software goes to /opt (which doenst exist by default).

2) the root/filesystem is not listed on your desktop, only seperate disks

3) i think you just need to disable the floppy option in the bios, not to sure..

4) agian, depens.. if its a graphical application, just place it in System > prefs > Sessions > Startup progs.

5) there offcourse tons of information on that.. linuxnewbie might be a good place, or the wiki for ubuntu?

---

### Post by robelliott2125 on 2008-04-28
> **marcosscriven said:**
> Hi

Just moved to Ubuntu 7.10 (waiting for 8.10 to become stable and installable on my computer)

Few questions:

1) Where's the conventional place to install apps that you don't get from apt-get? I ended up putting the JungleDisk binary in ~/JungleDisk/. But I don't suppose that's a good idea

2) When I installed, on a separate HD, my Windows HD appears on the desktop, but my Ubuntu one doesn't (although it does of course in Places->Computer)

3) How do I get rid of the floppy drive in Places->Computer?

4) Where's the best place to put auto-starts (ie so JungleDisk starts on boot)?

5) More general Linuxy stuff, can you recommend a really god book or online guide that goes through the average linux distro directory structure, variations therefore, the reasons, and even why they ended up getting names like /var /etc and so forth.?

6) Kind of a tagent this, but if you're running Ubuntu on Amazon's EC2 cloud, you actually have to use a Fedora core. Is that because the core is the only way to put drivers for virtual machines?

Marcos

I'm sorry this won't really help much, but you can't see your Linux from Windows because its a different Filesystem that Windows doesn't recognise.

Remember, windows only recognises fat / fat32 and NTFS, anything else and it'll have to be converted to one of the above.  Windows is a pig that way.

At least, thats my thoughts to that.

Ubuntu is fair and allows you to still see all your NTFS partitions, since i'm still able to see all my data and use it.  Hence the opensource way...

Hope this sort of helps you...  I'm new also, so making stuff up as i go along.  :D

Urmmm, as others have said above me, try the wiki, and if need be, google...  I've an ebook here and a very intelligent friend who's used to ubuntu and linux as a whole, so i tend to ask him everything if i can't find it for myself.  :D  If you want the ebook, let me know, and I can email it to you or something.

---

### Post by Patsoe on 2008-04-28
> **justleen said:**
> 
4) agian, depens.. if its a graphical application, just place it in System > prefs > Sessions > Startup progs.

Doesn't that only run it when you're logged in? (Not sure, I'm really asking.)

robelliott2125: Ext2 support for Windows -> [http://www.fs-driver.org/](http://www.fs-driver.org/)
(so that also reads Ext3, but doesn't do the journaling)

---

