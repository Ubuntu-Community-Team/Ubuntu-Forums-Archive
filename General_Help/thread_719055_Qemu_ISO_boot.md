---
title: "Qemu ISO boot"
date: 2008-03-08
forum: General Help
---

### Post by patrickaupperle on 2008-03-08
I tried this command

```
 sudo qemu -cdrom debian-live-etch-i386-gnome-desktop.iso
```

It started to boot. Then at mounting file system  it drops me at a busy box.
Please help. This also won't work with my pclos or hardykde4 images.

---

### Post by patrickaupperle on 2008-03-08
I tried -m 256 and a few other things. Any ideas would be appreciated.

and in PClOS, This comes up

---

### Post by patrickaupperle on 2008-03-09
I tried m -350 and it still stopped at the same spot.

---

### Post by patrickaupperle on 2008-03-09
I have now tried m -350 on all the isos. they all stop in the same spot

---

### Post by patrickaupperle on 2008-03-09
bump

---

### Post by patrickaupperle on 2008-03-11
bump

---

### Post by patrickaupperle on 2008-03-12
bump again?

Does anyone have any qemu experience?

---

### Post by tumnus on 2008-03-21
I was having the same issue, but I found a bug report on Launchpad with a workaround:

[https://bugs.launchpad.net/ubuntu/+source/bochs/+bug/123185](https://bugs.launchpad.net/ubuntu/+source/bochs/+bug/123185)

Apparently the QEMU BIOS that Gutsy ships with is faulty, but installing the one from Hardy fixes that:

[http://archive.ubuntu.com/ubuntu/pool/universe/b/bochs/bochsbios_2.3.6-2ubuntu1_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/b/bochs/bochsbios_2.3.6-2ubuntu1_all.deb)

After installing the package above, this command worked fine for me:

```
sudo qemu -m 512 -cdrom kubuntu-8.40-beta-desktop-i386.iso -boot d

```

However on my laptop (with a Core 2 Duo CPU) QEMU isn't able to use the CPU virtualisation via KVM for some reason and hence runs dog slow. So instead I use VirtualBox, in which you can setup a new VM instance without a hard drive and use then use the VM instance settings to make it mount the ISO you want to test and it runs full speed on my laptop.

---

### Post by patrickaupperle on 2008-03-22
> **tumnus said:**
> I was having the same issue, but I found a bug report on Launchpad with a workaround:

[https://bugs.launchpad.net/ubuntu/+source/bochs/+bug/123185](https://bugs.launchpad.net/ubuntu/+source/bochs/+bug/123185)

Apparently the QEMU BIOS that Gutsy ships with is faulty, but installing the one from Hardy fixes that:

[http://archive.ubuntu.com/ubuntu/pool/universe/b/bochs/bochsbios_2.3.6-2ubuntu1_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/b/bochs/bochsbios_2.3.6-2ubuntu1_all.deb)

After installing the package above, this command worked fine for me:

```
sudo qemu -m 512 -cdrom kubuntu-8.40-beta-desktop-i386.iso -boot d

```

However on my laptop (with a Core 2 Duo CPU) QEMU isn't able to use the CPU virtualisation via KVM for some reason and hence runs dog slow. So instead I use VirtualBox, in which you can setup a new VM instance without a hard drive and use then use the VM instance settings to make it mount the ISO you want to test and it runs full speed on my laptop.

Thank you for the reply, but I already switched to VirtualBox OSE:). It works great.:guitar:

---

