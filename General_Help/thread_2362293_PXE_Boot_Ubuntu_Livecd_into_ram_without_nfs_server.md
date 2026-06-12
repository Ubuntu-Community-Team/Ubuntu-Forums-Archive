---
title: "PXE Boot Ubuntu Livecd into ram without nfs server"
date: 2017-05-26
forum: General Help
---

### Post by wazzgame on 2017-05-26
Hello,

I am trying to pxe boot a ubuntu desktop livecd without using a nfs server. We have a bunch of servers in our data center and I would like the ability to boot them to a livecd for rescue mode / debugging purposes. I would like everything to be booted to ram without using a nfs mount for root file system.

The issue I am running into is squashfs. What is the best way to embed squashfs or get the kernel/initrd to download and use squashfs? We would like to load everything from http so once its loaded it does not rely on any other external service like nfs. I have downloaded the latest ubuntu 16.04 desktop/livecd and extracted vmlinuz + initrd.lz + filesystem.squashfs.

# Example pxe boot config.
kernel [http://192.168.10.10/boot_templates/ubuntu_16.04/casper/vmlinuz](http://192.168.10.10/boot_templates/ubuntu_16.04/casper/vmlinuz) boot=casper
initrd [http://192.168.10.10/boot_templates/ubuntu_16.04/casper/initrd.lz](http://192.168.10.10/boot_templates/ubuntu_16.04/casper/initrd.lz)
boot

I have looked at 100 pxe boot guides and 95 of them use nfs. Some of the older ubuntu 10/ubuntu 12 guides do use a fetch command but that does not need to be working with the ubuntu 16.04 files from livecd. Example - "fetch=http://192.168.10.10/boot_templates/ubuntu_16.04/casper/filesystem.squashfs"

I asked some people in the irc channel and one person mentioned that you can build your squashfs into your initrd / initramfs but didn't provide more details on that. So what is the easiest way to accomplish this? Also If I could some how setup rc.local or something to wget a bash/shell script to install our key file, start ssh, and perform a few other commands that would be great. Thanks!

---

### Post by wazzgame on 2017-05-26
FYI I just downloaded the [debian-live-8.8.0-amd64-standard.iso]("https://cdimage.debian.org/debian-cd/current-live/amd64/iso-hybrid/debian-live-8.8.0-amd64-standard.iso")[COLOR=#000000]  and extracted [/COLOR]vmlinuz initrd.img filesystem.squashfs and it fully booted to livecd from pxe. I used the same exact config for ubuntu and it fails trying to load root fs. I assume "fetch=" is not valid or integrated? 

kernel [http://192.168.10.10/boot_templates/debian_8.8/live/vmlinuz](http://192.168.10.10/boot_templates/debian_8.8/live/vmlinuz)
initrd [http://192.168.10.10/boot_templates/debian_8.8/live/initrd.img](http://192.168.10.10/boot_templates/debian_8.8/live/initrd.img)
imgargs vmlinuz boot=live config hooks=filesystem username=live noeject fetch=http://192.168.10.10/boot_templates/debian_8.8/live/filesystem.squashfs
boot

---

### Post by wazzgame on 2017-05-30
So it seems casper doesn't support http fetch of filesystem.squashfs. I found a patch on [https://forum.kde.org/viewtopic.php?f=309&t=136596](https://forum.kde.org/viewtopic.php?f=309&t=136596) but it doesn't seem to be working with the latest initrd/scripts/casper

Perhaps someone can take a look at the altered initrd/scripts/casper file and fix it up?
[https://pastebin.com/V6W39XJu](https://pastebin.com/V6W39XJu)

---

### Post by rp201 on 2018-02-21
Hello I see this thread is old but I have a small portable ar150 portable router from gl-inet with openwrt on it.  I decided to try out slitaz as and tftp boot from it since I read it did not reaquire nfs.  works  great

used this help [https://www.pcsuggest.com/boot-slitaz-from-a-openwrt-pxe-boot-server/](https://www.pcsuggest.com/boot-slitaz-from-a-openwrt-pxe-boot-server/)


slitaz worked great and booted quickly and was very responsive  if your using openwrt as you tftp server the readme has a typo of kmod  and it says komd in the setup process.  This was very easy cause I can use just about any pc and not have to deal with the wireless drivers and or compatabilty so  if I'm using the 32bit os I can boot it on just about anyting with a pxe boot lan card.  great to have tools live gparted or cloning and networking and all you need is a lancard and usb port for power. I'm actually typing this from the pxe boot of slitaz from the portable router.

---

