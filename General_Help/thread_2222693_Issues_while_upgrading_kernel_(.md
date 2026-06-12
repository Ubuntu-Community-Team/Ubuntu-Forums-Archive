---
title: "Issues while upgrading kernel :("
date: 2014-05-07
forum: General Help
---

### Post by michael102 on 2014-05-07
Hello,

I wanted to play with [www.docker.io]("http://www.docker.io"), its installation page said I needed to have kernel 3.8 [http://docs.docker.io/installation/ubuntulinux/](http://docs.docker.io/installation/ubuntulinux/) 

My VPS is running Ubuntu 12.04 (kernel 2.6.32-042stab084.17), I tried to upgrade to linux-image-3.8.0-39-generic and it failed. 
I tried to fix it but I keep receiving errors:

```

$sudo apt-get install -y linux-image-3.8.0-39-generic 

Reading package lists... Done
Building dependency tree
Reading state information... Done
linux-image-3.8.0-39-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 48 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up linux-image-3.8.0-39-generic (3.8.0-39.58~precise1) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
The link /initrd.img is a dangling linkto /boot/initrd.img-3.8.0-39-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.8.0-39-generic /boot/vmlinuz-3.8.0-39-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.8.0-39-generic /boot/vmlinuz-3.8.0-39-generic
update-initramfs: Generating /boot/initrd.img-3.8.0-39-generic
E: /usr/share/initramfs-tools/hooks/fixrtc failed with return 1.
update-initramfs: failed for /boot/initrd.img-3.8.0-39-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.8.0-39-generic.postinst line 1010.
dpkg: error processing linux-image-3.8.0-39-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-3.8.0-39-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I believe its concurrently in "half-configured" state:

```

dpkg -l linux-image-3.8.0-39-generic
iF  linux-image-3.8.0-39-generic

```

I read that I should run dpkg --configure, but it failed too:

```

$ sudo dpkg --configure -a

Setting up linux-image-3.8.0-39-generic (3.8.0-39.58~precise1) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
The link /initrd.img is a dangling linkto /boot/initrd.img-3.8.0-39-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.8.0-39-generic /boot/vmlinuz-3.8.0-39-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.8.0-39-generic /boot/vmlinuz-3.8.0-39-generic
update-initramfs: Generating /boot/initrd.img-3.8.0-39-generic
E: /usr/share/initramfs-tools/hooks/fixrtc failed with return 1.
update-initramfs: failed for /boot/initrd.img-3.8.0-39-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.8.0-39-generic.postinst line 1010.
dpkg: error processing linux-image-3.8.0-39-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-3.8.0-39-generic

```

I also tried apt-get install -f but it failed with similar error :(
Then I tried purging the package, it was successful but apt-get install gave me the same error when I retried :(

---

### Post by deadflowr on 2014-05-07
What happens if you try
```
sudo apt-get -f install
```

or perhaps a quick clean and reload
```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

---

### Post by michael102 on 2014-05-07
Thanks for the reply deadflowr, 

EDIT: see below

---

### Post by michael102 on 2014-05-07
Actually, it looks like rebooting after running those apt-get commands may have done the trick. :) :)

Now it shows linux-image-3.8.0-39-generic as being installed. 

```

$:~# dpkg --list | grep linux-image
ii  linux-image-3.8.0-39-generic         3.8.0-39.58~precise1                Linux kernel image for version 3.8.0 on 64 bit x86 SMP

```

However, why does uname -r still report the old kernel (2.6.32-042stab084.17) ?
```

$:~# uname -r
2.6.32-042stab084.17

```


/lib/modules/ shows:
```

drwxr-xr-x 2 root root 4096 Dec 27 12:43 2.6.32-042stab079.6
drwxr-xr-x 2 root root 4096 May  7 16:44 2.6.32-042stab084.17
drwxr-xr-x 4 root root 4096 May  7 16:28 3.8.0-39-generic

```

---

