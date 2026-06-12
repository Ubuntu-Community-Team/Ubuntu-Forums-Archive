---
title: "Accessing a 'cloned' Ubuntu drive."
date: 2023-01-24
forum: General Help
---

### Post by 77_GCSX on 2023-01-24
I have finally upgraded from 16.04 to 22.04. Everything went well but I have one issue. My customized Minecraft install. I NEED my java-7-openjdk-amd64 from my 16.04 drive. I have cloned it but whenever I plug it in to the dock it will not show up.

Is there a way to access this drive in Ubuntu? I do have a Windows 10 PC as well if this will help.

Thank You!!

---

### Post by TheFu on 2023-01-24
Connect the drive to the Linux system and run
```
lsblk -e 7 -o name,size,type,fstype,label,uuid,mountpoint
```
Post the command used and the output, wrap them in forum code tags.  Then we can see if we can help.  If the OS doesn't see the drive, there's little anyone here can do.  But if the OS sees the drive and the partitions, there's a good chance we can help you mount it.

However, if the UUIDs in the cloned drive and any drive inside your computer are the same, that will need to be fixed first.  Identical UUIDs on to file systems, partitions or disks are a problem.  The OS gets confused.

---

### Post by 77_GCSX on 2023-01-24
WELL, I guess I don't have to do the above. For some reason 22.04 can actually see the cloned drive. I was basing my post on previous experience with 16.04 and using 2 actual spinning disk drives. Maybe the UUID's were the same with the previous setup.

In any case I'm good. I plugged the cloned drive in and 22.04 saw it right away!!

Thank You!

---

### Post by TheFu on 2023-01-24
If the UUIDs are identical, you might be reading and writing to the wrong drive.  Every time it is connected or the system is booted, that risk exists.
If you used cloning tools like clonezilla or dd or ddrescue, then the UUIDs will be identical.  

If you really didn't clone, but just copied all the data over, then there are no inherent risks.

Only you know what happened, how the data got where it got and only you can decide what risks there are.  Changing a UUID isn't hard, especially on an external, unmounted, drive. Best to do that ASAP.  In fact, it wouldn't be a bad idea before you setup permanent mounts via the /etc/fstab.  

But it is your data to risk.

---

### Post by ActionParsnip on 2023-01-24
Is the issue now resolved? If so, please mark as solved

---

