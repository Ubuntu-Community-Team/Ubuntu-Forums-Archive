---
title: "Auto Mount at Startup"
date: 2016-05-08
forum: General Help
---

### Post by anon24 on 2016-05-08
I don't understand the point of this in Disks... 

It doesn't actually Auto Mount anything at Startup.

I have successfully done it through Terminal before.

Why does Disks claim to do this, but actually doesn't?

Am I mistaken in their meaning of Auto Mount?

When I think "Auto Mount at Startup". 

I expect the drive to be ready to go and files on the drive ready to be accessed at Startup without having to Mount it myself.

Another interesting thing, Disks says that it should mount here:

/mnt/18a5d1bb-26ac-437e-bb69-1b83aca17e0e

It actually mounts it in media...

---

### Post by Mark Phelps on 2016-05-08
What filesystem is it you are trying to mount?

You can accomplish the same thing by putting the mount command into the /etc/fstab file:  [https://wiki.archlinux.org/index.php/fstab]("https://wiki.archlinux.org/index.php/fstab")

Good Luck

---

### Post by oldfred on 2016-05-08
For those partitions I only occasionally use, I add labels. Then the automount uses the label instead of the UUID. And I then can really tell what partition it is. I normally try to remember to label when creating partition, but if changed or I forget then I use Disks or command line to add label.
With gpt now there are two labels, one is the gpt partition and one is the filesystem. Filesystem label is where it will be mounted.

I often link to same fstab as Mark Phelps link above. Best to review first.
This is a specific example that then may make more sense and gives specific examples/templates for both NTFS & ext4.
 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.

Are you just using the icon to mount in Disks.
If you want it to add an entry to fstab it does, but under "Edit Mount Options" on tiny gears icon.
But its default settings are not the best. See template above. You could use Disks to add entry and then edit parameters afterwards, if desired.

---

