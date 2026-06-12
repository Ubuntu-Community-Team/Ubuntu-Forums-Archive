---
title: "External disk stuck in a readonly state!"
date: 2021-06-24
forum: General Help
---

### Post by nyung47 on 2021-06-24
Hello,  I can't write onto my External Disk, it is working fine on Windows and chkdsk found no errors! But on Ubuntu it is readonly and I can't write to it. It is strange, I already reformatted the disk and it was working fine for a short time on Ubuntu and I didn't use it on Windows for anything, except to copy some files from it. And now again: it is stuck in readonly state on Ubuntu! I tried following commands, but they did not work:  ```
 sudo mount -o remount,uid=1000,gid=1000,rw /dev/sdc1 
```   ```
 command1:sudo umount /dev/sdc1  command 2: sudo mkdir toshibaHDD command3: sudo mount -o rw,uid=1000,gid=1000,user,exec,umask=003,blksize=4096 /dev/sdc1 /media/toshibaHDD 
```  Any help appreciated TY! PS: sorry about formatting, indentation doesn't work!

---

### Post by ActionParsnip on 2021-06-24
What file system are you using on the file system please?

---

### Post by ActionParsnip on 2021-06-24
Before you unplug the device physically, do you use the safe remove feature in the OS before pulling the cable?

---

### Post by oldfred on 2021-06-24
If NTFS, did Windows set fast boot on? 
That sets hibernation flag and then the Linux NTFS driver cannot default mount the partition.

---

### Post by nyumg47 on 2021-06-24
> **ActionParsnip said:**
> What file system are you using on the file system please? NTFS  > **ActionParsnip said:**
> Before you unplug the device physically, do you use the safe remove feature in the OS before pulling the cable? I usually turn off PC and then disconnect it. Because Safely Remove option is missing! But I could remove it possibly ,while PC was on, by accident.  > **oldfred said:**
> If NTFS, did Windows set fast boot on?  That sets hibernation flag and then the Linux NTFS driver cannot default mount the partition. I don't use fast boot! Nor fast startup, nor hibernation!

---

### Post by ActionParsnip on 2021-06-24
If you connect it to a different Windows system then safe remove it, does it help?

---

### Post by tea for one on 2021-06-24
> **nyumg47 said:**
> Because Safely Remove option is missing! 

Are you using Windows 10?

File Explorer > Locate Drive > Right Click > Eject
A message should appear:- [COLOR="#0000FF"]Safe to remove hardware[/COLOR]

Windows updates sometimes re-enable fast start-up without user intervention.

---

### Post by nyumg47 on 2021-06-24
> **ActionParsnip said:**
> If you connect it to a different Windows system then safe remove it, does it help? Problem is that I don't have "safely remove" always visible in "Files" on Ubuntu. Then I should probably disconnect it, only after I turn off PC, if I don't forget, which could happen... Also it is not good for a disk!  > **tea for one said:**
> Are you using Windows 10?  File Explorer > Locate Drive > Right Click > Eject A message should appear:- [COLOR="#0000FF"]Safe to remove hardware[/COLOR]  Windows updates sometimes re-enable fast start-up without user intervention. That actually worked, many thanks :)

---

### Post by tea for one on 2021-06-25
> **nyumg47 said:**
> Problem is that I don't have "safely remove" always visible in "Files" on Ubuntu. Then I should probably disconnect it, only after I turn off PC, if I don't forget, which could happen... Also it is not good for a disk!   That actually worked, many thanks :)

That looks like a step forward.

In Files for Ubuntu, you also right click to expose [COLOR="#0000FF"]eject[/COLOR] or [COLOR="#0000FF"]safely remove[/COLOR].

Can you now read/write to the drive in Ubuntu?

---

