---
title: "Wifi Networks Not Displayed On Cloned Ubuntu"
date: 2023-12-29
forum: General Help
---

### Post by mikegreen8 on 2023-12-29
With the help of this forum I was able to clone my MBR ubuntu Desktop onto a GPT ESATA. 

I built the ubuntu partition on the ESATA as follows:

1. Formatted an ESATA as GPT, and allocated an EXT4 partition.

2. Did a LIVE ubuntu ISO USB install onto the ESATA EXT4 partition

3. Booting with a USB, I rsync my ubuntu Desktop onto the ESATA EXT4 partition. In order to ensure the ESATA would boot, I Excluded the following files in the rsync command (--exclude-from=FILE). Here is the contents of the Exclude file:
- /boot
- /etc/fstab
- /etc/default/grub
- /etc/default/grub.d/*
- /etc/grub.d/*
- /etc/init.d/grub*
- /etc/pm/sleep.d/*grub-common
- /etc/kernel/post*.d/zz-update-grub
- /lib/systemd/system/grub*
- /usr/bin/grub*
- /usr/lib/grub-legacy/*
- /usr/sbin/*grub*
- /usr/share/bash-completion/completions/grub*
- /usr/share/bug/grub-pc/*
- /usr/share/doc/grub-pc
- /usr/share/man/man8/grub*
- /usr/lib/grub/*
- /usr/sbin/grub*
- /usr/share/apport/package-hooks/*grub2*
- /usr/share/bug/grub-common/*
- /usr/share/grub/*
- /usr/share/man/man*/grub-*
- /usr/share/doc/grub-gfxpayload-lists/*
- /usr/share/grub-gfxpayload-lists/*
- /usr/share/bug/grub-pc-bin/*
- /usr/share/lintian/overrides/grub-pc-bin
- /usr/share/bug/grub2-common/*
- /usr/share/grub/default/grub*
- /usr/share/info/grub*

I BIOS disabled my ubuntu Desktop SATA and booted the ESATA ubuntu - looks and feels identical to my Desktop  -  Except:

Clicking on the Network Manager icon at the top right of the screen, only the wired connection is displayed. Even though there are 4 wifi networks available, none are displayed. There isn't even an option to enable/disable wifi networks - see attachment. The ethernet connection works just fine.



If I look at System Settings - Network,  only the Wired Connection is shown. 



```
ncmli r wifi on  (network manager turn wifi on)
sudo nmcli d      (shows NO wifi:)
DEVICE  TYPE      STATE      CONNECTION         
eno1    ethernet  connected  Wired connection 2 
```

No Wireless Networks displayed here:
```
sudo ls /sys/class/net     eno1  lo

```


/etc/netplan/01-network-manager-all.yaml looks like this:
> # Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManager

sudo rfkill list shows nothing is blocked.


I don't understand why a clone (less pertinent Boot files) differs from the original by not displaying/recognizing any of my 4 wireless networks. Booting back to my original Desktop the wireless networks are all there.

Any Ideas ??

Thanks,
M...

---

### Post by #&amp;thj^% on 2023-12-29
A fast check while you wait, is this installed
```
apt policy wpasupplicant
```
EDIT Also check Additional Drivers to see if they just did not make it through your rsync.

---

### Post by mikegreen8 on 2023-12-29
That was quick.

sudo apt policy wpasupplicant yielded the same results for both the Desktop & the ESATA - see attached.

Also - DIR /etc/netplan is empty on my Desktop.

Note:
I did a sort of dry run on the rsync. First I tried it on an empty EXT4 partition on the ESATA, and 72,318,016,795 bytes were transferred. Then, on the ESATA ubuntu partition - 70,741,914,278 bytes were transferred. I thought it strange that the 2 were not Exactly the same.

Thanks,
M....

---

### Post by #&amp;thj^% on 2023-12-29
I was hoping it would be easier but please run the wireless info script, which will gather information to help diagnose your system. You can run it using this command:
```

wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && \
chmod +x wireless-info && \
./wireless-info

```
Now paste back the link or attache the wireless-info.txt  it  gives you so we can try to help you.

---

### Post by mikegreen8 on 2023-12-29
Okay I did the wget twice - once on the ESATA and once on my Desktop. 

I'm having trouble attaching the 2 files - maybe I've exceeded the attachment sizes ?? I've only attached the ESATA wireless-info.txt

Hopefully this works for you.

Thanks,
M...

---

### Post by #&amp;thj^% on 2023-12-29
Please run:
```
ubuntu-drivers devices
```
See if there is driver for your WiFi

---

### Post by tea for one on 2023-12-29
From post 60 of the previous thread > Network controller: Broadcom Inc. and subsidiaries BCM4352 802.11ac Wireless Network Adapter
Have a look at the useful sticky here [https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)

---

### Post by mikegreen8 on 2023-12-29
ubuntu-drivers devices
**Desktop**
mg@ubuntu:~$ ubuntu-drivers devices
== /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/0000:04:01.0/0000:05:00.0 ==
modalias : pci:v000014E4d000043B1sv00001043sd0000855Cbc02sc80i00
vendor   : Broadcom Inc. and subsidiaries
model    : BCM4352 802.11ac Wireless Network Adapter
driver   : bcmwl-kernel-source - distro non-free



**ESATA**
mg@ubuntu:~$ ubuntu-drivers devices
== /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/0000:04:01.0/0000:05:00.0 ==
modalias : pci:v000014E4d000043B1sv00001043sd0000855Cbc02sc80i00
vendor   : Broadcom Inc. and subsidiaries
model    : BCM4352 802.11ac Wireless Network Adapter
driver   : bcmwl-kernel-source - distro non-free


They look identical to me - Wireless Network Adapter is there.

Wife bugging me - have to go to dinner. Will continue tomorrow.

Thanks,
M...

---

### Post by jeremy31 on 2023-12-29
Try in terminal ```
sudo apt install --reinstall bcmwl-kernel-source
```
Reboot

---

### Post by mikegreen8 on 2023-12-30
jeremy 31 "*sudo apt install --reinstall bcmwl-kernel-source*" WORKED!!

It was actually working prior to booting. Can you explain to me what the 'reinstall bcmwl-kernel-source' actually did, and why it was necessary?

I thank you so much.

M.....

---

### Post by jeremy31 on 2023-12-30
It just reinstalled the proprietary driver for the wifi
No idea why cloning a disk would cause an issue

---

### Post by #&amp;thj^% on 2023-12-30
> **mikegreen8 said:**
> jeremy 31 "[I]Can you explain to me what the 'reinstall bcmwl-kernel-source' actually did, and why it was necessary?

I thank you so much.

M.....
Ninja-ed by jeremey31 :)
Simply the driver for your card was left in a broken or corrupted state, the reinstall corrected it.

---

### Post by mikegreen8 on 2023-12-30
I'm back.

I've gone through all apps with success. Now the but. But I noticed that Virtual Machine is not working.

I will mark this post as solved and create a new post.

Thanks,
M...

---

