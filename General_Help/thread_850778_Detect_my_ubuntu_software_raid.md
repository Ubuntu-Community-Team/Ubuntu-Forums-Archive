---
title: "Detect my ubuntu software raid?"
date: 2008-07-05
forum: General Help
---

### Post by Squish on 2008-07-05
I had a Linux software raid 0 mounted as /home/Videos

I reinstalled my ubuntu however, and now I cannot detect it anymore. 
How do I find it again. 

It was empty, so if I cant, can someone tell me how to create a raid 0 array with a ubuntu 8.04.1 i386 live desktop cd?

Thanks

---

### Post by fjgaude on 2008-07-06
Well, software raid can always be setup after you have the OS installed, using a program called **mdadm**. It is not loaded by default. Please don't make a raid0 array the boot drive. Use another drive to boot, best practice. <smile>

You have your OS running, right? Yes!

```
sudo apt-get install mdadm
```

Make sure you have tagged your two drives as "fd", Linux raid autodetect.

Now do a create like so:

```
sudo mdadm --create /dev/md0 --level=0 --raid-devices=2  /dev/yyy /dev/sdxxx 
sudo mkfs -t ext3 /dev/md0
sudo watch cat /proc/mdstat
```

When the array-build is finished you can mount it, and then put a line in the fstab file to auto mount on bootup.

You will likely find this link useful:

[http://shsc.info/LinuxSoftwareRAID](http://shsc.info/LinuxSoftwareRAID)

If you need help, let us know.

---

