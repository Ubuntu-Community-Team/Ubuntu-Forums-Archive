---
title: "Swap not mounting"
date: 2006-12-05
forum: General Help
---

### Post by Sam Lars on 2006-12-05
I realized today (while running Amarok and Swiftfox and Thunderbird) that my swap space is not mounted.  I tried mounting it, but it gave me this:
```
:~$ sudo mount /dev/hda5
mount: mount point none does not exist
```
mount -a says that everything that can be mounted is mounted...
I may try restarting.

---

### Post by kevinlyfellow on 2006-12-05
hmmm I don't think that you actually mount the swap.  Try the command 
```
swapon -a
```
If that doesn't work you'll need to check your fstab file (/etc/fstab)

Your fstab file should read
```
/dev/hda5       none            swap    sw              0       0
```

---

### Post by Sam Lars on 2006-12-05
```
:~$ sudo swapon -a
swapon: /dev/disk/by-uuid/00d45b21-2895-4402-ba89-700908e6aa21: Invalid argument
```
This is what fstab has for swap:
```
#/dev/hda5 -- converted during upgrade to edgy
UUID=00d45b21-2895-4402-ba89-700908e6aa21 none swap sw 0 0

```
I tried changing it to what you have.
```
:~$ sudo swapon -a
swapon: /dev/hda5: Invalid argument
```

---

### Post by kevinlyfellow on 2006-12-05
I'd back up the fstab and replace UUID=00d45b21-2895-4402-ba89-700908e6aa21 with the device

---

### Post by Sam Lars on 2006-12-05
It gives me the same "Invalid argument" either way.

---

### Post by kevinlyfellow on 2006-12-05
Oh, edgy handles swap differently in the fstab... I'm looking at this post:
[http://ubuntuforums.org/showthread.php?p=1683612](http://ubuntuforums.org/showthread.php?p=1683612)

try ```
sudo mkswap /dev/hda5
sudo swapon -a 
```

---

### Post by Sam Lars on 2006-12-05
Ah, I didn't even think of that.  I did try hibernating, but it just shut my computer off.  Thanks!  It works now!

---

### Post by dskloet on 2006-12-09
I have the same problem. And when I do```
sudo mkswap /dev/hda5
sudo swapon -a
```it seems to be working. But after rebooting I have the same problem all over again. :(

---

### Post by Sam Lars on 2006-12-09
Okay, I think I had the same problem.  I'm not sure if it's fixed or not, but try this.
When you do the mkswap /dev/hda5, it should tell you what it's doing.  It will list a long code for where it's making the swap.  Try putting that in the fstab in place of what it has for the swap code.

---

### Post by dskloet on 2006-12-09
I'm sorry, it seemed it was a problem with hibernate as well. I followed the instructions in the mentioned thread and it seems to be working now. I hope it keeps working now.
Anyway, thanks for trying to help :).

---

