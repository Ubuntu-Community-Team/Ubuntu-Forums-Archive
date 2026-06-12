---
title: "Trouble writing to 4TB ext4 partition..."
date: 2014-12-29
forum: General Help
---

### Post by homenboro on 2014-12-29
I am having trouble writing to a newly bought 4TB internal HDD...

What I use...
1)Ubuntu 14.10
2)Gparted


What I did...(as root)
1)Create Partition Table->gpt
2)Create New Partition->ext4

New partition created successfully
Size=3.64TB  Used=58.GB Unused=3.58TB

Now when I try to write something to that newly partitioned Drive I can't...I can't even create a New Folder...All I can do is see the Properties of the Drive...

---

### Post by TheFu on 2014-12-29
Sounds like a permissions issue.

**ls -al** on the top level of the mount? Who is the owner, group for the mount point after mounting?  root.root or you.you?

---

### Post by oldfred on 2014-12-29
If already mounted use that mount. This example is a manual mount.

 #if not known to list partitions, change sda5 to your data partition or create multiples with different mount points
# is comment, do not type
sudo parted -l
sudo mkdir /mnt/data
sudo mount /dev/sda5 /mnt/data
#where sda5 needs to be your drive, partition
sudo chmod -R a+rwX,o-w /mnt/data
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
#All directories will be 775.
#All files will be 664 except those that were set as executable to begin with.
sudo chown -R $USER:$USER /mnt/data

If an internal drive better to auto mount to same location whenever you reboot by adding to fstab.

      
 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to.

---

### Post by TheFu on 2014-12-29
@oldfred - "super moderator?"  That's new. Congrats!  

The permissions above are excellent for a single-user system but not so good if there are multiple users. Just be aware of that @homenboro. If you want/need multi-user storage, it isn't too hard, but we need to know.

---

### Post by oldfred on 2014-12-29
@TheFu
Not sure what super is? The first thing they said is I now have permission to do some limited Admin functions, but first instruction was "Do Not Break" things. So I have not tried too much yet.

I have not configured multiple users, so not real familiar with groups and those kinds of settings. I did do that with Novell Netware back in the '90s.

---

### Post by homenboro on 2014-12-30
Its was infact a permission issue...and was solved by changing the owner...Thanks everyone for your warm support

---

### Post by TheFu on 2014-12-30
Great.
* Please mark the thread as solved. Would be helpful with the exact command used for others.
* You probably want to change the group as well.

---

