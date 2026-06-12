---
title: "Building a RAID1 do I need a FakeRaid controller?"
date: 2008-04-10
forum: General Help
---

### Post by lil_elvis2000 on 2008-04-10
Hi all,
   I have a machine with a small primary drive which I want to put Xunbuntu on along with swap. Then I want to install two 500GB drives using a PCI SATA card - non-RAID and setup /home and SAMBA shares. This is my first delving into Linux BTW.

I have read through these forums and I can't see any advantage to using a fake-raid controller. It seems there are no drivers for most! I seems if I go with a generic PCI SATA controller and let Linux manage the RAID in software I will okay.

The machine is a 700Mhz Celeron, w/ 256 Ram (I'm going to upgrade the ram to 768 by getting 512M Dimm)
I think the primary drive is 8G - enough for Xubuntu with minimal software I think.

I'm wondering how I can get Xubuntu to boot to a command prompt and allow me to use X if I want to to cut down on cycles wasted on the GUI as well.

What issues will I encounter setting this up?

Thanks.

---

### Post by fjgaude on 2008-04-10
I can help with the raid issue, but not with the booting into a command line prompt. I'm sure the latter is easy to do if you understand what has to be done.

In the case of the two drives in raid1, you would use the software that is built-into the modern Ubuntu kernels, from Feisty through Hardy. You set up the software raid with a program that is called mdadm. It is in the repos. Install from there. Use **man mdadm** to get an idea of the power and flexibility of mdadm.

While at a command line, root, do this:

```
mdadm --create /dev/md1 --level=1 --raid devices=2 /dev/sda1 /dev/sdb1
```

After the array is built, check to see what it looks like:

```
mdadm --detail /dev/md1
```

After that, you would install the filesytem:

```
mkfs -t ext3 /dev/md1
```

Then you would mount the array at the mount point you have created:

```
mkdir /home/raid
```

Then mount:

```
mount /dev/md1 /home/raid
```

After all this is going well you can place a line in your /etc/fstab file that auto mounts the raid at boot time.

Let us know if you have any questions.

---

