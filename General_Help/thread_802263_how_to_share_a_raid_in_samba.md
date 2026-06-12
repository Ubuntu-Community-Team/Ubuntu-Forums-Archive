---
title: "how to share a raid in samba"
date: 2008-05-21
forum: General Help
---

### Post by helsing on 2008-05-21
hello,

i have a hardware raid1 that i set-up in the bios and that i want to have as a samba share.

i can see the raid as one drive on my desktop. i called the raid 'bipack.' that's the name of hd icon i see on the desktop

but in the directory structure i see...
/media/sdb1/ - one of the raid drives
/media/sdc1/ - the other raid drive

in smb.conf is the share path
/media/bipack

or some combination of
/media/sdb1/ - one of the raid drives
/media/sdc1/ - the other raid drive


thanks!!

---

### Post by mrprefect on 2008-05-21
first things first, this doesn't sound like the raid is actually being run properly by the hardware. Is this just some onboard support for RAID? I've said on threads in here before this is generally not really hardware RAID but software RAID and a linux distro will not display a proper RAID array when configured this way.

You likely need to build a software RAID and then mount that.

What type of RAID did you make RAID0? RAID1? can you see the actually array anywhere on your system or just the individual drives?

---

### Post by helsing on 2008-05-21
thanks,

it is a hardware raid, RAID 1. 

again, i see the raid as one hd icon my desktop with name of the raid. when i drag an item into this icon i see the item in both

/media/sdb1
and
/media/sdc1
when i browse the file system

so _it seems_ the the RAID is working as a hardware raid. 

so what would the share path be for samba?

cheers.

---

### Post by mrprefect on 2008-05-21
well assuming the Hardware RAID is working... still seems a bit weird but you should just be able to do a 

mount

and see what it spits out, I'm not sure exactly what the device will be called since it is based on hardware. you may also want to try a 

dmesg

and see what is listed in there when your PC starts, it will likely name the RAID drive. 

once you find out where this drive is mounted then all you have to do is add it to you /etc/samba/smb.conf just like you would any other shared folder.

If you are unsure paste the results of those commands on here and I can see if I can see where it is listed.

As an example I will show you what I have:

```

# mount
/dev/md0 on /samba type ext3 (rw)



# This is for a RAID5 software
# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sdb1[0] sdd1[3] sde1[2] sdc1[1]
      1465151808 blocks level 5, 64k chunk, algorithm 2 [4/4] [UUUU]

unused devices: <none>




# cat /etc/samba/smb.conf
[storage]  #Storage Drive
        comment = Network Drive
        path = /samba
        guest ok = no
        write list = @users
        read list = @users



```

---

