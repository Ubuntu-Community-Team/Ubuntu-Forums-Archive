---
title: "Raid5 mdadm assemble with weird error message"
date: 2021-04-05
forum: General Help
---

### Post by pzYsTorM on 2021-04-05
Hi,

I have a RAID5 with 5 disks, 4 of them are still alive. On one disk the "events" counter differs by 2.
I would like to start that array but there is an error.

```

$ mdadm &#8211;-assemble --run --force /dev/md128 /dev/sdg1 /dev/sdh1 /dev/sdi1 /dev/sdj1
mdadm: No action given for &#8211;-assemble in --misc mode
       Action options must come before device names

```

what am I doing wrong?

Here some infos on these four HDDs:

```

$ mdadm -E /dev/sd[ghij]1 | grep -E '(dev|UUID|Events)'
/dev/sdg1:
     Array UUID : d356f541:93207320:07aeec56:f23ebf2e
    Device UUID : b8175b1f:7e597f5b:516ccf30:9a20325e
         Events : 14973
   Device Role : Active device 4
/dev/sdh1:
     Array UUID : d356f541:93207320:07aeec56:f23ebf2e
    Device UUID : cbf47034:75e22b1a:7e4dd7c5:5ef3a417
         Events : 14971
   Device Role : Active device 2
/dev/sdi1:
     Array UUID : d356f541:93207320:07aeec56:f23ebf2e
    Device UUID : 0972bd4d:81165f64:a6404c16:0c30f023
         Events : 14973
   Device Role : Active device 1
/dev/sdj1:
     Array UUID : d356f541:93207320:07aeec56:f23ebf2e
    Device UUID : e019cdfe:3f4f9aaa:fffb4f67:fcd0291b
         Events : 14973
   Device Role : Active device 0

```

FYI: I just want as less write action as possible, because I dont know how long the disks are still surviving. Means: the best would be, just bring it up, maybe even in readonly mode, no resync etc.
I would immediately backup everything I need and afterwards destroy that array. I dont want to use that array afterwards.

---

### Post by TheFu on 2021-04-05
mdadm needs a **sudo** first.

---

### Post by pzYsTorM on 2021-04-05
Sure. I am executing these commands as root user.

---

### Post by TheFu on 2021-04-05
> **pzYsTorM said:**
> Sure. I am executing these commands as root user.

Ah ... by convention (all Unix/Linux books), the $ prompt would be shown, instead, as the **#** prompt when root is used.  I wondered why there wasn't a permission error displayed.

When I need to reassemble an array, 
```
sudo mdadm --assemble  /dev/md128   -v --force
```
would be the command.  Seems you have extra options which may be conflicting with the reality.  If a missing drive has been replaced, then add that to the array with something like ... 
```
sudo mdadm   /dev/md128 -a /dev/sdf1
```
first.  Has the bad HDD been logically failed and removed in the mdadm-world? Here's how
```
sudo mdadm --manage /dev/md128  --fail /dev/sdf1
sudo mdadm --manage /dev/md128  --remove /dev/sdf1
```

As for read-only ... that's controlled at mount time.
I don't know how to prevent a spare from rebuilding ... other than not having it available.
I like checking the /proc/mdstat file. Good, simple, overview of how things are in the arrays.

As you've learned, RAID is never a replacement for backups.  I really hope no data loss has happened.

---

### Post by pzYsTorM on 2021-04-05
Ok, thanks so far for your ideas.

With three drives I cant get it up because these are too few drives.

With an old mdadm version under Ubuntu 16 I had a similar issue and this command was successfully working:

```
mdadm –-assemble --run --force /dev/md128 /dev/sdg1 /dev/sdh1 /dev/sdi1 /dev/sdj1
```

and gave some output, something like that the event counter has been set to the highest number and the array is now up and running.
So this command was still in my "mdadm rescue text file".

---

### Post by SeijiSensei on 2021-04-05
Try putting "/dev/md128" immediately after "--assemble".

---

### Post by pzYsTorM on 2021-04-06
yeah, thanks, the order was indeed the problem.
only this command is working:

```

# mdadm --assemble /dev/md128 /dev/sdj1 /dev/sdi1 /dev/sdh1 /dev/sdg1 --run --force
mdadm: forcing event count in /dev/sdh1(2) from 14971 upto 14973
mdadm: /dev/md128 has been started with 4 drives (out of 5).

```

---

