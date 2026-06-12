---
title: "cannot install, remove or update anything! linux-image-3.19.0-25-generic problem!"
date: 2015-10-01
forum: General Help
---

### Post by robert-p1991 on 2015-10-01
Hello,
i was looking two days for this problem and tried to fix it. Now i dont know what i can do anymore! 
here is my problem... 
always when i try to install remove or even update something i get this error: 

```
/usr/sbin/grub-mkconfig: 35: /etc/default/grub: rcutree.rcu_idle_gp_delay=1: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.19.0-25-generic.postrm line 328.
dpkg: error processing package linux-image-3.19.0-25-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-3.19.0-25-generic
 linux-image-3.19.0-25-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

i tried to reinstall   linux-image-3.19.0-25-generic but i get the same error.
i tried to  dpkg --configure -a, tried to sudo apt-get update, sudo apt-get upgrade etc. nothing works.

---

### Post by v3.xx on 2015-10-01
Try purging with dpkg and then install

```
sudo dpkg -P linux-image- [COLOR="#FF0000"]and fill in the rest[/COLOR]
```

```
man dpkg
```

---

### Post by robert-p1991 on 2015-10-01
thank you for the answer.
i tried it and get this error again. 
```
sudo dpkg -P linux-image-3.19.0-25-generic
(Reading database ... 363251 files and directories currently installed.)
Removing linux-image-3.19.0-25-generic (3.19.0-25.26~14.04.1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-25-generic /boot/vmlinuz-3.19.0-25-generic
update-initramfs: Deleting /boot/initrd.img-3.19.0-25-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-25-generic /boot/vmlinuz-3.19.0-25-generic
/usr/sbin/grub-mkconfig: 35: /etc/default/grub: rcutree.rcu_idle_gp_delay=1: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.19.0-25-generic.postrm line 328.
dpkg: error processing package linux-image-3.19.0-25-generic (--purge):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-3.19.0-25-generic

```
i also tried to purge it with sudo dpkg -P --force-all but still the same.

---

### Post by v3.xx on 2015-10-01
What will this show?

```
grep -A1 "Package: linux-image" /var/lib/dpkg/status
```

---

### Post by robert-p1991 on 2015-10-01
ok i fixed it. 
i moved to ```
/var/lib/dpkg/info/
``` and delated there my linux-image-3.19.0-25-generic files
after that i was able to make ```
sudo dpkg --purge --force-all  linux-image-3.19.0-25-generic
```
Thank you for your support!

---

### Post by v3.xx on 2015-10-01
Well done :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

And welcome to the forums.

---

### Post by robert-p1991 on 2015-10-02
Oh i noticed, its still not realy solved. Now i have no linug-image-3.19xxxxxx package on my computer. when i try to install one, i get the same error as before :(

---

