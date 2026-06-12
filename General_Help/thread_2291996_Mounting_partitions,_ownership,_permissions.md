---
title: "Mounting partitions, ownership, permissions"
date: 2015-08-24
forum: General Help
---

### Post by drm200 on 2015-08-24
I have two Windows NTFS data partitions that I want to access via Ubuntu.  Originally, I was able to access these partitions without problem.  Then I was experimenting with the Ubuntu disks utility to edit the mounting options when I switched Off and then back ON the "Automatic Mount Options" Switch ... This is when my problems began ... I've since then confirmed that this action will erase lines for mounting the associated partition in your fstab.

Anyway, after this incident, I found one partition working fine .. and the other with root ownership that I could not modify and also this partition now considers all text files executable. 

This is what I want (This is a laptop and I am the sole user):
Partition 1 ... should auto mount on boot. It is data only (no executables) ... And I should be able to R/W.
Partition 2 ... should not automount.  I'd prefer to mount manually only with admin password.  This partition is also data only (no executables) ... And I should be able to R/W.

I've created these two lines in my fstab in an attempt to accomplish what I want:

Partition 1:
/dev/sda6 /media/Work_Data ntfs nosuid,nodev,noexec,nofail,umask=007,uid=1000,gid=1000 0 0


Partition 2:
/dev/sda5  /media/BU_Data ntfs nosuid,nodev,noexec,nofail,noauto,x-udisks-auth,umask=007,uid=1000,gid=1000 0 0


I originally did not include the "umask=007,uid=1000,gid=1000" ... but was forced to add these options in order to take ownership of the files on the partitions.


This nearly achieves what I was after.  I am now able to R/W the partitions.  When I click on a text file it opens properly in the text editor. 

However, there is a problem in that all of the text files on Partition 1 & 2 are still considered executable (I can verify this by looking at the file properties) ... So If I copy a text file from Partition 1 or 2 to my desktop, Ubuntu will try to run the text file rather than open it in the default text editor. Additionally, any new text files I create on Partition 1 or 2 are set by Ubuntu as executable.


What I want to achieve:
              All new text files I create in Partition 1 or 2 should to be set as nonexecutable
              All existing text files on these two partitions to be set as nonexecutable.
              If I copy a text file from Partition 1 or 2 to my desktop, it should be considered nonexcutable


I'm somewhat stalled on how to achieve this.

---

### Post by Morbius1 on 2015-08-24
Preplace umask with it's directory ( dmask ) and file ( fmask ) component parts:

dmask=007 <--- This will make all folders 770
fmask=117 <--- This will make all files 660

So it would look something like this:
>  /dev/sda6 /media/Work_Data ntfs nosuid,nodev,noexec,nofail[COLOR=#0000cd]**,dmask=007,fmask=117**[/COLOR],uid=1000,gid=  1000 0 0

---

### Post by TheFu on 2015-08-24
```

/dev/sda6 /media/Work_Data ntfs nosuid,nodev,noexec,nofail,umask=007,uid=1000,gid= 1000 0 0
```
Shows an extra space after the 'gid=' that will not work.  Typo?

Have you tried fmask and dmask options for stronger control over the umask?  After all, the directories must have execute or they don't work.
[https://askubuntu.com/questions/113733/how-do-i-correctly-mount-a-ntfs-partition-in-etc-fstab](https://askubuntu.com/questions/113733/how-do-i-correctly-mount-a-ntfs-partition-in-etc-fstab)

I've never seen nofail used. Need to look that up. I don't need that, see where it could be useful.  Have you seen the **nouser** and **users** options? Might simplify your desire to prevent others from mounting, but not cause sudo hassle for you.

---

### Post by drm200 on 2015-08-24
"dmask=007,fmask=117"



That worked beautifully ....  I was not aware of the dmask/fmask options ... Thanks

---

### Post by drm200 on 2015-08-24
> **TheFu said:**
> ```

/dev/sda6 /media/Work_Data ntfs nosuid,nodev,noexec,nofail,umask=007,uid=1000,gid= 1000 0 0
```
Shows an extra space after the 'gid=' that will not work.  Typo?

Have you tried fmask and dmask options for stronger control over the umask?  After all, the directories must have execute or they don't work.
[https://askubuntu.com/questions/113733/how-do-i-correctly-mount-a-ntfs-partition-in-etc-fstab](https://askubuntu.com/questions/113733/how-do-i-correctly-mount-a-ntfs-partition-in-etc-fstab)

I've never seen nofail used. Need to look that up. I don't need that, see where it could be useful.  Have you seen the **nouser** and **users** options? Might simplify your desire to prevent others from mounting, but not cause sudo hassle for you.

The extra space was just a typo when I inserted it here ... The sudo is ok for me ... its a partition I don't use much ..

thanks.

---

