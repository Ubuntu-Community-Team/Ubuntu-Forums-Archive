---
title: "Problem Booting most recent kernel"
date: 2022-03-05
forum: General Help
---

### Post by rsteinmetz70112 on 2022-03-05
I am upgrading one of my computers it has 2 mdadm ARRAYs whihc contail LVs.

Changing out some hardware am droping into initram shell with an error message that reads:
only give one device per array line.

there is also a reference to /scripts/init-premount

I've looked for the script in /etc/initramfs-tools/scripts and in /usr/share/initramfs-tools/scripts. There is nothing there.

I can boot into a live session and my md arrays are available.

Here is my mdadm.conf.

```
# cat mdadm.conf
ARRAY /dev/md/1 level=raid1 num-devices=2 metadata=1.2 name=romulus:1 UUID=f83e40b4:f7d446b4:1891663f:f94554d2
   devices=/dev/sdb1,/dev/sdc1
ARRAY /dev/md/0 level=raid1 num-devices=2 metadata=1.2 name=romulus:0 UUID=bcd25e93:034c9fbf:faeeec18:28341fb7
   devices=/dev/sdd1,/dev/sde1
```

---

### Post by rsteinmetz70112 on 2022-03-06
I've done some more investigating and discovered the issue only affects one kernel, the latest -5.4.0-89-generic. I can boot with an alternate kernel p-5.4.0-88-generic.
I have found a script in /usr/share/initramfs/script/local-top named assemble arrays. This is it;
```
#! /bin/sh

/sbin/mdadm -A --scan
```

It is dated  Jul 14  2010, obviously a hold over from something long ago. I do recall once having issues with getting mdadm and lvm2 to work properly during boot, they were not activated soon enough.
Another virtually identical computer with the mdadm/lvm2 setup works just fine but does not contain that file. 

Something must have changed between the last two kernels.

---

### Post by rsteinmetz70112 on 2022-03-07
I've been investigation and tried a lot of things to fix it including messing with the various initramfs-tools scripts. Updating grub and updating initramfs 

I have another computer which is very similar to the problematic one, it works fine. I noticed it has the following kernels

>  vmlinuz-5.4.0-100-generic
 vmlinuz-5.4.0-96-generic
 vmlinuz-5.4.0-99-generic

Oddly on this one when I run:

```
 # apt autoremove
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

It doesn't offer to remove one of the old kernels

On the problematic computer the kernels listed are older
> 
vmlinuz-5.4.0-88-generic
vmlinuz-5.4.0-89-generic


I don't get prompted to upgrade the kernel.

It looks like the the latest generic kernel for 20.04 is 5.4.0.100.104 so one machine is more or less up to date. I know I can install the hwe stack and get it 5.13.0.30.33 but I concerned that something else is wrong.

---

### Post by rsteinmetz70112 on 2022-03-08
I've now run:

```
# apt install --dry-run linux-generic
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following additional packages will be installed:
  amd64-microcode intel-microcode iucode-tool linux-headers-5.4.0-100
  linux-headers-5.4.0-100-generic linux-headers-generic
  linux-image-5.4.0-100-generic linux-image-generic
  linux-modules-5.4.0-100-generic linux-modules-extra-5.4.0-100-generic
  thermald
Suggested packages:
  linux-doc | linux-source-5.4.0 linux-tools
The following NEW packages will be installed:
  amd64-microcode intel-microcode iucode-tool linux-generic
  linux-headers-5.4.0-100 linux-headers-5.4.0-100-generic
  linux-headers-generic linux-image-5.4.0-100-generic linux-image-generic
  linux-modules-5.4.0-100-generic linux-modules-extra-5.4.0-100-generic
  thermald
0 upgraded, 12 newly installed, 0 to remove and 2 not upgraded.

```

That indicates it will install the latest 5.4.0-100 kernel and files.

---

### Post by rsteinmetz70112 on 2022-03-09
OK I've run **# apt install linux-generic** it installed kernel 5.4.0-104 so I'll do some testing and see if my issues is resolved, when I can take it down.

---

### Post by rsteinmetz70112 on 2022-03-12
This is sort of solved. 
I changed the grub menu to show during boot, allowing me to select a working kernel. 
I then installed the most recent kernel 5.4.0.104 The computer now boots properly and If I don't intervene it automatically boots the 5.4.0-104 kernel.
It still won't boot the 5.0.4-89 kernel but I can select and boot the 5.0.4.88 kernel
I don't know if the kernel update is working correctly. I'll wait until the next update and see if it'll update. If so I should be able to **apt autoremove** and be back to normal.
I'm going to make this one solved.

---

