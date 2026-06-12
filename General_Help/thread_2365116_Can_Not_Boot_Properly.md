---
title: "Can Not Boot Properly"
date: 2017-07-03
forum: General Help
---

### Post by SBTlauien on 2017-07-03
I'm running Ubuntu 16.04.2 on my Surface Pro 3 and the only way that I can currently boot is by putting in a live USB, pressing C(to get the Grub2 command line), and typing these lines...

```

set root=(hd1,2)
linux /vmlinuz root=/dev/sda2
initrd /initrd.img
boot

```

This will boot me into my OS.  I had this problem when I first installed and it went away after I did a 'dist-upgrade' but after a crash, the problem is back.

How can I get it to boot directly into Ubuntu?

---

### Post by gsahli on 2017-07-03
Just for info - you've already tried sudo update-grub?

---

### Post by SBTlauien on 2017-07-03
> **gsahli said:**
> Just for info - you've already tried sudo update-grub?

Yes, I've tried 'update-grub'.

What is the difference between /boot and /etc/default/grub?  Looking through files in those two directories it appears as if things aren't pointing to 'hd1,2' but I don't want to mess anything up.

---

### Post by Dennis N on 2017-07-03
If Ubuntu is installed in BIOS mode, then boot into Ubuntu using your method, then reinstall grub:

```
sudo grub-install /dev/sda
```

Run **sudo update-grub** after this. This assumes your startup drive is sda. It will set the default boot to Ubuntu's grub menu.

If this is UEFI, that's another story.

---

### Post by SBTlauien on 2017-07-03
I believe it's UEFI.  How can I check though?  Before this install, I was dualbooting and had a special screen that allowed me to choose what OS I wanted to boot(see link below).  Now that I'm not dual booting, I want it to just boot into Ubuntu.  I think it's UEFI though.

