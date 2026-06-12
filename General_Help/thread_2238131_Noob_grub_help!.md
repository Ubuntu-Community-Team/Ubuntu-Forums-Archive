---
title: "Noob grub help!"
date: 2014-08-06
forum: General Help
---

### Post by alan36 on 2014-08-06
So Im a noob to linux, and a first year computer science student who's playing around with amazon's ec2 during summer.
while prepping my first server of ubuntu with  "aptitude update" and "aptitude upgrade" like I have seen on youtube.
I suddenly get prompted with 2 boxes

1:>  The GRUB boot loader was previously installed to a disk that is no longer present, or whose unique identifier   &#9474;
 &#9474; has changed for some reason. It is important to make sure that the installed GRUB core image stays in sync      &#9474;
 &#9474; with GRUB modules and grub.cfg. Please check again to make sure that GRUB is written to the appropriate boot    &#9474;
 &#9474; devices.                                                                                                        &#9474;
 &#9474;                                                                                                                 &#9474;
 &#9474; If you're unsure which drive is designated as boot drive by your BIOS, it is often a good idea to install GRUB  &#9474;
 &#9474; to all of them.                                                                                                 &#9474;
 &#9474;                                                                                                                 &#9474;
 &#9474; Note: it is possible to install GRUB to partition boot records as well, and some appropriate partitions are     &#9474;
 &#9474; offered here. However, this forces GRUB to use the blocklist mechanism, which makes it less reliable, and       &#9474;
 &#9474; therefore is not recommended.                                                                                   &#9474;
 &#9474;                                                                                                                 &#9474;
 &#9474; GRUB install devices:                                                                                           &#9474;
 &#9474;                                                                                                                 &#9474;
 &#9474;    [ ] /dev/xvda (8589 MB; ???)                                                                                 &#9474;
 &#9474;    [ ] /dev/xvda1 (8578 MB; ???)                                                                                &#9474;
 &#9474;                                         

I have no clue what this means, and could someone explain it to me in laymans terms, and what I should select? Ive already tried googling and reading documentation; but the esoteric terms are simply a bit overwhelming for me. the second one was

2:> [COLOR=#000000][FONT=Verdana]A new version of /boot/grub/menu.lst is available, but the version installed currently has been locally modified. [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]1. install the package maintainer's version[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]2. keep the local version currently installed[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]3. show the differences between the versions[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]4. show a side-by-side difference between the versions[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]5. show a 3-way difference between available versions[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]6. do a 3-way merge between available versions (experimental)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]7. start a new shell to examine the situation[/FONT][/COLOR]

thanks for any help!


oh and p.s. just before the upgrade terminated, I got this message:
did I do something wrong, do I need to reinstall or something?

> Setting up open-vm-tools (2:9.4.0-1280544-5ubuntu6.2) ...open-vm-tools: not starting as this is not a VMware VM
Processing triggers for libc-bin (2.19-0ubuntu6.1) ...
Processing triggers for ureadahead (0.100.0-16) ...
Processing triggers for initramfs-tools (0.103ubuntu4.2) ...
update-initramfs: Generating /boot/initrd.img-3.13.0-32-generic
**W: Operation was interrupted before it could finish**


Current status: 0 updates [-61].




---

### Post by grahammechanical on 2014-08-06
Here goes. At least part of the way.

When we install Ubuntu whether it is the desktop or server version a boot loader will also be installed. It is called Grub (GRand Unified Bootloader). By default it will install into the MBR (Master Boot Record) of the first hard disk. And it will look for its configuration files in the /boot directory on the partition that Ubuntu is installed in. How does it find the correct partition? 

When the Ubuntu installer creates a partition it will give that partition a UUID (Universally Unique IDentifier), a combination of alpha-numeric characters that identify that partition. The first message is saying that Grub cannot find the partition where its configuration files stored. What changes have you made to the hard disks and partitions in this system?

Wikipedia has told me that xvda = Xen Virtual Disk *a* and xvda1 = Xen Virtual Disk *a* and partition *1*. Are you running Xen? Have you made changes to the set up in Xen? Again wikipedia tells me this:

> [COLOR=#252525][FONT=sans-serif]Xen boots from a [/FONT][/COLOR][bootloader]("http://en.wikipedia.org/wiki/Bootloader")[COLOR=#252525][FONT=sans-serif] such as [/FONT][/COLOR][GNU GRUB]("http://en.wikipedia.org/wiki/GNU_GRUB")[COLOR=#252525][FONT=sans-serif], and then usually loads a [/FONT][/COLOR][paravirtualized]("http://en.wikipedia.org/wiki/Paravirtualization")[COLOR=#252525][FONT=sans-serif] host operating system into the host domain (dom0).[/FONT][/COLOR]

[http://en.wikipedia.org/wiki/Xen](http://en.wikipedia.org/wiki/Xen)

I do not think that this is a Ubuntu problem but a Xen problem.

The second message is giving you the option of allowing the Grub configuration file to be overwritten by a default version or to keep the modified version that you have edited at some point. There are other options but those are the simple "Do I or Don't I" options. Now, the question is this, Which Grub is being updated? The Grub that loads Xen or the Grub inside the Xen virtual hard disk that loads Ubuntu server?

Regards.

---

### Post by alan36 on 2014-08-06
But I have not touched anything else besides launching the amazon ec2 instance!
Literally have not touched anything

---

### Post by oldfred on 2014-08-06
Somewhere you started an update process. Often just installing software will do that to make sure it is current.

But it says menu.lst. That is grub legacy last used with Ubuntu 9.04 or April 2009. It still is in repository, but grub2 has and is the current boot loader. Why do you have grub legacy?

When major updates occur, it will update its configuration files. So you must have edited menu.lst and now it says it wants to install the new version or keep your old version. 

It is a lose, lose situation unless you backed up your menu.lst already. 
If you use your version you may not be able to boot as new version may be a lot different. Or the customizations you made will be lost and you cannot boot because you need those customizations. And usually choosing merge does not work.

---

### Post by alan36 on 2014-08-06
After launching the EC2 instance for the current ubuntu server OS
I simply typed the
sudo aptitude update
sudo aptitude upgrade

are you saying I should not type update?

---

### Post by oldfred on 2014-08-06
Generally you want to keep system up to date.

Some with critical servers may delay updates for a while. They test the updates in the backup server first.

---

### Post by alan36 on 2014-08-07
well then, is there a way to simply upgrade the libraries that I use, such as imagick, and its dependency tree - without touching bootloader/kernel updates?
(*without manually updating every single one*)
like something akin to an except option

---

