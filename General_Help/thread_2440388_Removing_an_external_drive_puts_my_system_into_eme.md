---
title: "Removing an external drive puts my system into emergency mode"
date: 2020-04-09
forum: General Help
---

### Post by michael351 on 2020-04-09
I upgraded to a new computer recently and took the external drive (media files) from the old computer and connected it with the new computer. All is good.

So I went back to my old computer to do clean up and when I tried to boot into Ubuntu 18.04 - it went into emergency mode. I looked at the journal log and sure enough it had my old external drive (in red letters) as "failed" .... which of course it hasn't, it was just removed.

So I went to my new computer, took off the external hard drive and put it back on my old computer - and the old machine booted up just fine into Ubuntu 18.04 like it always did.

What do I do to "safely" remove this disk so Ubuntu on this old computer no longer looks for it or otherwise try and mount it. 
Why does Ubuntu do this in the first place? why not just advise me there is a missing drive and ask what I want to do? like skip it?

Thanks!

---

### Post by michael351 on 2020-04-09
O.k. - update - I unmounted the drive and then edited /etc/fstab and commented out the external USB drive. Shutdown the computer, removed the drive and re-booted and it came up fine.

So my question becomes, what would I have to do if the drive actually failed and I had to replace it? The new drive would have a different UUID identifier.

---

### Post by TheFu on 2020-04-09
if a drive fails, then you'll need backups if any partitions are integrated into the OS.  You'll need to learn to do that.  

External disks really should be mounted in a way that doesn't break anything if they are or aren't there at any point - boot, post-boot, whatever.  The fstab has options for that.  systemd-mount has options for that. systemd-automount has options for that.

Definitely prefer one of those methods over using a GUi to access the storage.  
[https://ubuntuforums.org/showthread.php?t=2437500&p=13935156#post13935156](https://ubuntuforums.org/showthread.php?t=2437500&p=13935156#post13935156) has an example.

---

