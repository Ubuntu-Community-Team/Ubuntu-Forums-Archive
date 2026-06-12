---
title: "GRUB partition problem"
date: 2013-02-06
forum: General Help
---

### Post by adm1n on 2013-02-06
During today's GRUB update, there was an error:

GRUB tries to install to /dev/sda1 (and doesn't give me any other options), but the root partition is mounted at /dev/root, so the installation fails. I continued without installing GRUB and tried to install it manually afterwards.

```
# grub-install /dev/root
/usr/sbin/grub-probe: warn: disk does not exist, so falling back to partition device /dev/sda1.
/usr/sbin/grub-probe: error: cannot stat `/dev/root'.
```What do I do now?

Booting a live CD is not an option, as this is a server with only CLI.

---

### Post by dino99 on 2013-02-06
sudo grub-install /dev/sda
sudo update-grub

---

### Post by adm1n on 2013-02-06
> **dino99 said:**
> sudo grub-install /dev/sda
sudo update-grub

```
# grub-install /dev/sda
/usr/sbin/grub-probe: warn: disk does not exist, so falling back to partition device /dev/sda1.
/usr/sbin/grub-probe: warn: disk does not exist, so falling back to partition device /dev/sda1.
/usr/sbin/grub-probe: error: cannot stat `/dev/sda'.
# update-grub
Generating grub.cfg ...
/usr/sbin/grub-probe: warn: disk does not exist, so falling back to partition device /dev/sda1.
/usr/sbin/grub-probe: warn: disk does not exist, so falling back to partition device /dev/sda1.
/usr/sbin/grub-probe: warn: disk does not exist, so falling back to partition device /dev/sda1.
/usr/sbin/grub-probe: warn: disk does not exist, so falling back to partition device /dev/sda1.
/usr/sbin/grub-probe: warn: disk does not exist, so falling back to partition device /dev/sda1.
/usr/sbin/grub-probe: warn: disk does not exist, so falling back to partition device /dev/sda1.
/usr/sbin/grub-probe: warn: disk does not exist, so falling back to partition device /dev/sda1.
/usr/sbin/grub-probe: warn: disk does not exist, so falling back to partition device /dev/sda1.
Warning: update-grub_lib is deprecated, use grub-mkconfig_lib instead
Found linux image: /boot/bzImage-3.2.13-xxxx-grs-ipv6-64
/usr/sbin/grub-probe: warn: disk does not exist, so falling back to partition device /dev/sda1.
/usr/sbin/grub-probe: warn: disk does not exist, so falling back to partition device /dev/sda1.
/usr/sbin/grub-probe: warn: disk does not exist, so falling back to partition device /dev/sda1.
/usr/sbin/grub-probe: warn: disk does not exist, so falling back to partition device /dev/sda1.
  No volume groups found
grub-probe: warn: disk does not exist, so falling back to partition device /dev/sda1.
umount: /var/lib/os-prober/mount: not mounted
done

```

Not sure if that's good, because it says "done", or bad, because of all the errors...

---

### Post by oldfred on 2013-02-06
I think dino's instructions only work once inside your install not from a liveCD. You can either manually boot if possible or use Supergrub. Otherwise from liveCD you have to mount Ubuntu (and /boot if separate partition) and then install grub to sda.

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB2
Grub2 info & full chroot version - also METHOD 3 - CHROOT:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

    
       #Comments are anything after the #, enter commands in terminal session
#Install MBR from liveCD/DVD/USB, Ubuntu install on sda1 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda1 if not correct:
sudo fdisk -l
#confirm that linux is sda1
[COLOR=DarkRed]sudo mount /dev/sda1 mnt[/COLOR]
[COLOR=DarkRed]sudo grub-install --root-directory=/mnt/ /dev/sda[/COLOR]
#  The above command should work but they now suggest this command for grub 1.99 with Natty 11.04 or later - uses boot not root.:
sudo grub-install --boot-directory=/mnt/boot /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

---

