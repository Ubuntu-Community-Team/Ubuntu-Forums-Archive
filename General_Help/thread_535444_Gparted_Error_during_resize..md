---
title: "Gparted Error during resize."
date: 2007-08-26
forum: General Help
---

### Post by romaho on 2007-08-26
I made a rookie mistake and didnt allocate enough room to my Ubuntu partition, so i want to resize it using Gparted.  so far here are the steps i have taken, and the result:

1. Boot from a LiveCD
2. Open Gparted
3. Unmounted the partition I wish to change
4. click the resize operation, and add another 20Gb to the end of it.  
    ***note*** there are no other partitions after the ubuntu partion, and there is plenty of free space.
5. click apply.
6. When the "applying pending operations" window opens up it goes through several steps and then fails.  It fails when it comes to "check filesystem on /dev/hdd3 for errors and 
fix them"

I have tried to run the disk check alone without the resize and i get the same error.  Also, every time it fails to complete the operation if i want to try again the partition is mounted again and I have to unmount it again.  

If anyone has any ideas I would love to give them a shot and let you know how it goes.

Thanks
Romaho

---

### Post by khughitt on 2007-08-26
Are you running a dual-boot system? I know sometimes GParted has trouble resizing NTFS partitions and you need to run [FONT="Courier New"]chkdisk[/FONT] (in windows) before you can resize the partition.

What is your current partition set-up? There is a bootable version of Gparted ([Gparted Live!]("http://www.google.com/url?sa=t&ct=res&cd=1&url=http%3A%2F%2Fgparted.sourceforge.net%2Flivecd.php&ei=NsfRRqPzEaW8esuExLQJ&usg=AFQjCNGWyivxbJE-tRN5Pe2km0nGTmRBvw&sig2=cGLIwcVmmWHU3bV6td2E3A")) you can use so that you don't have to run the Ubuntu live cd everytime you want to change the partitions.

---

### Post by romaho on 2007-08-26
Thanks Pwnedd, 

     I am going to give that Gparted Live CD a shot and see how it goes.  As far as my hard drive setup i have:

1. ~40Gb NTFS
2. 2GB Swap
3. 10Gb Ext3
4. Lots of unallocated.

I will try reunning check disk in windows, but I am not try to resize the NTFS partition so i dont know how much it will make a difference.  But I'll give it a shot here in a couple of minutes.  I'll oet you know how it goes.

---

### Post by romaho on 2007-08-26
> **pwnedd said:**
> Are you running a dual-boot system? I know sometimes GParted has trouble resizing NTFS partitions and you need to run [FONT="Courier New"]chkdisk[/FONT] (in windows) before you can resize the partition.

What is your current partition set-up? There is a bootable version of Gparted ([Gparted Live!]("http://www.google.com/url?sa=t&ct=res&cd=1&url=http%3A%2F%2Fgparted.sourceforge.net%2Flivecd.php&ei=NsfRRqPzEaW8esuExLQJ&usg=AFQjCNGWyivxbJE-tRN5Pe2km0nGTmRBvw&sig2=cGLIwcVmmWHU3bV6td2E3A")) you can use so that you don't have to run the Ubuntu live cd everytime you want to change the partitions.


The GParted Live CD worked like a charm.  I think my problem had something to do with a bug i was reading about where drives were auto mounted even after being unmounted.  

Thanks man.

---

### Post by khughitt on 2007-08-27
No problem. Glad it worked out :)

---

