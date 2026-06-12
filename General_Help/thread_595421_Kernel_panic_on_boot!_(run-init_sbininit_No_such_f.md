---
title: "Kernel panic on boot! (run-init: /sbin/init: No such file or directory)"
date: 2007-10-28
forum: General Help
---

### Post by brownbat on 2007-10-28
My oldest stick of RAM was causing some memory errors. I pitched it, but now when I reboot, I get :

```

run-init: /sbin/init: No such file or directory
Kernel panic - not syncing: Attempted to kill init!

```

fsck and parted show a clean drive. Not sure what to do now. The live CD shows me that I do have an /sbin/init, it's about the right size and everything. My fstab and grub's menu.lst seem fine. Any hints on how to further diagnose this problem?

Can I copy the /sbin/init from the liveCD onto my disk? Are they substitutable?

---

### Post by lubosz on 2007-11-30
I have the same problem....
I didn't change anything, maybe some updates... Could this be a hardware issue?

Same thing in safe mode btw.... I'll try some stuff...

---

### Post by smo0th on 2008-05-19
The exact same problem here, I'm not alone! :lolflag:

Well, let's research this more and post possible solutions here O:)

---

### Post by smo0th on 2008-05-19
Tried with the "recover broken system"(or something like that) that comes in th installation cd menu below OEM install.. no luck with any option.

Tried reinstalling the system, when I was at the partitioning section I saw something interesting, file system appears as ext2 and should be ext3, need to change that and see what happens, no clue on how to do that at this time.

---

### Post by smo0th on 2008-05-19
Okay, to convert ext2 to ext3 we have to follow this procedure:

1. Check if your root partition is mounted(in my case /dev/sda1)
```
df
```
If it's mounted you'll see it listed, in my case I have /dev/sda1 mounted in /ubuntu and we need to unmount it to proceed, use ```
sudo umount /ubuntu
``` or unmount it by right clicking on the device and select the 'Unmount' option(if allowed)

2. We proceed to create a journal inode to convert the ext2 file system to ext3:
```
sudo tune2fs -j /dev/sda1
```
3. Verify partition type: 
```
sudo blkid
```

We should see our /dev/sda1 as ext3 now.

However, after reboot I still get the same error :(

---

### Post by smo0th on 2008-05-19
Well, I decided to re-install the system leaving the root partition unformatted to preserve all data, I got out of ideas(and luck?) so this should fix the problem.

But why in the world this happened?
It all began with a [GRUB error 17]("http://ubuntuforums.org/showthread.php?t=752588"), my first part of the history there.
It would be interesting if someone could give a hint on this.

From all this I just think it's a good idea to ```
sudo e2fsck -C0 -p -v -f /dev/sda1
``` often as tons of errors arised when I ran it and seems to be a good practice to prevent this kind of weird stuff.

---

### Post by krkeegan on 2008-07-22
yup same thing happened to me tonight. Took my 3 hours to straighten all of this out, and I still don't really understand what happened.

All of a sudden my server had hundreds of nmbd processes running. This proceeded to bring it down before I could find the cause(which I never found).

Then I reboot I got the same Kernel panic error for a missing /sbin/init.  And when I used the rescue disk init was right there where it was supposed to be.  I ran fsck, I copied a new init over, nothing fixed it.

I eventually followed the last post that just did a base install over the top of the root partition.  That worked, but it sill made for a nice headache to clean up after.

Still wish I knew what caused both errors(nmbd and kernel panic), this is normally a very reliable server running for months at a time without complaint.

---

### Post by smo0th on 2008-07-22
my only clue for this is a hot key combination, although I didn't research on that, but my problem arose when the keyboard fell, anyway, it's always healthy to have backups and do periodically sanity checks :)

---

