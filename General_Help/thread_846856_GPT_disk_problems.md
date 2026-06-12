---
title: "GPT disk problems"
date: 2008-07-01
forum: General Help
---

### Post by kandresen on 2008-07-01
I am running Ubuntu 8.4 and Ubuntu 7.10 while currently migrating from one system to the other, but while creating a software raid partition between my two disks (in Ubuntu 7.10) it seems to have incorrectly messed with my GPT partition. I am now getting:

/dev/sdb contains GPT signatures, indicating that it has a GPT table.  However, it does not have a valid fake msdos partition table, as it should.  Perhaps it was corrupted -- possibly by a program that doesn't understand GPT partition tables.  Or perhaps you deleted the GPT table, and are now using an msdos partition table.  Is this a GPT partition table?

It is indeed a GPT - if possible I would like to not depend on the fake msdos table at all - I should not need it. But right for now I am trying to get my partitions to work again... I can see them in gparted, but I cannot mount them :(

I have already tried to use: parted /dev/sdb 
rescue
start: 0%
end: 100%
and answered yes to it being a GPT table, this did not fix it.

partprobe is stating
 Warning: Disk has a valid GPT signature but invalid PMBR.
 Assuming this disk is *not* a GPT disk anymore.
 Use gpt kernel option to override.  Use GNU Parted to correct disk.

How do I correct this, and where can I pass the gpt kernel option to override, but if this is a boot option, I am not entirely sure it will help as sda,sdb, and sdc keep changing volume letter and current sdb may as well be sda at next boot.

---

### Post by kandresen on 2008-07-01
I found the solution;
It appears parted does not write the corrections to disk for some reasons, I did however notice that by using the "print" command from within gparted, the table was printed correctly, however I had to say yes repetitively.

What I thus did was to create a new partition, within the GPT volume crossing my fingers this would not overwrite anything, and it worked like a charm!

Since the creation of the partition table got written to disk, all partitions are now correctly discovered again :)

If anyone know what I need to do to write the changes to disk WITHOUT adding/deleting a partition I would like to know. Even better - If someone know how to remove the fake msdos partition altogether, I would love to hear it!

---

