---
title: "Please HELP ME! Forgot to change fstab and it doesn't boot"
date: 2007-02-18
forum: General Help
---

### Post by october1917 on 2007-02-18
Please help me.

I reformated the /dev/hda4 partition from EXT3 into reiserfs but i foregot to change the fstab. (The first column in my fstab had the UUID and not the device name (i mean /dev/hd))

So when i reboot the system it cannot boot, neither while trying through Safe Mode.
It gives me console mode as root, but it doesn't accept any command.

I'm now connected using the Live CD, but it doesn't seem to can do something.

Is there a way to change the reaf fstab using the Live CD?

What to do??????:confused:

---

### Post by moshuptrail on 2007-02-18
From the Live CD you should be able to mount the drive where your fstab is located and then fix it.

---

### Post by solar george on 2007-02-18
Just delete the whole "uuid=3218ujdio2rejlk" bit and replace it with /dev/hda4.

I hope that wasn't your root (/) partition because if it is you have just wiped all of the information off it.

---

### Post by october1917 on 2007-02-18
> From the Live CD you should be able to mount the drive where your fstab is located and then fix it.Yes, that's what i want to do, but i cannot find where is the REAL fstab. Because when you boot from Live CD is creates a virtual fstab, which was no relationship with the real one.

Also, i cannot browse my filesystem using the live CD, because it says > **Unable to mount the selected volume.**

error: device /dev/hda4 is not removable
error: could not execute pmount


@Solar George i know what to do, but i dno't know how... :(

---

### Post by october1917 on 2007-02-18
Alright. I managed to mount the / partition, so i found the real fstab. But i cannot change it. I do not have permission.

Is there a way to gain root access from Live CD?

---

### Post by solar george on 2007-02-18
just use sudo - you shouldn't need a password.

---

### Post by chinese_ys on 2007-02-18
why you guys always use live cd? try alternative one to heal the system. YOu can re-install the grub in the recovering, and it should let you boot the new drive.

---

### Post by mcduck on 2007-02-18
> **chinese_ys said:**
> why you guys always use live cd? try alternative one to heal the system. YOu can re-install the grub in the recovering, and it should let you boot the new drive.

Because it's a completely different CD, and everybody might not have it? Or because live-CD gives you a nice GUI so you can read instructions from web while doing the needed fixes. Everybody doesn't love working from CLI (I do :))

---

### Post by solar george on 2007-02-18
> try alternative one to heal the system.
Some people find the text based installer too intimidating - and if you can fix it fine from the live cd why make people use the alternate cd.

> YOu can re-install the grub in the recovering,

This won't fix it if the fstab is the problem.

---

### Post by cmertayak on 2007-02-18
> **october1917 said:**
> Alright. I managed to mount the / partition, so i found the real fstab. But i cannot change it. I do not have permission.

Is there a way to gain root access from Live CD?

As solar george said, just use "sudo" without passwd. Doesn't it work?

```
sudo vim fstab
```

---

### Post by akshaysrinivasan on 2007-02-18
If the drive which you reformatted wasn't the root drive (obviously!) ,there are chances that the drive designation of your root partition has changed,it is always better to confirm that with gparted.

---

### Post by october1917 on 2007-02-18
Alright. I fixed it.

Thank you. I mounted the / partition to the /media of the virtual CD's filesystem  and the disks to /media/media

Then i changed the /media/etc/fstab and finished.

Thank you.

---

