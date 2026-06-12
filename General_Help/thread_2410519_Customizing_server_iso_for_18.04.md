---
title: "Customizing server iso for 18.04"
date: 2019-01-16
forum: General Help
---

### Post by copeland3300 on 2019-01-16
Hey All,

I'm trying to create a custom server ISO based on the following constraints:
 - The installation will be done on an air-gapped system
 - I'd like it to be as up to date as possible
 - I'm looking to use this iso to install several systems, both physical and virtual
 - I'd like to include a variety of software (source tarballs and snaps) that will be available to install without the iso


I thought the best way to do this was to build out a template system, with the snaps and tarballs staged in a directory, and then use that filesystem to create the squashfs that will be installed onto the other servers. 

Where I'm at right now:
 - I've generated the squashfs from the existing system
 - I've regenerated the filesystem.manifest and filesystem.size files in the /install directory on the iso
 - I've regenerated a new md5sum.txt at the root of the iso
 - I've tried to create new initrd and vmlinuz files, but the initrd doesn't work. I'm getting a variety of errors, and I'm not sure how to proceed from here.

Most of the guides I've come across talk about building a live system and use casper as part of it. They also seem targeted at versions prior to 18.04. I was unsure about building a live system, as I'm not really looking to boot to a live environment, I just want to install this existing build out. Additionally, I remember casper was used for 16.04, but I didn't see it being part of 18.04. I could be wrong on that though...

SO, if anyone has any resources to point me toward, or suggestions on how to proceed forward, I would greatly appreciate it.

Thanks

---

### Post by 1clue on 2019-01-16
I would consider a bootable USB stick rather than an iso. Then at any point you can update the files to get the latest software. And a USB stick typically holds a lot more data than a DVD. And it's rewritable.

Alternately you could use something like a system rescue cd which is not an installer at all, and add your staging directory to that. [http://www.system-rescue-cd.org/](http://www.system-rescue-cd.org/)

On the Gentoo distribution this would be called a stage 4 tarball. A pre-compiled image of your boot disk as you want it installed.

There is nothing magical about an installer ISO. All you need is:
[LIST=1]
[*]Something that boots and leaves all your devices named the same as they would be when your system boots.
[*]Enough tools to format and mount your partitions.
[*]A binary image of what you want to chroot into for the later part of the install. This would include a kernel, basic libraries, modules your system must have (matches your hardware), package manager, bash, maybe busybox, not sure what else.
[*]Enough tools to copy files or install .deb packages.
[*]An editor you like.
[*]A staging directory for packages you want.
[*]One or more scripts to automate the parts you will want to be consistent across your images.
[/LIST]

I think that's it, but I'm going from memory.

[https://wiki.gentoo.org/wiki/Stage_tarball](https://wiki.gentoo.org/wiki/Stage_tarball)

---

