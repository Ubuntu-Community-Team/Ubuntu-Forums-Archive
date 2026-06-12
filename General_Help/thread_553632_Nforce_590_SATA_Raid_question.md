---
title: "Nforce 590 SATA Raid question"
date: 2007-09-18
forum: General Help
---

### Post by c0rrupts3ct0r on 2007-09-18
I have a Nvidia Nforce 590 SATA Asus board, the p5n32-sli premium. I run 2 150 GB Raptors in a raid 0 with the NVIDIA RAID software on the motherboard. I am trying to get the SATA RAID recognizable in Ubuntu 7.04. I had activated DMRAID and tried to mount the RAID into my home/windows folder but it says it is busy and will not mount. When i go to that directory it is empty. Can anyone help me? I may be doing something wrong. I had followed a guide i found on the internet with everything that was said but it just won't mount. If i open up GpartEd with the nvidia device in question it shows up as a RAID but i just dont know how to mount it from there. 

Is there something I am doing wrong?

I also have 2 320 gig sata drives on the Nvidia RAID controller but those aren't raid, there seperate, and then a 200 gig sata drive that ubuntu is installed on.  I just want to be able to see the RAID partitions in Ubuntu and move some data over.

---

### Post by fjgaude on 2007-09-18
What does sudo dmraid -tay show?

Did you do something like:

sudo mkfs -t ext3 /dev/mapper/nv_ahahbhbjaddg
sudo dmraid -s
mkdir /raid
sudo mount -t ext3 /dev/mapper/nv_ahahbhbjaddg /raid

Where the nv_ahahbhbjaddq is your listed raid device?

frank
[http://yantrayoga.typepad.com/noname/](http://yantrayoga.typepad.com/noname/)

---

### Post by c0rrupts3ct0r on 2007-09-18
> **fjgaude said:**
> What does sudo dmraid -tay show?

Did you do something like:

sudo mkfs -t ext3 /dev/mapper/nv_ahahbhbjaddg
sudo dmraid -s
mkdir /raid
sudo mount -t ext3 /dev/mapper/nv_ahahbhbjaddg /raid

Where the nv_ahahbhbjaddq is your listed raid device?

frank
[http://yantrayoga.typepad.com/noname/](http://yantrayoga.typepad.com/noname/)
sorry i did not get back sooner.

here is the output you requested: 

nvidia_icaceacc: 0 586093312 striped 2 128 /dev/sda 0 /dev/sdb 0
nvidia_icaceacc1: 0 293041602 linear /dev/mapper/nvidia_icaceacc 63
nvidia_icaceacc2: 0 293048320 linear /dev/mapper/nvidia_icaceacc 293042176

i want to be able to access the NTFS partitions that are on the Stripe, Windows XP and Vista.

if i do the mkfs will it wipe the existing partitions off of the hard drive?

---

### Post by fjgaude on 2007-09-19
> **c0rrupts3ct0r said:**
> sorry i did not get back sooner.

here is the output you requested: 

nvidia_icaceacc: 0 586093312 striped 2 128 /dev/sda 0 /dev/sdb 0
nvidia_icaceacc1: 0 293041602 linear /dev/mapper/nvidia_icaceacc 63
nvidia_icaceacc2: 0 293048320 linear /dev/mapper/nvidia_icaceacc 293042176

i want to be able to access the NTFS partitions that are on the Stripe, Windows XP and Vista.

if i do the mkfs will it wipe the existing partitions off of the hard drive?

Yes, I think it will, so don't. Now I see that you are wishing to do things I've never done.

Since dmraid didn't show your striped array as a md value mapped what do we do? Make sure you have installed ntfs-3g; you can use Synaptic or apt-get, it's in the Ubuntu repos.

I know you will need to mount the array at bootup using something like this in fstab:

```
/dev/mapper/nvidia_icaceacc    /media/raid    ntfs-3g    default,locale=en_US.utf8   0   0
```

Or you can manually mount the striped array like so:

```
sudo mount -t ntfs-3g /dev/mapper/nvidia_icaceacc /mount_point
```

The issue here is that the filesystem is unknown to the kernel, so we make it known. Yes.

Your mount point can be whatever you wish, e.g., /media/raid or /media/Windows or even /home/raid or /srv if you have created a directory called /srv off of /.

If there is anyway to backup the data you have on your strip, please do. I tell you I've never done this before but it should work. Brave souls may try it. <smile>

frank
[http://yantrayoga.typepad.com/noname/](http://yantrayoga.typepad.com/noname/)

---

### Post by c0rrupts3ct0r on 2007-09-19
that worked perfectly. thank you.. one more question. what file do i put it in to make it mount on startup. is it the /etc/fstab file? i may try that just to see if that works

thanks for your help
Christopher

---

### Post by c0rrupts3ct0r on 2007-09-20
just wanted to say i added the lines to /etc/fstab and i can access both partitions now. thanks for your help.

I have used other distros, SuSe, Mandriva, Redhat, and Fedora, but i like ubuntu the best. after you get all the drivers in and the programs in that you like its really easy to use.

---

### Post by fjgaude on 2007-09-20
Wonderful to get success...have lots of fun with Ubuntu... glad I could help.

frank
[http://yantrayoga.typepad.com/noname/](http://yantrayoga.typepad.com/noname/)

---

