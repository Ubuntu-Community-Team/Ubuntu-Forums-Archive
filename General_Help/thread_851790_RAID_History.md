---
title: "RAID History"
date: 2008-07-07
forum: General Help
---

### Post by Kissell on 2008-07-07
Is there a way I can see the history of my RAID array?

I noticed all the drive lights flashing with steady heavy activity with no one using the system, so sure enough I did a "cat /proc/mdstat" and saw it was in the middle of rebuilding the array.  

Strange thing is, it was putting the array back into the state it was already in, so evidentially one of the disks got kicked out of the array at some point, and then it decided the disk was usable again and inserted it back in and rebuilt itself... 

But I would like to know more, like which disk, and why...  anyone know how can I find this!?

---

### Post by fjgaude on 2008-07-07
Next time use

```
sudo watch cat /proc/mdstat
```

and you can see the array working.

What does

```
sudo mdadm -D /dev/md0
```

show? Assuming your array is named md0. You'll see which drive or drives are acting up, if any. Then using the drive name you find what is its SN through this command:

```
sudo hdparm -i -v /dev/sda3
```

Then physcially you can find which drive has this SN and take it out, replace it, etc.

Let us know how you are doing.

---

### Post by Kissell on 2008-07-07
Thanks, I didn't know I could get the serial number from the hdparm command.  That will help a lot in the future.

But, the mdadm command just shows the state is clean, because everything is fine now.  What I want to know is why it wasn't clean a few days ago.  It seemingly broke itself and fixed itself, and that makes me nervous, because another failure while it takes a day to rebuild could be catastrophic.  

So it's clean now, but how do I see why it thought it wasn't clean a few days ago.  It's as if it decided one of the disks wasn't good, then it automatically decided it was good and used the one it previously thought was broken to fix itself.

---

### Post by fjgaude on 2008-07-07
It's hard to say what might have happened... all you can do is unmount the array and run **fsck** on the array. That will find anything weak and fix it, if possible.

---

