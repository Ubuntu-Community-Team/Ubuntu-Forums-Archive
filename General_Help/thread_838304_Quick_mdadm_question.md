---
title: "Quick mdadm question"
date: 2008-06-23
forum: General Help
---

### Post by Muntted on 2008-06-23
I recently lost a hard drive in a raid 5 setup. I didnt "remove" the device from mdadm's setup. However I did remove the drive and replace it with another. 

Now that I have added a new drive im getting this:
...
active raid5 sdb1[3] sdc1[1] sdd1[0]
...
I am missing xxx1[2]. Im presuming that this is the drive I didnt 'remove' from mdadm before actually removing it from the system. Is there anything wrong with this? Any way to fix it?

---

### Post by fjgaude on 2008-06-23
I'm not sure if there is anything wrong with what you have, and can't say how to "fix" it. I do know that md keeps everything about an array in the UUID for the array, which is the same as the UUID for each drive in the array.

You might try:

```
sudo mdadm -D /dev/md[nn]
```

and see what mdadm is saying about the mounted array. Even though you took out the drive you might still fault and remove it using mdadm. I've never tried such but you don't have anything to lose.

It is always a good idea to really know what you are doing before you do it with mdadm and raid. So much power therein. And, it is also wise to keep full backups of all important data on an array. I keep two.

Keep us informed of how you do.

---

### Post by Muntted on 2008-06-28
It seemed to fix itself after another reboot.

Thanks anyway

---

### Post by fjgaude on 2008-06-28
Great... some things are not to be known! <smile>

---

