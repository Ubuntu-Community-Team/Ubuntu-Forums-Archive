---
title: "Trying to increase the size of my boot partition, but I'm stuck at what to do."
date: 2017-02-19
forum: General Help
---

### Post by NoSalt on 2017-02-19
I have Xubuntu 14.04 installed on my server. I set this up several years ago, and didn't do a super job. I took the RHCT class back in 2005 and they suggested a boot  partition of 128MB, so that is what I made it. This is what my disk looked like when I was done:

```

/dev/sda1    ext4             128MB     /boot
/dev/sda2    linux-swap       2GB       swap
/dev/sda3    ext4             25GB      /
/dev/sda4    ext4             207GB     /home

```

I have since, of course, run out of room on my /boot  partition, so I need to increase the size. I used ```
sudo resize2fs /dev/sda4 206GB
``` to shrink the file system. Then I shrank the partition with GParted. I took about 1GB off so that I could extend my /boot partition. However, I can't seem to be able to extend the boot partition with GParted. This is where I need help. Will I be able to allocate that 1.25GB unallocated partion to /boot, or am I just stuck with it sitting on the end like it is? Here is a screenshot of my GParted.

[IMG]http://i.imgur.com/pWy3M4Z.png[/IMG]

Thanks for taking the time to read. Have a good day. :)

---

### Post by HereInOz on 2017-02-20
Hello,

I have never actually done this but I think your problem may be that you cannot edit the boot partition size while the partition is mounted and, if you have run GParted from within the Xubuntu system, that is probably the issue.  I shall be shot down in flames by others if I am wrong :-)  

You may have some luck in resizing the partition if you boot from a live DVD of Xubuntu, or a bootable CD of GParted.  That will leave the HDD unmounted and you may have more success.

Personally, I don't set up with a boot partition any more.  Just a /  and a /home and a swap.

Good luck.

---

### Post by plucky on 2017-02-20
> Will I be able to allocate that 1.25GB unallocated partion to /boot

No

The easiest thing for you to do is in Gparted, unmount and delete the swap partition and then you should be able to resize the boot partition into that space.

You can then recreate the swap partition in the space you created at the end of the drive.

You will then have to change the UUID in the /etc/fstab for the swap partition so that it is mounted at startup.

This has to be done offline in the Live DVD/USB environment.

Hope this makes sense.

---

### Post by igdfpm on 2017-02-20
Do you have a large number of "spare" kernels using up you existing /boot space? Trim a few old kernels will make the partition voodoo unnecessary.

You should be able to unmount /boot as it is done with once the machine is up and running

You may get more mileage (and future proofing) by removing your existing swap partition and extending boot into that freespace then resizing /home down and recreating /swap at the end of the drive.

You will have to update your /etc/fstab to reflect the partition changes which **must** be done, checked and rechecked **before** rebooting the machine.

---

### Post by gordintoronto on 2017-02-20
+1 for removing old kernels.

---

### Post by Impavidus on 2017-02-21
1. Your /boot partition is indeed tiny. It may have been enough in 2005, but now it barely holds two kernels.

2. The easiest solution is as plucky explained. +1 to that post.

3. Xubuntu 14.04 will reach end of life in two months. You'll have to upgrade or install a newer release. Maybe you want to seize the opportunity to get rid of the /boot partition altogether. Very few non-LVM systems use a /boot partition nowadays.

---

