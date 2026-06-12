---
title: "How to make sure Windows is totally gone"
date: 2015-06-09
forum: General Help
---

### Post by grant10 on 2015-06-09
Don't know much about computers at all. My girlfriend's computer was running windows but got some error related to boot.mgr and would never start. I was able to trace the problem back to some folder titled [(^_^)]  so I figured it was probably something malicious. I read on another site that they probably already wiped my hard drive.

Anyway, I installed Ubuntu now. I chose to replace the Windows with Ubuntu instead of having both.

So, is Windows and everything related to it completely gone from the computer now? Is there a way to check if its completely gone? If it's not completely gone, how do I delete the rest of it? I don't want anything to do with Windows or any of the files on this computer anymore.

Thanks

---

### Post by QDR06VV9 on 2015-06-09
Hi gGrant10 and Welcome to Ubuntu. If you did indeed choose replace windows and install Ubuntu.
 You accomplished what you wanted that method will wipe Windows and delete your data.
I have been Windows Free for 7 years and LOVE it.
If I could offer advise to you and your girlfriend it be **patience**!
I am sure by now you have noticed that Linux is not Windows.(You will appreciate that in time)
Kind Regards and Happy Ubuntu-ing

---

### Post by yancek on 2015-06-09
In order for malware to be damaging, it needs to be executable.  A windows executable will not run on any Linux system.  You might still see some annoying malware.  If you used the "Erase disk and install Ubuntu" option you should be good.

---

### Post by coffeecat on 2015-06-09
Welcome to the forum.

If you chose the option that uses the whole drive for Ubuntu, Windows is gone. Ubuntu files will have overwritten some areas where Windows-associated files were. In other areas of the drive there will still be the 0's and 1's which if reconstructed would be Windows associated files or personal data, but it would need recovery software to be able to do anything with them. Ubuntu cannot access them without such recovery software and will eventually overwrite them. If you want to be sure that all the Windows partitions have gone, open a terminal (keyboard shortcut = ctrl-alt-t) and run this command:

```
sudo fdisk -l
```

Post the output and someone will interpret it for you. The command will ask you for your password. As you type this in, nothing appears to be happening. This is normal. Just type it in followed by enter. To copy and paste into your post, highlight the output with your mouse, right-click -> copy. Then paste into your post.

---

### Post by grant10 on 2015-06-16
> **coffeecat said:**
> Welcome to the forum.

If you chose the option that uses the whole drive for Ubuntu, Windows is gone. Ubuntu files will have overwritten some areas where Windows-associated files were. In other areas of the drive there will still be the 0's and 1's which if reconstructed would be Windows associated files or personal data, but it would need recovery software to be able to do anything with them. Ubuntu cannot access them without such recovery software and will eventually overwrite them. If you want to be sure that all the Windows partitions have gone, open a terminal (keyboard shortcut = ctrl-alt-t) and run this command:

```
sudo fdisk -l
```

Post the output and someone will interpret it for you. The command will ask you for your password. As you type this in, nothing appears to be happening. This is normal. Just type it in followed by enter. To copy and paste into your post, highlight the output with your mouse, right-click -> copy. Then paste into your post.

Thanks to everyone for the help. I ran that command and pasted the results below. I'm probably never going to do it, but how hard/how expensive would it be to try to retrieve our old pictures from windows?


```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

pickle@pickle-HP-G62-Notebook-PC:~$ sudo fdisk -l
[sudo] password for pickle: 

Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 byteshttp://ubuntuforums.org/showthread.php?t=2154381&p=13305096&viewfull=1#post13305096
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x45b40621

Device     Boot     Start       End   Sectors  Size Id Type
/dev/sda1  *         2048 968796159 968794112  462G 83 Linux
/dev/sda2       968798206 976771071   7972866  3.8G  5 Extended
/dev/sda5       968798208 976771071   7972864  3.8G 82 Linux swap / Solaris

pickle@pickle-HP-G62-Notebook-PC:~$
```

---

### Post by coffeecat on 2015-06-16
> **grant10 said:**
> I'm probably never going to do it, but how hard/how expensive would it be to try to retrieve our old pictures from windows?

Inexpensive but tedious and ultimately only partly rewarding. The results below show that you have used the whole disk for Ubuntu, so that you have effectively removed Windows.

> **grant10 said:**
> ```

Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 byteshttp://ubuntuforums.org/showthread.php?t=2154381&p=13305096&viewfull=1#post13305096
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x45b40621

Device     Boot     Start       End   Sectors  Size Id Type
/dev/sda1  *         2048 968796159 968794112  462G 83 Linux
/dev/sda2       968798206 976771071   7972866  3.8G  5 Extended
/dev/sda5       968798208 976771071   7972864  3.8G 82 Linux swap / Solaris

pickle@pickle-HP-G62-Notebook-PC:~$
```

But as far as rescuing old data is concerned, you have to bear in mind that the files that make up your Ubuntu installation will have overwritten some of your Windows files, but not necessarily all. Some/many of your personal files will still be written to disk, and not yet overwritten, but not accessible through the new filesystem. The trouble is that they will be mixed up with files that made up your Windows OS, all nicely mixed together. 

The testdisk app includes photorec that can recover many types of file in such a situation as this, including jpegs. But it is not particularly easy to use for someone new to Linux operating systems, and if it finds jpegs, the original filenames will be lost. Have a look at these links and see if this is something you wish to consider:

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)

Slightly more user friendly, but very dated, in that instructions for use in Ubuntu may need to be modified for current versions of Ubuntu:

[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

---

