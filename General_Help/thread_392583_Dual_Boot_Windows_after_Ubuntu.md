---
title: "Dual Boot Windows after Ubuntu"
date: 2007-03-24
forum: General Help
---

### Post by greenrabbi on 2007-03-24
Alright, 

So here is the situation. I had Ubuntu 6.10 installed, and i took windows completely off my computer. I am fluent with windows, but a complete newbie with linux.

So, after much adeau, I finally got my dual monitors and beryl, and all those fun things installed and working. But, a while after diving right into ubuntu, i realize that there are limitations that i need windows to supplement. 

So I went for the dual boot. I have the "C:" drive (aka. hda, or hd0) basically empty, and I had my second drive running ubuntu and all my files. So, I installed windows fine, then threw in the liveCd after restarting. I did the grub modifications, (setup (hd0), etc) then restarted. 

Well... nothing is working now. I am getting errors saying, "can't access tty". So i thought grub might be pointing to the wrong partition. In that menu, (to pick the boot), i went in to edit where it was grub pointing to. But it looks right. I tried changing it to every other partition (hd0,0 hd0,1...) but all of them said "cannot mount partion" or something to this effect. The correct one for me, (hd1,0) is were i am sure my root folder is. Well, it starts to load, and I get that tty error.

Conversely, if I try to load XP, i get a very brief "GUI Loading... something something 1.5" and then it goes back to the boot menu. I tried loading previous releases of the kernal as well but to no avail.

Any help would be appreciated. I am so frustrated with song and dance i have to do everytime i want linux to do something new, that i almost just want to go back to "windoze" just to save me the head-ache (which is ironic). 

I love the idea of linux, and OSS... but I am almost starting to feel like i don't have the time to continue having to reconfigure every little thing if i want to do something in ubuntu. It makes me upset, because i like the entire philosophy behind linux and I want to stand behind it but it seems like i am always scouring the internet trying to figure out how to do respectively simple things.

Anyways, I can't find this same problem elsewhere. A few posts with this error due to other things... but I am not finding solutions.

I would love some help if possible. Thanks so much.

---

### Post by confused57 on 2007-03-24
Does Ubuntu boot, if you boot first to your Ubuntu drive?  If so, you could just add an entry to boot Windows to your /boot/grub/menu.lst, something similar to the one in this link:

