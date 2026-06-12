---
title: "a start job is running for /boot/efi (1.30 min slow boot time)"
date: 2022-06-12
forum: General Help
---

### Post by user9820 on 2022-06-12
I am experiencing very slow boot times on reboot and I have to manually restart 2-3 times to get to a regular boot for it to boot properly. 
I am getting "a start job is running for /boot/efi" at the start and then several lines with journal checking and so on. 


I have looked on other threads people reporting the same issue and it seems to be caused by a /etc/fstab erroneous uuid. 
But I checked sudo blkid and /etc/fstab output and they seem to match.


$ sudo blkid
```

/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/loop7: TYPE="squashfs"
/dev/nvme0n1p1: LABEL="SYSTEM" UUID="40F6-B9B6" TYPE="vfat" PARTLABEL="EFI system partition" PARTUUID="96888f3a-32b4-4c29-a97a-0a2752032570"
/dev/nvme0n1p3: LABEL="Windows" UUID="AEB4F937B4F9029F" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="69a69e0a-938c-42ce-9226-be4c125ee402"
/dev/nvme0n1p4: LABEL="WinRE_DRV" UUID="E0B4F9BEB4F9976E" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="8c6c7f7d-4df1-40cc-a2b1-f0dc3013f00a"
/dev/nvme0n1p5: UUID="d4d0677a-3d4f-4c7c-96f4-66ed734a5a3d" TYPE="ext4" PARTUUID="4452c614-1e43-4141-91f7-46c009f9f177"
/dev/nvme0n1p6: UUID="a718d4e2-923d-4377-ad85-99693a258718" TYPE="swap" PARTUUID="9d01bb23-5e03-4854-802d-de338d04a749"
/dev/loop8: TYPE="squashfs"
/dev/loop9: TYPE="squashfs"
/dev/loop10: TYPE="squashfs"
/dev/loop11: TYPE="squashfs"
/dev/loop12: TYPE="squashfs"
/dev/loop13: TYPE="squashfs"
/dev/loop14: TYPE="squashfs"
/dev/loop15: TYPE="squashfs"
/dev/loop16: TYPE="squashfs"
/dev/loop17: TYPE="squashfs"
/dev/loop18: TYPE="squashfs"
/dev/loop19: TYPE="squashfs"
/dev/loop20: TYPE="squashfs"
/dev/loop21: TYPE="squashfs"
/dev/loop22: TYPE="squashfs"
/dev/loop23: TYPE="squashfs"
/dev/loop24: TYPE="squashfs"
/dev/loop25: TYPE="squashfs"
/dev/loop26: TYPE="squashfs"
/dev/loop27: TYPE="squashfs"
/dev/loop28: TYPE="squashfs"
/dev/loop29: TYPE="squashfs"
/dev/loop30: TYPE="squashfs"
/dev/loop31: TYPE="squashfs"
/dev/loop32: TYPE="squashfs"
/dev/loop33: TYPE="squashfs"
/dev/loop34: TYPE="squashfs"
/dev/loop35: TYPE="squashfs"
/dev/loop36: TYPE="squashfs"
/dev/loop37: TYPE="squashfs"
/dev/loop38: TYPE="squashfs"
/dev/loop39: TYPE="squashfs"
/dev/loop40: TYPE="squashfs"
/dev/loop41: TYPE="squashfs"
/dev/loop42: TYPE="squashfs"
/dev/loop43: TYPE="squashfs"
/dev/loop44: TYPE="squashfs"
/dev/loop45: TYPE="squashfs"
/dev/loop46: TYPE="squashfs"
/dev/loop47: TYPE="squashfs"
/dev/loop48: TYPE="squashfs"
/dev/loop49: TYPE="squashfs"
/dev/loop50: TYPE="squashfs"
/dev/nvme0n1: PTUUID="6b27bf65-2dd5-46ec-aaa7-7a757af74c48" PTTYPE="gpt"
/dev/nvme0n1p2: PARTLABEL="Microsoft reserved partition" PARTUUID="c8291373-5fbb-4874-b897-fc75feb2b9f6"



```





$ cat /etc/fstab 



```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/nvme0n1p5 during installation
UUID=d4d0677a-3d4f-4c7c-96f4-66ed734a5a3d /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/nvme0n1p1 during installation
UUID=40F6-B9B6  /boot/efi       vfat    umask=0077      0       1
# swap was on /dev/nvme0n1p6 during installation
UUID=a718d4e2-923d-4377-ad85-99693a258718 none            swap    sw              0       0



```

Does anyone know what is causing this and how to fix it?

---

### Post by oldfred on 2022-06-12
Also here:
[https://askubuntu.com/questions/1413730/a-start-job-is-running-for-boot-efi-1-30-min-slow-boot-time](https://askubuntu.com/questions/1413730/a-start-job-is-running-for-boot-efi-1-30-min-slow-boot-time)

You have a lot of snaps. Each takes time to load.

Post these:
systemd-analyze
systemd-analyze blame  # only need to post first lines or first page & please use code tags.

Please copy & paste the pastebin link to the Bootinfo summary report ( do not post report), do not run the auto fix till reviewed.Lets see details, use ppa version with your USB installer (2nd option) or any working install,  not Boot-Repair ISO
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)   &

---

