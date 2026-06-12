---
title: "Best way to add hard drives to file server?"
date: 2008-01-28
forum: General Help
---

### Post by Eluzion on 2008-01-28
I have a file server setup for my home network. The computer I'm running the file server on has two hard drives, only one of which is actually being used with Ubuntu installed on it. I have Netatalk setup since most computers in the house are Macs. Everything is working great.

I'd like to add the second hard drive to increase the storage capacity of the file server but I was wondering if there was such a way to do it so Ubuntu would use both hard drives as one? If so, any tutorials or pointers on how to go about achieving this?

---

### Post by colo on 2008-01-28
Yep, there is (resp. there are ways to do so). Some terms to feed into Google:

mdadm, md, jbod, lvm2, evms

Have fun! :)

---

### Post by Eluzion on 2008-01-28
Is there any specific one you would recommend for a home file server? ;) I'd like one I can add additional hard drives in the future, painlessly (if that's possible).

---

### Post by Eluzion on 2008-01-28
It appears LVM is the best choice, which I am running now. However, trying to add a second hard drive and expanding the overall size of the partition has been quite the task... no clue if I have it working correctly. ;) Been trying to follow a dozen different tutorials.

---

### Post by PilotJLR on 2008-01-28
Just keep in mind that with LVM on disks not being in a RAID array, then you can pretty much count on losing data on ALL disks if any one should fail...
So adding more disks actually increases your data loss risk.

The perfect setup would be LVM on top of hardware RAID... but that would require buying a hardware raid card.

---

### Post by Eluzion on 2008-01-28
Yeah, I'm aware of that. The computer I'm using has an onboard RAID controller so I'll eventually setup a mirror or something. This is more for just learning for now.

Do you perhaps know any good tutorials on expanding an existing LVM partition? For example, I installed Ubuntu on one 80GB hard drive and have another 80GB hard drive I'd like to use to extend the first partition. I've been reading up on several different tutorials and think I got it working but I get this:

# pvscan
  PV /dev/sda5   VG server1   lvm2 [74.29 GB / 0    free]
  PV /dev/sdb1   VG server1   lvm2 [74.53 GB / 5.86 GB free]
  Total: 2 [148.82 GB] / in use: 2 [148.82 GB] / in no VG: 0 [0   ]

I have no clue why it's saying 0 free and 5.86 free? Both hard drives are nearly empty.

EDIT:
Nevermind. I think I did it right.

#df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/server1-root
                      134G  5.8G  122G   5% /
varrun                506M  116K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M   88K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
/dev/sda1             236M   24M  200M  11% /boot

---

### Post by _sAm_ on 2008-01-28
I am about to do the same. Are the «onboard RAID controlle» fake raid(1)?. I have that on my board, but will rather use software raid that comes with Linux. From what I have read it is better then fake raid.

So, I will use RAID0 on all my disk(only 2 disk so far), and the use LVM on top, so I can increase the storage later when needed(and also better speed(3). I will use EVMS(2) to handle both the RAID and LVM. This program gives you GUI, I am not so good with the terminal. Fedora has a nice program for this called «Logical Volume Manager», but it is not in the repo for Ubuntu – so I will try EVMS. 

The good part is that I can add raid and VLM  later, without the need to install Ubuntu again:-D 



1: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
2: [http://evms.sourceforge.net/](http://evms.sourceforge.net/)
3: [http://www.linux.com/feature/124256](http://www.linux.com/feature/124256)

---

### Post by PilotJLR on 2008-01-28
Your server1-root LV is nearly empty?? It is showing as 122GB is used. If you have that much stored, then it sure looks good! But if there is nothing there, then something is amiss.

---

