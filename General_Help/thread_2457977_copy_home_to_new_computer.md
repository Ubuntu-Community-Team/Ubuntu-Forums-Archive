---
title: "copy home to new computer"
date: 2021-02-13
forum: General Help
---

### Post by cmcanulty on 2021-02-13
I always use the same name and passwords for my new machines. So I try to use grsync to move /home/myname to a new computer and I get boot error on missing uuid Why would uuid be needed for home? I thought that was in etc. Is there a way to move home and add an exception for the files that would cause this issue? Everything else works OK

---

### Post by TheFu on 2021-02-13
> **cmcanulty said:**
> I always use the same name and passwords for my new machines. So I try to use grsync to move /home/myname to a new computer and I get boot error on missing uuid Why would uuid be needed for home? I thought that was in etc. Is there a way to move home and add an exception for the files that would cause this issue? Everything else works OK

More details please.  Like the exact command used (can't grsync dump the rsync command?) and the partition setup?  Did you unplug a drive?

---

### Post by cmcanulty on 2021-02-14
I have a separate home and use the setup in the screenshots for grsync. Thank you.

[ATTACH=CONFIG]287957[/ATTACH]

[ATTACH=CONFIG]287958[/ATTACH]

[ATTACH=CONFIG]287959[/ATTACH]

[ATTACH=CONFIG]287960[/ATTACH]

---

### Post by TheFu on 2021-02-14
> **cmcanulty said:**
> I have a separate home and use the setup in the screenshots for grsync. Thank you.
 
I'd rather not be a dentist digging for clear information. Is that the source or the target?  A **df -Th** would be better, BTW.  Please remove the junk lines that aren't real file systems when posting.

I don't know grsync. Doesn't it show the rsync command somehow?  I find the GUI confusing.

---

### Post by cmcanulty on 2021-02-14
I am sorry that wasn't clear enough. Those partitons are from when I had a dual boot and I was told that I couldn't remove them without messing up the whole works. So everything is in a extended  partition. The 2MB is just the UEFI allotted partiton. So the 2 real partitions are /ext4 39 GB for everything except the /home of 891GB. The unallocated things I couldn't get rid of. grsync is the graphical front end for rsync and I use it because I am comfortable with it and it doen't seem as scary as grsync. It works very well and fast. I just need to find out where in the /home partition there is a file that states a specific UUID so I can put an option to exclude that file or directory. Thank you

---

### Post by Keith_Helms on 2021-02-15
You shouldn't need "run as superuser" checked just to copy your home directory.  UUIDs are hexadecimal keys associated with partitions.  A file copy operation should not mess with them EXCEPT if you somehow managed to copy into  / or /etc and overwrote your fstab file.  If you weren't running as superuser, you couldn't accidentally do that.

---

### Post by mastablasta on 2021-02-15
additionally you probably need to copy files, not partition. if you copied partition then new system needs to know where it is, so it is asking for it's UUID.

---

### Post by TheFu on 2021-02-15
> **cmcanulty said:**
> I am sorry that wasn't clear enough. Those partitons are from when I had a dual boot and I was told that I couldn't remove them without messing up the whole works. So everything is in a extended  partition. The 2MB is just the UEFI allotted partiton. So the 2 real partitions are /ext4 39 GB for everything except the /home of 891GB. The unallocated things I couldn't get rid of. grsync is the graphical front end for rsync and I use it because I am comfortable with it and it doen't seem as scary as grsync. It works very well and fast. I just need to find out where in the /home partition there is a file that states a specific UUID so I can put an option to exclude that file or directory. Thank you

So no **df -Th** will be provided as requested?
BTW, the grsync doesn't actually show any source/target stuff - or I'm I just dense?  GUIs are so confusing.  Plus, they lie. Give me a shell and a program with options any day.  Much clearer.

For people who find that confusing, there is explainshell.com.  It uses manpages to fill in what each option for a command means.

---

### Post by cmcanulty on 2021-02-15
OK thanks. The reason I run it as superuser is otherwise there is always an error usually referring to the .gvfs directory which is root even in /home

---

### Post by TheFu on 2021-02-15
.gvfs is a fake mount for temporary storage. We never want to backup that. Just one reason why mouting additional storage under a HOME is almost always a bad choice.

There shouldn't be any files/directories owned by other userids, even root, in a HOME for another user. There 
are exceptions, but I doubt more than 1,000 people worldwide would use that.  I needed it once, 20 yrs ago, for a few weeks.

---

### Post by cmcanulty on 2021-02-15
OK so I will set an exclude option in grsync for /home/cmcanulty/.gvfs and then uncheck the super user option, thanks all

---