[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

### Post by jwbaker on 2007-03-25
The way it sounds to me is that you got grub to boot off the right partition, but you didn't change the root=whatever kernel argument.  Since you added a disk, the device names will have changed.

So you need to get into grub, do root (hd1,0), kernel /boot/vmlinuxwhateveretc root=/dev/hdc???, initrd=/boot/initrd.imgblahblahblah, and finally the "boot" command.

---

### Post by greenrabbi on 2007-03-25
Hi, 
I did not add an extra harddrive. It has always been there, just not being used for file storage. It could have been... i mean, i just needed to save or transfer the files to it.

So, I decided (after about 2-3 months of strict ubuntu use), that I **needed** some of the programs that just don't run, or run properly on ubuntu.

That's why I installed windows on the free drive. I did format the harddrive partition to ntfs... but i can't see how that would make a difference, (as ubuntu is completely on a different drive.)

so right now, I am actually not able to boot to either windows, or ubuntu. I am stuck on livecd until i find a solution. 

To clarify, i get the:
> **Ephemeral said:**
> Hello !

```
/bin/sh : can't access tty; job control turned off
(initramfs) _
```

And something about a BusyBox v(something) Debian.

As someone else put it.

Any idea's? The kernal still seems to be pointed to within grub... I can check again though. 

Thanks for any help.

---

### Post by confused57 on 2007-03-25
From the live cd, you might want to post the output of:
```
sudo fdisk -l
```
the -l is a small "L"

and

```
sudo grub
find /boot/grub/stage1
quit
```

You may be able to install grub to your Ubuntu drive mbr, using the live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

then set your bios to boot your Ubuntu drive before the Windows drive, if you get a grub menu at boot, highlight your Ubuntu entry, press "e" to edit, change or make sure root is (hd0,0), depending on what "sudo fdisk -l" shows as your root partition, then press "b" to boot.

If your Ubuntu drive boots doing this, then you could add an entry similar to the one in the link I provided in my first reply.

---

### Post by jwbaker on 2007-03-25
It sounds to me as if grub is booting your kernel without an initrd.  That's usually what causes the drop into busybox.  It's very difficult to diagnose these types of problems on a forum, however, so I could be wrong.

---

### Post by greenrabbi on 2007-03-25
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1           6       48163+  de  Dell Utility
/dev/hda2               7        9726    78075900    7  HPFS/NTFS

Disk /dev/hdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       14031   112703976   83  Linux
/dev/hdb2           14770       30515   126479745    b  W95 FAT32
/dev/hdb3           14032       14500     3767242+  83  Linux
/dev/hdb4           14501       14769     2160742+  82  Linux swap / Solaris

Partition table entries are not in disk order
```

```
grub> find /boot/grub/stage1
 (hd1,0)
```

I am going to check the grub menu. It does goto the grub menu, but I think that I have the right root drive selected properly already. I feel like windows is trying to sabotage linux... which i wouldn't put past them... 

I will double check...

Thanks for your help.

---

### Post by greenrabbi on 2007-03-25
so in the grub menu...

```
root (hd1,0)
kernel /boot/vmlinuz-2.6.17-generic root=/dev/hdb1 ro quiet splas->
initrd /boot/initrd.img-2.6.17-10-generic
quiet
savedefualt
boot
```

I tried booting via the recovery selection in the grub menu... and this is some of the things i saw

```
EXT3-fs: group descriptors corrupted!
mount: Mounting /dev/hdb1 on /root failed
mount: /root/dev ... no such file or directory
mount: /proc on /root/proc failed: no such file or directory
Target filesystem doesn't have /sbin/init
```

Any thoughts on this?

---

### Post by bulldog on 2007-03-25
Your entry in GRUB is correct,but what the recovery spits out,isn't very nice.

I'm afraid your ubuntu is destroyed,but have to say,I'm no expert about this.

I should try to copy important data,if there is any,and do a reinstall.

Or wait till some body comes along who can help you recover it,if possible.

---

### Post by greenrabbi on 2007-03-25
yeah... it's a mofo...

anyone have idea's how to fix/get some files off of here?

Thanks.

Blu.

---

### Post by greenrabbi on 2007-03-25
Alright, so here is the situation.

I reinstalled windows, and i can transfer many of my media files to my hd0. 

I then downloaded, explore2fs, which allows windows to read ext2/ext3...

so I am recovering many of my files this way.

However, it is clear that the drive must not be currupted if I can transfer these files.

I would like to have linux still on my computer... and keep growing in my knowledge with it, however, in another sense... i almost feel like washing the blood of all the days of time i have killed trying to get linux to function properly. 

There is just no time to completely reinstall the entire system from the ground up. the video driver was ridiculously complex from my memory... and beryl junked up my computer the first time i installed it. *sigh* 

It's tragic that all drivers and whatnot are generally only created for windows systems. Then they leave us the scraps to try and port them to linux. 

What linux really needs, is some added user friendliness. more gui installed applications, with clicking. I am unsure why most linux people are married to the terminal. I mean, it's great that you know all the commands and what-have-you, but for average users, (especially those used to windows systems), the learning curve becomes so steep that without advanced computer aptitude, it is a system that is not seemingly reachable without hours of time to completely reeducate themselves as to how computers function.

I want to be clear that i think the linux system is often more logical, and in turn better... but i really think that the user-friendliness needs to be increased. 

Let me if anyone has any idea's how i can "salvage" my ubuntu system. Otherwise, I think i might just scrap it for now and maybe try it again when I have a couple of weeks to kill...

Regards, 

Blu.

---

### Post by confused57 on 2007-03-25
You might be able to run a filesystem check on your root partition:
[http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem](http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem)

also, see the link to the gparted live cd, which can also perform a check on a partition...I think all you do is right-click on the partition & select "check"...worth a shot.

If you decide to reinstall Ubuntu you might want to check out the link I provided earlier:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)
note that I have a Dell Dimension 4550, and I can't boot first to the slave drive, so I opted to install Ubuntu to a drive connected as master, moved my Windows drive to the slave position & added an entry to grub to boot Windows.

---

