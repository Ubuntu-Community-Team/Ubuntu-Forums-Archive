---
title: "Need to enlarge boot partitions"
date: 2023-09-01
forum: General Help
---

### Post by c7890 on 2023-09-01
Hello,

Here's a screenshot of my partitions using gparted on Ubuntu 20. I keep getting errors about my boot partition being out of space. What should I do to enlarge my boot partition(s)? 

I "sudo apt autoremove" after every upgrade but that's no longer sufficient.

Thanks in advance!


[IMG]https://imgur.com/a/VldgLBx[/IMG]

[https://imgur.com/a/VldgLBx](https://imgur.com/a/VldgLBx)

---

### Post by oldfred on 2023-09-01
Those sizes look reasonable.
What do these show?
lsblk -e 7 -o name,fstype,size,fsused,label,UUID,mountpoint
ll /mnt/boot  # I may have ll as a version of ls, not sure if default or not.
My .bashrc has this:
alias ll='ls -alF'

---

### Post by Dennis N on 2023-09-02
Even with three kernels, your sda5 should be around 300 MB. Current size is 620 MB. Check for older kernels you could remove.

---

### Post by c7890 on 2023-09-02
```
NAME FSTYPE   SIZE FSUSED LABEL UUID                                   MOUNTPOINT
sda         931.5G                                                     
&#9500;&#9472;sda1
&#9474;    vfat     512M     4K       3C26-ED01                              /boot/efi
&#9500;&#9472;sda2
&#9474;               1K                                                     
&#9500;&#9472;sda5
&#9474;    ext4     731M 591.5M       5426c271-9ffa-47b5-90e0-439546d4d438   /boot
&#9492;&#9472;sda6
     crypto 930.3G              b092eaf0-1157-48e8-9f9c-4624a8011bbd   
  &#9492;&#9472;sda6_crypt
     LVM2_m 930.3G              QJNrFS-fevI-itE9-vHW8-e06I-t87F-pASVVc 
    &#9500;&#9472;vgubuntu-root
    &#9474;  ext4   929.3G 298.2G       0b251ad8-f23a-415e-88d4-1a1cbdf913fd   /
    &#9492;&#9472;vgubuntu-swap_1
       swap     976M              75c82ca0-aef6-4e0f-8060-1f895c799410   [SWAP]
sr0          1024M  
```

As for the 2nd command, I tried a few variations but I received this message each time: "ls: cannot access '/mnt/boot': No such file or directory"

---

### Post by c7890 on 2023-09-02
> **Dennis N said:**
> Even with three kernels, your sda5 should be around 300 MB. Current size is 620 MB. Check for older kernels you could remove.

I'm not sure how to do that. Here's what I just attempted:

```
sudo apt autoremove --purge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up initramfs-tools (0.136ubuntu6.7) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.136ubuntu6.7) ...
update-initramfs: Generating /boot/initrd.img-5.15.0-82-generic
I: The initramfs will attempt to resume from /dev/dm-2
I: (/dev/mapper/vgubuntu-swap_1)
I: Set the RESUME variable to override this.
Error 24 : Write error : cannot write compressed block 
E: mkinitramfs failure cpio 141 lz4 -9 -l 24
update-initramfs: failed for /boot/initrd.img-5.15.0-82-generic with 1.########..........................................] 
dpkg: error processing package initramfs-tools (--configure):
 installed initramfs-tools package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

EDIT: I followed this guide: [https://linuxconfig.org/how-to-remove-old-kernels-on-ubuntu](https://linuxconfig.org/how-to-remove-old-kernels-on-ubuntu) 
...and removed the kernels that I'm not currently using. 

Now my /dev/sda5 is 48% used. Does that sound right/acceptable? If so, I'll mark this is solved.

---

### Post by yancek on 2023-09-02
Partitions on Linux will generally give that full error when they are 90-95% full while your showed only 85% so I don't know why you got it.  I don't use LVM so I'm not familiar but 48% full should not be a problem.  Regularly remove old kernel as you update to avoid this problem.

---

### Post by c7890 on 2023-09-02
Ah - I wasn't removing old kernels - that was my problem. I'll remove them going forward.

Is there a way to remove the old ones automatically? My guess is that this is what happens normally but I may have disrupted that process. When I first installed 20.04 I had a WiFi USB dongle which required a kernel modification to install the drivers for the dongle. Is that what threw me off?

Thanks to all - marked as solved.

---

### Post by Dennis N on 2023-09-02
> **c7890 said:**
> Ah - I wasn't removing old kernels - that was my problem. I'll remove them going forward.

**Is there a way to remove the old ones automatically?** My guess is that this is what happens normally but I may have disrupted that process. When I first installed 20.04 I had a WiFi USB dongle which required a kernel modification to install the drivers for the dongle. Is that what threw me off?

Thanks to all - marked as solved.

You should use **Software Updater** for your updates. It will offer to remove the oldest kernel packages after any transaction involving a kernel update.

---

### Post by c7890 on 2023-09-02
> **Dennis N said:**
> You should use **Software Updater** for your updates. It will offer to remove the oldest kernel packages after any transaction involving a kernel update.

Thanks!

---

