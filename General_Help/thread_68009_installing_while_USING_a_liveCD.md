---
title: "installing while USING a liveCD?"
date: 2005-09-21
forum: General Help
---

### Post by urbandryad on 2005-09-21
I know you can't install FROM the LiveCD, but I wonder, once I've tried the LiveCD, and figured out how to format my disc, is there anyway to download the install and begin it WHILE using the Boot CD? Like, I download from the net, save it to the Hard drive somehow, and then install that, so that I don't need the LiveCD?

Thanks

---

### Post by urbandryad on 2005-09-22
[QUOTE=urbandryad]I know you can't install FROM the LiveCD, but I wonder, once I've tried the LiveCD, and figured out how to format my disc, is there anyway to download the install and begin it WHILE using the Boot CD? Like, I download from the net, save it to the Hard drive somehow, and then install that, so that I don't need the LiveCD?

Thanks[/QUOTE]
 no replies. No replies. *twiddles thumbs patiently*

---

### Post by tomchuk on 2005-09-25
You can bootstrap an ubuntu install from the LiveCD using debootstrap.

Something like this should get you close.
```

sudo mkdir -p /mnt/ubuntu
sudo monut /dev/hda1 /mnt/ubuntu # assuming you will install ubuntu on /dev/hda1 and it is already formatted.
sudo swapon /dev/hda2 # assuming swap partition is /dev/hda2
sudo debootstrap hoary /mnt/ubuntu http://archive.ubuntu.com/ubuntu/
# base system is downloaded and installed
sudo cp /etc/resolv.conf /mnt/ubuntu/etc/
sudo cp /etc/apt/sources.list /mnt/ubuntu/etc/apt/
sudo mount -t proc proc /mnt/ubuntu/proc
sudo mount -t sysfs sysfs /mnt/ubuntu/sys
sudo chroot /mnt/ubuntu /bin/bash
# you are now inside your new install
export LC_ALL=C
apt-get install ubuntu-base ubuntu-desktop
grub-install /dev/hda
exit
# back to your liveCD system
sudo umount /mnt/ubuntu/{sys,proc,}

```

You might also have to do fun stuff like manually set up /etc/fstab, install a kernel, etc...

---

