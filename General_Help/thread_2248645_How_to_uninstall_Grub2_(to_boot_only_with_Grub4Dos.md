---
title: "How to uninstall Grub2 (to boot only with Grub4Dos)"
date: 2014-10-15
forum: General Help
---

### Post by Kirkx on 2014-10-15
I have a few Linux distros installed on different partitions and all of them are booted from Grub4Dos w/o any problems. I want to completely get rid of Grub2 from all distro installations and maybe leave it intact only in one of them, just in case. Compared to Grub4Dos, Grub2 is a bloated pig that makes the process of each kernel update extremely long, especially when there are multiple Linux versions installed on the same machine. You just get stuck watching the screen showing the message "updating grub configuration file" when Grub2 slowly scans the hard drive.

I assume that if you have kernel v3.13.0-37 Grub4Dos only really needs two files to boot Ubuntu, Xubuntu, Kubuntu, etc, and all the remaining files in "boot" directory can be deleted:

/boot/vmlinuz-3.13.0-37-generic
/boot/initrd.img-3.13.0-37-generic

[http://i.imgur.com/muqeLe5.png](http://i.imgur.com/muqeLe5.png)

For the record, booting Linux from Grub4Dos is explained here:

[http://reboot.pro/topic/20015-booting-linux-from-grub4dos/](http://reboot.pro/topic/20015-booting-linux-from-grub4dos/)

---

### Post by Kirkx on 2014-10-24
After checking Synaptic it seems that Grub2 which comes with Xubuntu 14.04.1 on my Legacy/BIOS machine consists of the following packages:

grub-pc, grub-common, grub2-common, grub-pc-bin, grub-gfxpayload-lists

I'm wondering what is the cleanest way to remove all those packages.

1) The command shown below usually comes up when you google the subject but I'm wondering if it is sufficient:

```

sudo apt-get purge grub-pc grub-common

```

2) How about including all five packages in "purge"  command:

```

sudo apt-get purge grub-pc grub-common grub2-common grub-pc-bin grub-gfxpayload-lists

```

3) Another option would be to remove the packages from Synaptic.

---

### Post by Al1000 on 2014-10-24
I also use Grub4Dos, and just disregard the Grub files.

So I find the title of the thread to be rather confusing. Unless you are using Grub4Dos to boot into the Grub bootloader, you should already be booting only with Grub4Dos.

Now and again I lose my Grub4Dos boot menu when updates for Kubuntu include updates for Grub, but when that happens I just run Grub4Dos again, then delete the menu.lst it creates and replace it with a back-up of the one I already have.

---

### Post by oldfred on 2014-10-24
I did not originally like grub2. I had used grub legacy to multiple-boot using chain loading from a grub only partition.

But now I just turn off os-prober since I also have lots of installs and it does take forever to scan system. And with grub2 the link method seems to work well to always boot most current kernel.

       From Ranch hand
You only need 3 scripts for grub2 to tick like a clock;
00_header
05_debian-theme
06_custom (or 07, 08, 09, 25, 40)

Shows use of Links & changing colors of fonts and back ground image:
      
 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)
