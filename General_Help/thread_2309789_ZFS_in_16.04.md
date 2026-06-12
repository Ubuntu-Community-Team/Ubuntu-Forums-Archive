---
title: "ZFS in 16.04?"
date: 2016-01-13
forum: General Help
---

### Post by bobk48 on 2016-01-13
How will zfs be implemented in Ubuntu 16.04? In the kernel as the root file system, exactly like Solaris, OpenIndie, FreeBSD, PCBSD, or as a user land add-on? I have read the posts dealing with zfs in earlier releases, and the instructions there for making it the root file system seem very complex and error-prone. I would like to, for example, mirror my boot/system disk using zfs.
Anyone at Canonical know the details and willing to share them at this time?
Thanks!

---

### Post by grahammechanical on 2016-01-13
> Anyone at Canonical know the details and willing to share them at this time?

This is a Ubuntu user forum. Do Canonical engineers use Ubuntu? I believe they do. Do Canonical engineers frequent this forum? Unlikely.

> ZFS is licensed under the [CDDL]("http://en.wikipedia.org/wiki/CDDL"), a popular and widely used [OSI-approved open source license]("http://opensource.org/licenses/category"), that is [recognised by the FSF]("https://www.gnu.org/licenses/license-list.html#CDDL")  as a free software license, but is incompatible with the GNU GPL.  **Because of that ZFS cannot be added to the Linux kernel directly**. It  can, however, be distributed as a DKMS package separate from the main  kernel package.

[https://wiki.ubuntu.com/ZFS](https://wiki.ubuntu.com/ZFS)

For Ubuntu 15.10 onwards
> 
ZFS support was added to Ubuntu Wily 15.10 as a technology preview. It is only supported on 64 bit architectures. 

To install ZFS, use: 

sudo apt-get install zfsutils-linuxthis will take a while to install as the ZFS drivers need to be built from source using DKMS, so please be patient. Below is a quick overview of ZFS, this is intended as a getting started primer.

[https://wiki.ubuntu.com/Kernel/Reference/ZFS](https://wiki.ubuntu.com/Kernel/Reference/ZFS)

I do not think that ZFS will be much more advanced than that in 16.04. But 16.04 does have ZFS utilities in the universe repository.

[https://github.com/zfsonlinux/pkg-zfs/wiki/HOWTO-install-Ubuntu-16.04-to-a-Native-ZFS-Root-Filesystem](https://github.com/zfsonlinux/pkg-zfs/wiki/HOWTO-install-Ubuntu-16.04-to-a-Native-ZFS-Root-Filesystem)

Still very complex and error prone, if you ask me.

Regards.

---

### Post by bobk48 on 2016-01-13
My understanding is, similar to iXsystems being the "steward" of PC-BSD, that Canonical is the steward of Ubuntu. That understanding does not include the actual ownership and legal stipulations of "stewardship".  So the 16.04 information that I have Googled so far comes from them, or at least it appears to come from their engineers. 
I know the procedure for getting zfs in 15.10. The root file system information for that release is what I referred to (at least to me as appearing) being complex and error prone, particularly on my part! Compare this to PC-BSD zfs mirroring of the system/boot disk: 5 easy-to-understand gpart commands and one zfs zpool command. Game over!
I have absolutely no idea what being "in the kernel" means anyway. I just know that userland commands for zfs work to do file system maintenance in a pretty convenient and easy to understand way.  Whether they are in the kernel or not makes absolutely no difference to me, as long as they work like they do in Solaris, OpenIndie, FreeBSD, and PC-BSD.

---

### Post by lukeiamyourfather on 2016-01-13
> **bobk48 said:**
> In the kernel as the root file system, exactly like Solaris, OpenIndie, FreeBSD, PCBSD, or as a user land add-on?

Neither. It's a kernel module so it's high performance like other file systems but it's not part of the Linux kernel itself (licensing issues). This is what Ubuntu is pulling from.

[http://zfsonlinux.org/](http://zfsonlinux.org/)

GRUB supports ZFS now which makes it much easier to do root file system with ZFS but I haven't tried this personally. I use it for storing data for network shares.

> **grahammechanical said:**
> Still very complex and error prone, if you ask me.

My experience with it is quite the opposite. I've been using ZFS on Linux with hundreds of terabytes of data in a production environment for several years.

> **bobk48 said:**
> Whether they are in the kernel or not makes absolutely no difference to me, as long as they work like they do in Solaris, OpenIndie, FreeBSD, and PC-BSD.

The commands work the same as they do on other platforms (zfs and zpool).

---

### Post by bobk48 on 2016-01-13
Thanks for the clarifications Darth, very valuable insights! And also very considerate of you to share your experiences with us.

Thanks for the feedback about Canonical! Also, I get similar feelings about ZFS implementation in LINUX, but read lukeiamyourfather comments above. Sounds good enough for me to give it a thorough test right now on one of my servers: IBM x3650 running 15.10 desktop, I can test everything in ZFS.

Did apt-get install zfsutils-linux, rebooted, now have zfs on 15.10 desktop. IBM x3650 has hardware RAID, so there might be some collisions there. zfs is useful on a single disk system, I have a 2 TB Samsung in the x3650 but can set copies=2 and zfs duplicates and bit level checks the disk. Can do many other sys admin chores, like snapshots, rsync over the network, etc.. Bravo Ubuntu and zfs! Looking forward to 16.04.

---

