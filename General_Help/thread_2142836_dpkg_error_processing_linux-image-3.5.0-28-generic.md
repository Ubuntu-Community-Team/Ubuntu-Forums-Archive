---
title: "dpkg: error processing linux-image-3.5.0-28-generic"
date: 2013-05-06
forum: General Help
---

### Post by sudonohup on 2013-05-06
I have  Ubuntu Server 12.04.2 LTS installed on a server. After I run


        ```
apt-get update & apt-get upgrade & apt-get dist-upgrade
```


My kernel version has been changed to `linux-image-3.5.0-28-generic`. (The original one is `linux-image-3.5.0-23-generic`)


However, after the above operations, when I run `apt-get upgrade` or `apt-get autoremove` or `apt-get install ntp`(or other package), the shell prints the following error message:




    ```
root@network:/boot# apt-get upgrade
    Reading package lists... Done
    Building dependency tree       
    Reading state information... Done
    0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
    3 not fully installed or removed.
    After this operation, 0 B of additional disk space will be used.
    Do you want to continue [Y/n]? y
    Setting up linux-image-3.5.0-28-generic (3.5.0-28.48~precise1) ...
    Running depmod.
    update-initramfs: deferring update (hook will be called later)
    Examining /etc/kernel/postinst.d.
    run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.5.0-28-generic /boot/vmlinuz-3.5.0-28-generic
    run-parts: executing /etc/kernel/postinst.d/dkms 3.5.0-28-generic /boot/vmlinuz-3.5.0-28-generic
    run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.5.0-28-generic /boot/vmlinuz-3.5.0-28-generic
    update-initramfs: Generating /boot/initrd.img-3.5.0-28-generic
    run-parts: executing /etc/kernel/postinst.d/update-notifier 3.5.0-28-generic /boot/vmlinuz-3.5.0-28-generic
    run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.5.0-28-generic /boot/vmlinuz-3.5.0-28-generic
    /usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
    run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
    Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.5.0-28-generic.postinst line 1010.
    dpkg: error processing linux-image-3.5.0-28-generic (--configure):
     subprocess installed post-installation script returned error exit status 2
     E: Sub-process /usr/bin/dpkg returned an error code (1)

```



Does any one have any ideas to get this working? (I don't even know what's wrong with that?) Or how to roll back to the previous Linux kernel version?(Since there is no problem for the previous `linux-image-3.5.0-23-generic` version.) Thanks!

---

### Post by sudonohup on 2013-05-06
Through Google, I have just found what's wrong with that.


Actually, my problem is the same as


[http://ubuntuforums.org/showthread.php?t=1553405](http://ubuntuforums.org/showthread.php?t=1553405)


since my server is also a diskless NFS-booting server...


The solution for my problem is simple:
[http://jeffwelling.github.io/2011/08/29/Diskless-Upgrade-Problem.html](http://jeffwelling.github.io/2011/08/29/Diskless-Upgrade-Problem.html)


Just comment out `exec update-grub` in the file `/etc/kernel/postinst.d/zz-update-grub`.


(NFS booting does not need grub.)


Thanks!

---