[https://help.ubuntu.com/community/Grub2/Displays](https://help.ubuntu.com/community/Grub2/Displays)

---

### Post by Kirkx on 2014-10-26
Thank you both for your comments. Turning off os-prober is the easy solution. You still get stuck for a short while watching the message "generating grub configuration file" but it's acceptable. For the record, here are instructions how to turn off os-prober:

- gksudo to: /etc/default/grub

- add the following line:

GRUB_DISABLE_OS_PROBER=true

Ref: [https://help.ubuntu.com/community/Grub2/Setup](https://help.ubuntu.com/community/Grub2/Setup)

In case you decide to completely uninstall Grub2, as discussed in earlier posts, then os-prober should be included in the purge command:```

sudo apt-get purge grub-pc grub-common grub2-common grub-pc-bin grub-gfxpayload-lists os-prober

```

---

### Post by Kirkx on 2014-10-30
Update: I have uninstalled Grub2 using the command mentioned earlier (shown below) and Xubuntu boots just fine chainloaded from Grub4Dos.

```

sudo apt-get purge grub-pc grub-common grub2-common grub-pc-bin grub-gfxpayload-lists os-prober

```

There seems to be too many files left over (see screenshots 2-5 below). Maybe some more packages should have been included in the purge command. I'm not sure which of these files can be safely deleted manually. It is possible that only the files on screenshot #1 are really needed and all the others can be deleted.

1)  [http://i.imgur.com/A7FkY8t.png](http://i.imgur.com/A7FkY8t.png)

2)  [http://i.imgur.com/lwFomxi.png](http://i.imgur.com/lwFomxi.png)

3)  [http://i.imgur.com/HZiJPsL.png](http://i.imgur.com/HZiJPsL.png)

4)  [http://i.imgur.com/hAMpIGX.png](http://i.imgur.com/hAMpIGX.png)

5)  [http://i.imgur.com/3pmbMdb.png](http://i.imgur.com/3pmbMdb.png)

6)  [http://i.imgur.com/IYR0E6A.png](http://i.imgur.com/IYR0E6A.png)

---

### Post by oldfred on 2014-10-30
Your first screen shot is the kernels & initrd files that actually boot system. 
Not sure about rest.

---

### Post by Kirkx on 2014-11-13
Update: I have deleted all left over files and directories mentioned in my previous post (screenshots 2-5) and Xubuntu booted and worked just fine without them. However, during the subsequent kernel upgrade all of them were reinstalled, so there is really no point going this route.

During the kernel upgrade (to v3.13.0-39) the installer initially insists on re-installing all the packages removed as described in my last post, but don't worry:

```

sudo apt-get -y install  linux-headers-3.13.0-39  linux-headers-3.13.0-39-generic  linux-image-3.13.0-39-generic  linux-image-extra-3.13.0-39-generic

```

During the process the following window pops-up:

[http://i.imgur.com/DLKbg0N.png](http://i.imgur.com/DLKbg0N.png)

At this point you need to tab to OK (make sure that you do not hit the spacebar by mistake because this would select the disk or partition for Grub2 installation). At the next window click YES (Continue without installing Grub):

[http://i.imgur.com/bHOaDBO.png](http://i.imgur.com/bHOaDBO.png)

And that's it. The message "update/generate grub configuration file" will not show any more.

---

### Post by Al1000 on 2014-11-13
I have changed my boot configuration files since I last posted in this thread, since I decided that I wanted access to the memory test options (although I haven't got round to using them yet) on the Grub2 menu.

So I have this in menu.lst which boots the computer into Kubuntu directly with Grub4Dos:

```
title Kubuntu 12.04.4 LTS (sda7)
uuid c3401d73-0c85-43ba-abf5-dc18b525f3e7
kernel /vmlinuz root=/dev/sda7 rootdelay=5 ro quiet splash
initrd /initrd.img
```

...and I have this in menu-advanced.lst which 'finds' the Grub2 boot menu (from where I can boot into Kubuntu using Grub2 should I want to for any reason - such as to see a different splash screen... )

```
title Find Grub2
  find --set-root --ignore-floppies --ignore-cd /boot/grub/core.img
  kernel /boot/grub/core.img
```

---

### Post by Kirkx on 2014-11-15
Thanks for posting your Grub4Dos menu.lst. Here are a few observations.

1) I could never get vmlinuz and initrd.img symlinks working properly. They would sometimes work and sometimes not, with the following commands:

```

title Xubuntu (symlinks)
root (hd0,22)
kernel /vmlinuz root=/dev/sda23 ro
initrd /initrd.img

```

To get reliable boot I was always using the hard coded kernel version:

```

title Xubuntu
root (hd0,22)
kernel /boot/vmlinuz-3.13.0-39-generic root=UUID=95c8g184-fdze-7b49-8st5-b88g4f5d3729 ro
initrd /boot/initrd.img-3.13.0-39-generic

```

However, your commands seem to resolve this problem. It's either the line with UUID or "rootdelay" parameter (I set it to 3 seconds, which should be sufficient if you just boot from internal hard disk).

```

title Xubuntu
uuid 95c8g184-fdze-7b49-8st5-b88g4f5d3729
kernel /vmlinuz root=/dev/sda23 rootdelay=3 ro
initrd /initrd.img

```

I didn't know that you can have the separate line with UUID like that. Are you sure that's the proper syntax, and not something like:

```

root=UUID=95c8g184-fdze-7b49-8st5-b88g4f5d3729

```

2) I have run a few tests to see what happens to vmlinuz and initrd.img symlinks during kernel upgrade and downgrade on my system (with Grub2 uninstalled and its leftover files left intact as explained in my previous post). I was upgrading/downgrading between kernel 3.13.0-37-generic and 3.13.0-39-generic.

a) when the kernel is upgraded the new symlinks will be automatically generated. So you do not need Grub2 installed for that.

b) the above is only the case with mainstream, generic kernels. If you upgrade to some beta kernel then you might be out of luck. I upgraded my Linux Lite kernel to 3.17.0-linuxlite and the new symlinks were not created.

c) when the kernel is downgraded then the symlinks for the uninstalled kernel are deleted, but the ones for the previous kernel version will not have "old" extension automatically removed, you need to do this manually:

[http://i.imgur.com/E4zXolh.png](http://i.imgur.com/E4zXolh.png)

3) Without Grub2, upgrading or downgrading a kernel is a breeze. With four distros installed on the computer, this downgrade took about 15 seconds to complete:

[http://i.imgur.com/s05kwZh.png](http://i.imgur.com/s05kwZh.png)

And the following upgrade took about 30 seconds to finish:

[http://i.imgur.com/Ci1E1Ni.png](http://i.imgur.com/Ci1E1Ni.png)

---

### Post by Kirkx on 2014-11-20
After a few month break I have decided to play around with booting Xubuntu from Grub4Dos using kernel and initrd symlinks and this time around I had no problems at all. Below are three code examples that work ok booting Xubuntu v14.04.1 (kernel v3.13.0-39-generic) installed on hard disk #1 on a system with Grub2 permanently uninstalled. I skipped [rootdelay=n] parameter mentioned before, assuming that it is only needed when booting from the live media.

1) This seems to be the cleanest code. It passes the UUID as the kernel parameter:

```

title Xubuntu (symlinks-1)
root (hd0,22)
kernel /vmlinuz root=UUID=95c8g184-fdze-7b49-8st5-b88g4f5d3729 ro
initrd /initrd.img

```

UUID must be in upper case, entering it in lower case (as shown below) will result in kernel panic:

```
kernel /vmlinuz root=uuid=95c8g184-fdze-7b49-8st5-b88g4f5d3729 ro
```

2) This code does not specify UUID at all, only device (partition) number. My guess is that it doesn't work with all kernels, probably only with newer ones.

```

title Xubuntu (symlinks-2)
root (hd0,22)
kernel /vmlinuz root=/dev/sda23 ro
initrd /initrd.img

```

3) This is the code with "root" command replaced by "uuid" command (as reported by Al1000 in his post). In this case "uuid" must be in lower case, otherwise the boot process will stop and throw some error code. This command wasn't available in older versions of Grub4Dos.

```

title Xubuntu (symlinks-3)
uuid 95c8g184-fdze-7b49-8st5-b88g4f5d3729
kernel /vmlinuz root=/dev/sda23 ro
initrd /initrd.img

```

---

