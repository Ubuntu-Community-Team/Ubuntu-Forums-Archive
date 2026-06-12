---
title: "Need some tips on copying many files to external drive"
date: 2017-02-19
forum: General Help
---

### Post by wardwebber on 2017-02-19
I'm fairly new to Ubuntu. A couple of years ago, I installed Precise Pangolin on my Windows PC so I could run either OS. After using Windows 10 for a year or so, I was suddenly unable to boot Windows up. I tried many workarounds, but all failed, so I'll have to reinstall Windows (which will delete all my documents, apps, etc.). I thought all my files would be lost, until I booted up Ubuntu; all my files were accessible, so I connected an external drive and began the tedious drag/drop task of copying them. After I reinstall Windows I plan to move all the files back onto the main drive.

I found I couldn't just copy a large number of files unattended, because error messages pop up, most related to files being buried too deep. I've tried using Backup, and no error messages appeared, but I'm not sure how to deal with the resulting "duplicity-full<lots of numbers and letters>" files on my external drive. 

Does anyone have any tips on how to accomplish this task reasonably efficiently?

---

### Post by ajgreeny on 2017-02-19
I'm not sure why files being "buried too deep" should make any difference but I do not use Windows any more so I may not know enough about their filesystem hierarchy.

Try using a copy command from your Ubuntu system to copy the files from Windows file system to your external drive with command ```
sudo cp */path/to/windows/files/* /media/*username/externaldrive/folder*
```editing what I show in italics to fit your situation, of course.
This will copy files as root so may work where doing it as user failed.

---

### Post by papibe on 2017-02-19
Hi wardwebber. Welcome to the forum ):P

Is the external drive NTFS formated too? (as the source in your Windows partition)?

If so, you may be hitting a limit on NTFS tree structure. Try to copy your files into a directory high up on the hierarchy. Alternatively, you could reorganize your source tree by copying less directories at a time and put them at the same level, or upper, instead of deep where they are.

I recommend using rsync to copy big chucks of data. If you have lots and lots of file, it would be also a good trick to copy subsets of directories at a time because rsync might use to much RAM at a time.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by HermanAB on 2017-02-19
Whoah...  which file system are you using on the external drive?  Portable disks usually come with FAT which has various limitations.  You should probably reformat the disk with something decent such as ext4, btrfs or even NTFS, then make the backup using rsync.

---

### Post by SuperFreak on 2017-02-19
> **HermanAB said:**
> Whoah...  which file system are you using on the external drive?  Portable disks usually come with FAT which has various limitations.  You should probably reformat the disk with something decent such as ext4, btrfs or even NTFS, then make the backup using rsync.

If you are copying the files back to a Windows system I wouldn't use ext4 or btrf as Windows won't read these file systems. NTFS is a better choice

---

### Post by wardwebber on 2017-02-19
The wording of the error messages I actually get is "Too many levels of symbolic links." I understand now that an rsync argument can take care of that.

---

### Post by wardwebber on 2017-02-19
Thank you all for your suggestions. I'm trying to use rsync with a few arguments to do the job. I had some problems specifying the source and destinations, but I seem to have succeeded when using the -n argument to do a dry run; at least I do get a file listing. However, when I remove the -n argument I get the result below. I'm trying to copy the directory "Wardo.Ward-Gateway" and its subdirectories and contents to Seagate Expansion Drive/Users. (I've found I need to use underscores for that name.) Here's the command I'm using and the result:

[FONT=courier new]ward@ward-K8T890-A:/media/Gateway/Users$ rsync -vap --safe-links Wardo.Ward-Gateway /media/Seagate_Expansion_Drive/Users/
sending incremental file list
rsync: writefd_unbuffered failed to write 4 bytes to socket [sender]: Broken pipe (32)
rsync: mkdir "/media/Seagate_Expansion_Drive/Users" failed: No such file or directory (2)
rsync error: error in file IO (code 11) at main.c(605) [Receiver=3.0.9]
rsync: connection unexpectedly closed (9 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(605) [sender=3.0.9][/FONT]

To a beginner like me, the errors are a tad arcane. I wish it were a simple directory name typo. . . .

---

### Post by SuperFreak on 2017-02-19
There is a graphical interface for rsync called grsync in Software Centre that will allow you to do this without renaming directories

---

### Post by wardwebber on 2017-02-20
Thanks so much, SuperFreak! I installed grsync and I'm copying happily away, with all the arguments and options I need; nothing pleases a Windows addict like a GUI interface. I recommend grsync to any other newbies who need the comfort of a dialog box :-)

---

