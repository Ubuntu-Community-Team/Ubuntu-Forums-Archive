---
title: "recover folder name and file name"
date: 2024-09-12
forum: General Help
---

### Post by mangada on 2024-09-12
I try to recover folder name and file name in NTFS partition, but Photorec recovers files without real name and folder name, what else utilities can do this?

---

### Post by dragonfly41 on 2024-09-12
testdisk

---

### Post by Rubi1200 on 2024-09-12
There are no guarantees that any of these tools will recover what you want.

Another option to consider is using a USB stick to boot the Windows partition and use Recuva, which is a Windows program.

Obviously, you need to install it on the USB stick first.

Again, no way anybody can guarantee these tools will work since we don't know how or when the folder was lost.

---

### Post by yancek on 2024-09-12
Why are you asking here at a Linux forum about recovering folders/files from a windows filesystem partition?  Microsoft has a support site you can go to and there are a number of windows specific forums to use, depending upon which version of windows you are using which you have not mentioned. 

What you describe about photorec is the expected, default behavior.

---

### Post by mangada on 2024-09-13
> **Rubi1200 said:**
> There are no guarantees that any of these tools will recover what you want.  Another option to consider is using a USB stick to boot the Windows partition and use Recuva, which is a Windows program.  Obviously, you need to install it on the USB stick first.  Again, no way anybody can guarantee these tools will work since we don't know how or when the folder was lost.  I just deleted files in a very simple way, and no files generated to overwrite the blocks, in my experience of using Windows program, it is almost 100% viewing / recovering folders/files with real name, I just want to do the same thing in Ubuntu.

---

### Post by yancek on 2024-09-13
If you have a windows filesystem on the partition, the logical thing to do would be to use a windows system to try to recover files.  Did you try booting windows and try to recover the files or use the software suggested in post 3?

---

### Post by mangada on 2024-09-14
> **yancek said:**
> If you have a windows filesystem on the partition, the logical thing to do would be to use a windows system to try to recover files.  Did you try booting windows and try to recover the files or use the software suggested in post 3?

I know I can do it in windows system, I still want to do it in Linux.

---

### Post by yancek on 2024-09-14
> I know I can do it in windows system, I still want to do it in Linux. 		 

That could be a challenging and time consuming hobby.  I can't help as I don't use windows and I can't imagine why any Linux developers would want to spend time on something like this, especially for free.  Have fun.

---

### Post by dragonfly41 on 2024-09-14
*A long shot* .. but I can remember using R-Linux *installed in Windows 10 (in dual boot mode) * to recover files. Also if you have recovered files using Photorec in a repository you can use Recoll to index every file and hunt for key words within the unnamed files. I use Recoll to go back more than 10 years in mail and other archives hunting for a word within each file. It takes a long time for Recoll to index and you need plenty of headroom to store the Recoll index file. I have just purchased Recoll (donation) to try it in Windows since I get great results in Ubuntu.

---

### Post by mangada on 2024-10-06
> **yancek said:**
> That could be a challenging and time consuming hobby.  I can't help as I don't use windows and I can't imagine why any Linux developers would want to spend time on something like this, especially for free.  Have fun.

No, **PhotoRec**'s brother **TestDisk** can list the name of the deleted file, it's unbelievable no one tell me here...

---

### Post by oldfred on 2024-10-06
I guess you did not see post #2 or first suggestion.

Testdisk does not always find files, and a few have said it showed files with full names, but then tried something else and never found them again. So if using testdisk, always copy files to another device immediately.

Photorec works, and there are tools to auto rename some types of files like photos. 

Best to always have back up then you do not have to spend 3 weeks trying to recover data.

---

### Post by TheFu on 2024-10-06
> **mangada said:**
> I know I can do it in windows system, I still want to do it in Linux.

In linux, we have these magical things called "backups", which make data recovery of deleted files unnecessary.  The admin for a system is expected to setup backups and maintain them in a verified way.  Linux isn't MS-Windows.  

So, to restore the stuff you deleted, pull out your backups from last night and restore the desired files and directories.  That's the expected way to accomplish this goal on Linux.

---

### Post by TheFu on 2024-10-06
> **mangada said:**
> No, **PhotoRec**'s brother **TestDisk** can list the name of the deleted file, it's unbelievable no one tell me here...

We all have backups that can be restored.  I find it surprising that you do not.  Just a different perspective, I suppose.

---

### Post by dragonfly41 on 2024-10-06
Did you read post #2? In reply to your post #1.

---