Looks liike it was rEFInd: [http://blog.davidelner.com/dual-booting-ubuntu-14-10-on-the-surface-pro-3/](http://blog.davidelner.com/dual-booting-ubuntu-14-10-on-the-surface-pro-3/)

---

### Post by Dennis N on 2017-07-03
> **SBTlauien said:**
> I believe it's UEFI.  How can I check though?  Before this install, I was dualbooting and had a special screen that allowed me to choose what OS I wanted to boot(see link below).  Now that I'm not dual booting, I want it to just boot into Ubuntu.  I think it's UEFI though.

Looks liike it was rEFInd: [http://blog.davidelner.com/dual-booting-ubuntu-14-10-on-the-surface-pro-3/](http://blog.davidelner.com/dual-booting-ubuntu-14-10-on-the-surface-pro-3/)

If you had Windows 10 pre-installed, then it would be UEFI, but run this from Ubuntu to be sure of Ubuntu's boot mode:

```
[dmn@Sydney ~]$ df -h
Filesystem      Size  Used Avail Use% Mounted on
dev             1.9G     0  1.9G   0% /dev
run             1.9G  1.5M  1.9G   1% /run
/dev/sdb9        25G   17G  7.2G  70% /
tmpfs           1.9G   57M  1.9G   3% /dev/shm
tmpfs           1.9G     0  1.9G   0% /sys/fs/cgroup
/dev/sda4       120G   56G   58G  49% /mnt/Common-Files
tmpfs           1.9G   41M  1.9G   3% /tmp
[COLOR="#FF0000"]/dev/sdb1       197M  237K  197M   1% /boot/efi[/COLOR]
tmpfs           384M   44K  384M   1% /run/user/1000

```

If there is a partition mounted on /boot/efi, then it is installed as UEFI.

---

### Post by Dennis N on 2017-07-03
I just glanced through the article. I see you are using the Manual Booting technique shown in the appendix.

In the other section of the Appendix, the author says:
> If you install GRUB updates via Ubuntu's apt-get update or other package management system, you might find yourself being dumped back in GRUB after a reboot. To get things back to where they were, I suggest a rEFInd reinstall.

You could go through the steps he gives there.

---

### Post by SBTlauien on 2017-07-04
> **Dennis N said:**
> If you had Windows 10 pre-installed, then it would be UEFI, but run this from Ubuntu to be sure of Ubuntu's boot mode:

```
[dmn@Sydney ~]$ df -h
Filesystem      Size  Used Avail Use% Mounted on
dev             1.9G     0  1.9G   0% /dev
run             1.9G  1.5M  1.9G   1% /run
/dev/sdb9        25G   17G  7.2G  70% /
tmpfs           1.9G   57M  1.9G   3% /dev/shm
tmpfs           1.9G     0  1.9G   0% /sys/fs/cgroup
/dev/sda4       120G   56G   58G  49% /mnt/Common-Files
tmpfs           1.9G   41M  1.9G   3% /tmp
[COLOR=#FF0000]/dev/sdb1       197M  237K  197M   1% /boot/efi[/COLOR]
tmpfs           384M   44K  384M   1% /run/user/1000

```

If there is a partition mounted on /boot/efi, then it is installed as UEFI.

Looks like mine is UEFI...

```

Filesystem      Size  Used Avail Use% Mounted on
udev            1.9G     0  1.9G   0% /dev
tmpfs           386M  6.5M  380M   2% /run
/dev/sda2       113G   13G   95G  12% /
tmpfs           1.9G  288K  1.9G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           1.9G     0  1.9G   0% /sys/fs/cgroup
/dev/sda1       511M  4.9M  507M   1% /boot/efi
tmpfs           386M  4.0K  386M   1% /run/user/108
tmpfs           386M  100K  386M   1% /run/user/1000

```

In "/boot/efi/EFI/ubuntu/grub.cfg" it ihas(I x'ed out the uuid just in case)...

```

search.fs_uuid xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx root hd0,gpt2 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

```

Should that "hd0" be "hd1" instead?  This is just a guess.

---

### Post by SBTlauien on 2017-07-04
Running 'efibootmgr' gives me this...

```

Timeout: 2 seconds
BootOrder: 0002,0001
Boot0001  Windows Boot Manager
Boot0002  USB Drive

```

Why is "Windows Boot Manager" there?

---

### Post by Dennis N on 2017-07-04
> **SBTlauien said:**
> Running 'efibootmgr' gives me this...

```

Timeout: 2 seconds
BootOrder: 0002,0001
Boot0001  Windows Boot Manager
Boot0002  USB Drive

```


There is no Ubuntu entry. This is set to boot to the USB, so that is the problem. 

Try this from Ubuntu: it should generate a new entry in the boot list according to man page of efibootmgr:
```
sudo efibootmgr -c --disk /dev/sda --part 1 --label Ubuntu
```
where the number after --part is the partition number for the EFI system partition. 1 in this formulation would correspond to sda1.

If it works, run efibootmgr using -o option after this to fix the boot order if necessary.

---

### Post by SBTlauien on 2017-07-04
> **Dennis N said:**
> There is no Ubuntu entry. This is set to boot to the USB, so that is the problem.  I think it's set to that either because I have it set up to boot from the USB if media is attached, or because I happened to boot from the USB to get my system running.

---

### Post by SBTlauien on 2017-07-05
> **Dennis N said:**
> There is no Ubuntu entry. This is set to boot to the USB, so that is the problem.   Try this from Ubuntu: it should generate a new entry in the boot list according to man page of efibootmgr: ```
sudo efibootmgr -c --disk /dev/sda --part 1 --label Ubuntu
``` where the number after --part is the partition number for the EFI system partition. 1 in this formulation would correspond to sda1.  If it works, run efibootmgr using -o option after this to fix the boot order if necessary.  Running that command and now it won't even boot into a Live Session.  I get nothing but the Surface Pro 3 bootloader.

---

### Post by SBTlauien on 2017-07-05
Alright, I got it working.  For some reason, after running that command, it doesn't like to boot from the USB.  After turning it on and off and booting it with the volume-Up and volume-Down button held down, I got it to boot the live USB.

---

### Post by Dennis N on 2017-07-06
Well, the command makes a new numbered entry, and doesn't delete or replace anything. So if it does not work, you can simply use your previous one. I think you might need the -l option specifying the boot file path. Otherwise, you get some default stuff. I have used this once to restore an entry that vanished for some reason, and I remember I needed the -l option in that case. But some say all you need is -c and it will default to the current boot parameters.

---

### Post by SBTlauien on 2017-07-07
I tried running Boot Repaid Disk and I get a "locked-EFI" error.

I think before when I got it working, I had created some kind of key and then rebooted.

This is what my partitions look like..

[[IMG]http://i5.photobucket.com/albums/y156/SBTlauien/g_zpspuzdaapj.png[/IMG]]("http://s5.photobucket.com/user/SBTlauien/media/g_zpspuzdaapj.png.html")

---

### Post by SBTlauien on 2017-07-10
Bump.

---

### Post by SBTlauien on 2017-07-12
Somehow I got it working again.  What I did was I just booted into the live session by choosng the "Try Ubuntu" option and then I rebooted.  Now I am presented with the Grub2 menu.

I'd still like to know what is causing it to go back and forth and how I can permanently keep it the way it is.

---