### Post by user9820 on 2022-06-12
$ systemd-analyze
```
Startup finished in 11.643s (firmware) + 12.869s (loader) + 3.236s (kernel) + 14.426s (userspace) = 42.176s
graphical.target reached after 13.879s in userspace
```

$ systemd-analyze blame
    ```
1min 59.635s fstrim.service
          7.779s NetworkManager-wait-online.service
          3.367s plymouth-quit-wait.service
          2.023s [EMAIL="postfix@-.servic"]postfix@-.servic[/EMAIL]e
          1.628s snapd.service
          1.526s apparmor.service
          1.196s docker.service
          1.097s networking.service
          1.039s fwupd.service
          1.036s [EMAIL="systemd-backlight@backlight:intel_backlight.servic"]systemd-backlight@backlight:intel_backlight.servic[/EMAIL]e
           949ms plymouth-read-write.service
           903ms keyboard-setup.service


```

This is on a good boot (just 5-10 secs instead of the 1.30+ min one).

What do you mean by bootinfo? How do I run it?
Edit: I think you mean this? [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Unfortunately I don't have a USB flash disk easily accessible atm.

---

### Post by oldfred on 2022-06-12
You can run Boot-Repair's BIS report from any working current version Ubuntu, and many other Linux.

I think your top 2 are things I mentioned in the links I have posted in multiple places on slow boot issues.
I turn off network-manager & change grub to use noplymouth boot parameter in place of quiet splash.
[FONT=monospace][COLOR=#000000]GRUB_CMDLINE_LINUX_DEFAULT="noplymouth"

[https://ubuntuforums.org/showthread.php?t=2450783](https://ubuntuforums.org/showthread.php?t=2450783)
[https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499](https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499)
[https://ubuntuforums.org/showthread.php?t=2417453](https://ubuntuforums.org/showthread.php?t=2417453) & 
[https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392](https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392) & 
[https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html](https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html)

[https://askubuntu.com/questions/1284302/is-it-possible-to-make-ubuntu-20-04-boot-faster](https://askubuntu.com/questions/1284302/is-it-possible-to-make-ubuntu-20-04-boot-faster)
[https://askmeaboutlinux.com/2019/11/28/how-to-speed-up-boot-time-on-linux-if-it-boots-slowly/](https://askmeaboutlinux.com/2019/11/28/how-to-speed-up-boot-time-on-linux-if-it-boots-slowly/)

[/COLOR]Each loopmount is a snap application. I do not use snaps.
boot time cut in half by removing snaps, they since this post have improved snap boot somewhat
[https://ubuntuforums.org/showthread.php?t=2391341](https://ubuntuforums.org/showthread.php?t=2391341)




[/FONT]

---

### Post by user9820 on 2022-06-13
Every thread that I'm reading suggests it's a problem with /etc/fstab not having the right entries but my entries match the blkid output (as shown in the paste)! So I don't know what to fix. 

I'm not complaining about a "slow boot" actually, it starts in emergency mode everytime, one day something happened (didn't do anything different so I can't pinpoint the reason behind it) and boot now takes 1.30-3 mins instead of the normal 5secs. Something is definitely failing because it says a start job is running for dev-disk-by.. like in this thread: [https://askubuntu.com/questions/711016/slow-boot-a-start-job-is-running-for-dev-disk-by](https://askubuntu.com/questions/711016/slow-boot-a-start-job-is-running-for-dev-disk-by)

---

### Post by user9820 on 2022-06-13
[COLOR=#232629][FONT=-apple-system]Another thread with the same problem: [/FONT][/COLOR][askubuntu.com/questions/960790/&#8230;]("https://askubuntu.com/questions/960790/stuck-in-emergency-mode-and-nothing-works")[COLOR=#232629][FONT=-apple-system] The problem is that they seemed to be having mismatched /etc/fstab entries whereas I do not as far as I can see unless I'm missing something..[/FONT][/COLOR]

---

### Post by oldfred on 2022-06-13
Did you plug in an external drive that it then is having issue mounting?

Review log files, I get multiple warnings, but none are really important
sudo egrep -i 'warn|error' /var/log/*g

---

### Post by user9820 on 2022-06-13
Hm now that you mention it, I think I had my mobile phone (Android) plugged in the usb port when I rebooted. Other than that I don't remember anything else.
 Reviewed errors and warnings and there are loads of them but don't seem significant. Multiple nautilus errors etc. 

I think I will boot from a usb flash disk and fsck the root partition (or maybe the others are needed as well?) as this is something I saw being recommended in other threads when dealing with emergency mode (same as my situation).

---

### Post by user9820 on 2022-06-16
Damn I tried fsck -y against all partitions and it said the main root partition (ext4) is clean, but the problem persists.
It keeps going into emergency mode and I have to reboot 3-4 times to boot into normal mode and I don't know why.
journalctl -xb shows so many entries and I cannot know which warn/error are responsible (or if they're the cause).

It is driving me nuts, if anyone can help I would appreciate it!

---

### Post by web-user on 2022-06-18
Try to boot from another system using live USB system and check if there this error. If there aren't, it's the problem of Ubuntu. Otherwise, you should search for a general Linux solution

---

### Post by user9820 on 2022-06-19
What kind of error should I look for?

---

### Post by oldfred on 2022-06-19
Errors/Warnings:
sudo journalctl -b -p err
sudo egrep -i 'warn|error' /var/log/*g

I do get a page of errors/warnings, but none are critical. You just have to review them and search to see if issue is important.

---

