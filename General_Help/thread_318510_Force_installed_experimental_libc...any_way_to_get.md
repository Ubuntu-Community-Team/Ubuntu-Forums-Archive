---
title: "Force installed experimental libc...any way to get back?"
date: 2006-12-14
forum: General Help
---

### Post by sleestak240 on 2006-12-14
Hey all,
Well, feeling frisky from my success installing Win2K and VMPlayer along with VMTools I decided to try and get VMPlayer running with 3D Acceleration.  I was getting an error about OpenGL needing GCC 4.2 so I set about making that happen by download Debian experimental packages.  Well, obviously I needed libgcc and the experimental libc6 2.5 pacakges.  Well, I did something stupid and force-depends installed the new libc pacakges using dpkg and almost immediately everything went crazy...no way to get back to the default Ubuntu packages.  So, I did a reboot knowing I wasn't getting back in...and obviously I didn't.  Tried the CD rescue mode and tried to get a shell and can't.  I think I already know the answer, but I'm kind of in denial since I've spent months getting everything the way I wanted it.  Is there any hope for me, or is tomorrow a lost day having to reinstall and reconfigure Ubuntu?  I'm hoping there is some way I can bring back the old version of libc without destroying my setup.  I tried to play with fire and got burned...never again. :p

---

### Post by sleestak240 on 2006-12-14
Alright, well...I've mounted the drive in a Live CD and have been trying to run the package managers to no avail.  apt-get install -f does not work, dpkg does not work, and I can't run Synaptic.  

dpkg gives me this:
/mnt/hda3/usr/bin/dpkg: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /mnt/hda3/usr/bin/dpkg)

apt-get install -f and synaptic gives me this:
/mnt/hda3/usr/bin/apt-get: error while loading shared libraries: libapt-pkg-libc6.4-6.so.3.51: cannot open shared object file: No such file or directory

So...is there anything I can do without being able to run a package manager?  Is there anyway I can read and modify the package database from my Live CD?

---

### Post by napsilan on 2006-12-14
you can try booting off the livecd, chrooting into your installed system, and using dpkg and apt from there.  If all else fails, you should be able to copy your important files to safety using a livecd as well.  

chroot goes something like this:

mount your existing partition at, let's say, /target
chroot /target

and you should have most of your remaining console commands referencing your installed system rather than the live system.  

Check the wiki for more info before trying this.  I've only done it once and that was part of a dmraid install.

---

### Post by sleestak240 on 2006-12-14
Yeah, that's pretty much what I've done...booted the LiveCD into a Gnome desktop and mounted the drives.  Problem is, I can't run any of the commands on my installed system because the libc libraries are half-installed.  I've pretty much decided I'm going for the reinstall...at least I can make backups of my stuff like you said. 

It's finally time to do away with that Windows XP partition anyways I think! :mrgreen:

---

