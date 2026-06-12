---
title: "Deleting corrupt file &quot;Bad message&quot;"
date: 2016-12-13
forum: General Help
---

### Post by delhagen-k on 2016-12-13
I'm trying to delete a file that I am 100% certain is corrupting my brand new ssd. I've tried deleting it with sudo rm "Test.txt" sudo rm -i *Test.txt* and also tried deleting it using the inode number through ls -li, but ls -li only shows ? for the inode number and the permissions although the file name is still there. Whenever I try to do one of these commands or even just ls in the directory containing that file it puts my entire system into read only mode and gives the error in terminal "cannot access 'Test.txt':Bad Message". Sometime it makes kubuntu not boot, and I have to fix that with fsck /dev/sda5 -y  but the file still remains. I have tried using a live cd to delete it, but I get the same results. The os operates completely normally including saving and creating files until attempting to read or write to this file. Please help :)

---

### Post by ajgreeny on 2016-12-13
What does the command ```
file /path/to/Test.txt
```using the full path, of course, not what I have typed, tell you about the file, if anything?

---

### Post by delhagen-k on 2016-12-13
Cannot open './Desktop/Test.txt' (Bad message)

I also ran it with sudo same thing.

---

### Post by delhagen-k on 2016-12-13
I believe I created the file when I was booted in windows using ext2fsd. Im pretty sure that its 4 bytes long and contains the word 'test'. I realized a few days ago that ext2fsd was corrupting my drive every time it mounted it in windows 10(It messed up superblocks or something), so I set ext2fsd to only open it in read only mode. I tried deleting the file in windows by re enabling the read write access in ext2fsd, but it wont change back. I am dual booting using rEFInd as my boot manager, although I dont know if that information is necessary. What should my next step be?

---

### Post by delhagen-k on 2016-12-14
Bump: I really need this fixed as the only other option I see is to wipe the partition and reinstall kubuntu.

---

### Post by RobGoss on 2016-12-14
Have you tried to rename this file and then try to delete it? or move it to the trash bin and delete it from there

---

### Post by delhagen-k on 2016-12-14
The problem is that whenever I try to anything it makes my entire harddrive read only. I can not even see the file with dolphin. Im able to prevent the entire system from read only by using a live cd, but even then I still get "bad message" on anything. I was able to move the file into the trash by using the mv command on its parent folder to home/username/.local/share/Trash/files/, but again when I try to delete the files in the trash(or even view) it puts the system in read only. Do you think this has something to do with the file's owner and its permissions? Maybe it doesnt have read enabled for any user, because it was created in windows. Any thoughts?

---

### Post by cdtech on 2016-12-15
Sounds like a zombie file.

> From Wikipedia on SIGCHLD signal:

When a child process terminates before the parent has called wait, the kernel retains some information about the process to enable its parent to call wait later. Because the child is still consuming system resources but not executing it is known as a zombie process.

On Unix and Unix-like computer operating systems, a zombie process or defunct process is a process that has completed execution but still has an entry in the process table. This entry is still needed to allow the process that started the (now zombie) process to read its exit status.


Using the "top" and "pstree" command could show which parent to kill, which in turn would send the init to the zombie process.

**I'm just guessing here........**

---

### Post by RobGoss on 2016-12-15
> **delhagen-k said:**
> I believe I created the file when I was booted in windows using ext2fsd. Im pretty sure that its 4 bytes long and contains the word 'test'. I realized a few days ago that ext2fsd was corrupting my drive every time it mounted it in windows 10(It messed up superblocks or something), so I set ext2fsd to only open it in read only mode. I tried deleting the file in windows by re enabling the read write access in ext2fsd, but it wont change back. I am dual booting using rEFInd as my boot manager, although I dont know if that information is necessary. What should my next step be?

So you state you think you created this file while you were booted up in Windows correct? 

If that's the case you might be able to also remove that test txt. file it while booted and login using Windows just a thought

---

### Post by delhagen-k on 2016-12-15
> **RobGoss said:**
> So you state you think you created this file while you were booted up in Windows correct? 

If that's the case you might be able to also remove that test txt. file it while booted and login using Windows just a thought

> **delhagen-k said:**
> I tried deleting the file in windows by re enabling the read write access in ext2fsd, but it wont change back.

> **cdtech said:**
> Sounds like a zombie file.



Using the "top" and "pstree" command could show which parent to kill, which in turn would send the init to the zombie process.

**I'm just guessing here........**
I ran top, it says there are 0 zombie processes even after I attempt to access the file. Is there something else that I am supposed to be doing with those commands?

---

### Post by QIII on 2016-12-15
Hello!

I don't think there is a process running, so there is nothing to kill.

What I suspect might be going on here is that you created and moved the file with Windows and then "shut down". 

 But if Windows "Fast Startup" is not disabled, Windows does not actually fully shut down.  Instead, it enters a hybrid hibernation mode.  In that condition, a dual boot Ubuntu will be kept from deleting any files your Windows boot counts to be in its bailiwick.  The file is effectively in a read/only state that Ubuntu will not mess with.  That is intended to keep you from corrupting your Windows installation.  

You might try turning off "Fast Startup" (which is really nothing more than a ploy to make it seem as though Windows is starting faster, when all it is really doing is resuming from hibernation) in Windows and making sure Windows is fully shut down -- not in that hybrid hibernation mode.  Then try deleting that file.

---

### Post by kpatz on 2016-12-15
Boot from a live CD or USB, then run```
sudo e2fsck -f -p /dev/sda5
```and see what you get. (change /dev/sda5 to whatever partition the errant file is in).

The -f will make it check the entire file system instead of just replaying the journal and thinking all is ok.  Hopefully that will fix the issue--sounds like the directory entry is pointing to a non-existent or invalid inode.

---

### Post by delhagen-k on 2016-12-16
> **QIII said:**
> Hello!

I don't think there is a process running, so there is nothing to kill.

What I suspect might be going on here is that you created and moved the file with Windows and then "shut down". 

 But if Windows "Fast Startup" is not disabled, Windows does not actually fully shut down.  Instead, it enters a hybrid hibernation mode.  In that condition, a dual boot Ubuntu will be kept from deleting any files your Windows boot counts to be in its bailiwick.  The file is effectively in a read/only state that Ubuntu will not mess with.  That is intended to keep you from corrupting your Windows installation.  

You might try turning off "Fast Startup" (which is really nothing more than a ploy to make it seem as though Windows is starting faster, when all it is really doing is resuming from hibernation) in Windows and making sure Windows is fully shut down -- not in that hybrid hibernation mode.  Then try deleting that file.

I already had fast boot disabled when I decided to dual boot so I dont think thats the issue

> **kpatz said:**
> Boot from a live CD or USB, then run```
sudo e2fsck -f -p /dev/sda5
```and see what you get. (change /dev/sda5 to whatever partition the errant file is in).

The -f will make it check the entire file system instead of just replaying the journal and thinking all is ok.  Hopefully that will fix the issue--sounds like the directory entry is pointing to a non-existent or invalid inode.
I already decided to just wipe linux and reinstall as I barely had any files on it. This might have fixed it, but I guess we will never know. Also thanks everyone for the replys!

---

