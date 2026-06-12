---
title: "is there any way to make a reliable usb installation with persistence?"
date: 2013-06-29
forum: General Help
---

### Post by jjjjswait on 2013-06-29
hello,
does anyone have advice about making a reliable, usable usb ubuntu installation that has persistence?  i've failed many times.  i'm using a variety of usb drives, three installer applications (unetbootin, startup disk creator and lilu), multiple computers using linux and windows, and have installed three versions of ubuntu, two versions of lubuntu, two versions of xubuntu, two versions of mint, and puppy linux. 
one of two things goes wrong every time; either the drive eventually refuses to boot, or (more often) I'm unable to install certain common packages.
as for the second problem, which seems to be the fixable one, i haven't been able to find any useful information online.  upon installation i am unable to install certain software (eg: adobe flash plugin, vlc).  if i try to install in synaptics i'm given this message (for flash):
" Could not mark all packages for installation or upgrade
The folowing packages have unresolvable dependencies.  Make sure that all required repositories are added and enabled in the preferences.
flashplugin-installer:
 Depends: libnspr4-0d but it is not going to be installed "
if i try to install from the software center i'm given this message:
" Package dependencies cannot be resolved
This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time. "
i've gone into 'software sources'  and clicked all of the boxes.   that doesn't change anything.  with one or two installations i've been able to install any packages at first, but then either lose the ability or the usb fails to boot after a week or so.
has anyone else had a similar experience?  i'm exclusively  using usb installations on an old eee pc with no internal hdd.  i don't want to give up on it yet.  does anyone have any ideas?  i've never had the package source/installation problems on regular, non-usb installs of x/l/ubuntu/mint.  thanks

---

### Post by kurt18947 on 2013-06-29
Yes,  I've done a 'real' install on a flash drive vs. a 'live' install with persistence.  I've never tried this on a netbook but it should work, it'll just be slower.  I've done this from a desktop with all the hard drives unplugged so the lack of a functional hard drive shouldn't be a showstopper.   You need a 'live' install in order to create the 'real' install.  I assume you have two functional USB ports so you should be okay there.  Boot the live install, plug in the target USB flash drive, you could use gparted to create a Linux compatible file system on the target flash drive then install as per normal.  I've used ext2 for a file system in the past but in the future I'll probably use ext4 and modify fstab like I were installing to a SSD and see how that works out.  

My experience is that installing and updating on a flash drive is much slower than a spinning hard drive - writing to flash is much slower than reading.  Once installed and updated, it runs a little slower than from a hard drive but it's still quite usable.  And it's a 'real' install so I can update, install proprietary drivers and printers etc. just like installing to a hard drive.  I was concerned about durability - flash memory cells 'wear out' from being written to but another member here has had a 'real' USB flash drive install working for several months at least and it's still working well.

---

