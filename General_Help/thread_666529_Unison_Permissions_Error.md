---
title: "Unison Permissions Error"
date: 2008-01-13
forum: General Help
---

### Post by GoodPanos on 2008-01-13
I synchronize files between my laptop and my NAS Drive using the Unison GUI.  Every time I try to synchronize the files from the laptop to the NAS I get the following error:
> Error in setting permissions

I mount the folder that's on the NAS using SMB.  I have the following line in my fstab:
```
//192.168.1.10/projects    /media/projects smbfs  credentials=/home/goodpanos/.smbcredentials,dmask=777,fmask=777  0	0
```

I read on some threads that you have to mount the shared folder with the same privileges as my account?  I am not quite sure how to do this. :confused:

Any help would be greatly appreciated.

---

### Post by jken146 on 2008-01-13
sorry, ignore please :)

---

### Post by GoodPanos on 2008-01-13
Bum!

---

### Post by fragos on 2008-01-13
This may not be your issue but I had something similar with Unison and FAT formatted memory stick used to sync two Ubuntu boxes.  Windows more limmited permissions lost things with FAT in the middle.  I changed to using my local wireless network with NFS.  The permissions issue went away.

---

### Post by GoodPanos on 2008-01-14
Thanks for the reply but this is one of those Buffalo HDs where you just hook it up to the network and it gives you a web-interface to control it.  I am not sure it supports NFS.

I am still betting on it being a permissions issue.  One guy here got it working but he never gave a clear explanation of his solution.

---

### Post by GoodPanos on 2008-02-06
Really BUM! :(

---

### Post by beansdad on 2008-03-06
Bump.

I have the same sort of problem but both laptop & desktop drives are FAT32 the prob is that laptop has rwxrwxrwx permissions whereas desktop has rwxrwx---! Nothing I try will let me change these and unison simply refuses as chmod is not allowed.

I am desperate for a sync prog that works without changing the file dates.

Please can somebody help.:confused:

---

### Post by fragos on 2008-03-06
Available permissions are a function of the file system.  Linux file systems support user, group and world where Microsoft FAT doesn't.  When you transfer to or from a FAT file system the original Linux permissions can't go with the file.

---

### Post by beansdad on 2008-03-07
Does this mean I can't sync files at all? Unison reports property differences as well as file changes and won't allow the files to transfer as it can't change the properties.:confused:

---

### Post by fragos on 2008-03-07
I use Unison to sync two Ubuntu machine over NFS.  Both are formatted EXT3.  I've also used Unison to sync with a memory stick formatted FAT.  It always worked but always changed the permissions which is why I now run Unison over NFS.  I might ask why you are using FAT.  It makes sense on flash storage media.

---

### Post by beansdad on 2008-03-07
I keep my files on a separate partition formatted as FAT so that should I ever have to use Windows I can still read the files. My customers tend to use MS progs so, regretably, I need to check compatibility once in a while.

---

### Post by beansdad on 2008-03-11
Bump again - I really do need to get this working but Unison will not allow file permissions to be changed by chmod and won't ignore the permissions either.

Please help.:(

---

### Post by GoodPanos on 2008-03-25
BUM Indeed! :(

To this day I can't natively synchronize my files on Ubuntu to my NAS Drive.  I have to run Windows on VirtualBox, share my files, and then run SyncToy.  That is ridiculous.

Is there something that works!!?? ](*,)  Any recommendations are greatly appreciated; it doesn't even have to be Unison.

Seriously, how do you sync your files to a network drive?

---

### Post by fragos on 2008-03-25
I haven't used it myself but rsync might provide a solution for you.

---

### Post by kevdog on 2008-03-25
[http://ubuntuforums.org/showthread.php?t=280473](http://ubuntuforums.org/showthread.php?t=280473)

You've read that thread -- particularly about the UID part in the instructions?


Edit
I also found this link useful:
[http://www.linuxquestions.org/questions/linux-newbie-8/mounting-an-smbfs-using-fstab-461202/](http://www.linuxquestions.org/questions/linux-newbie-8/mounting-an-smbfs-using-fstab-461202/)

---

### Post by wieman01 on 2008-03-25
Unison has issues with FAT32 volumes. I used to experience the exact same problem with Unison, and 'chmod' won't make a difference because FAT file systems cannot handle Linux file permissions. 

So my advice is that you use a ext3 or Reiser file system instead. If you still need FAT, then take a look at this thread:

[http://ubuntuforums.org/showthread.php?t=302412]("http://ubuntuforums.org/showthread.php?t=302412")

Basically it says:
> Unison stores sync profiles in ~/.unison/*.prf. Edit the relevant prf file, and add a line 'perms = 0' and it will always ignore permissions for that profile. 
But apparently this doesn't work for everybody.

---

### Post by GoodPanos on 2008-04-02
Sorry I haven't tried the new suggestions yet.  I did though insert the line "perms = 0" in the profile on my MAC PowerBook G4 which used MAC OSX and it worked there fine.  I have yet to try it on Ubuntu.

---

### Post by GoodPanos on 2008-04-05
That did it, "perms = 0" :)

---

### Post by beansdad on 2008-04-08
"perms = 0" won't work for me. I need to keep documents in FAT32 partition so they can be read by Win2K or XP when I absolutely have to.

---

### Post by wieman01 on 2008-04-08
> **beansdad said:**
> "perms = 0" won't work for me. I need to keep documents in FAT32 partition so they can be read by Win2K or XP when I absolutely have to.
But you can install [this tool]("http://www.fs-driver.org/") for Windows so that it can read and write to ext2 / ext3 volumes. No problem.

---

### Post by beansdad on 2008-04-08
Thanks, I'll give that a try and report back.

---

### Post by beansdad on 2008-04-11
That link certainly makes the difference - alas once I'd changed to ext2 for the partition where my files are kept it would no longer automatically mount. There is probably a solution to this but I've done a complete re-install. Still Unison works fine now.

---

