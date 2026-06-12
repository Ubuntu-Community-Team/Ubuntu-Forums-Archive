---
title: "Missing Root Disk ; problem locating file to move directory"
date: 2017-03-23
forum: General Help
---

### Post by elvis6 on 2017-03-23
I am running Ubuntu 12.04 Precise version, on a dual OS with Windows, and it was installed using WUBI.
Suddenly I am unable to boot Ubuntu, and get this error message
"GNU GRUB version 1.99-21ubuntu3.20
Minimal BASH-like line editing is supported. For the first word, TAB  lists possible command completions. Anywhere else TAB lists possible  device or file completions
grub>"

In another thread on this topic, readers were referred to these instructions.
[http://ubuntu-with-wubi.blogspot.co.at/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.co.at/2011/08/missing-rootdisk.html)

However, the recover process will not complete. When I get to the step to type the command "C:\>cd \found.000\dir" , it says [B]"File Not Found"
[/B]
This is the complete sequence of commands I type :
cd \
dir /a:h
C:\>cd \found.000
C:\>cd \found.000\dir

So, I get stuck after the last command. Instead of listing the root disk in the list of directories, it says File Not Found.
I don't know if it's user error on my part, or if the root disk is completely lost.

Here is the complete process, including my entries and the responses, copied and pasted> 
C:\WINDOWS\system32>cd \
 
C:\>dir /a:h
 Volume in drive C has no label.
 
 Directory of C:\
 
12/19/2016  07:18 PM               238 boot.ini
12/19/2016  06:19 PM                 0 CONFIG.SYS
03/05/2017  02:24 PM    <DIR>          found.000
09/17/2011  05:13 PM                 0 IO.SYS
09/17/2011  05:13 PM                 0 MSDOS.SYS
08/04/2004  08:00 AM            47,564 NTDETECT.COM
09/17/2011  07:57 PM           250,048 ntldr
03/22/2017  01:16 PM     1,598,029,824 pagefile.sys
03/20/2017  01:33 AM    <DIR>          RECYCLER
11/14/2014  06:37 PM    <DIR>          System Volume Information
               7 File(s)  1,598,327,674 bytes
               3 Dir(s)  49,794,396,160 bytes free
 
C:\>cd \found.000
 
C:\found.000>dir
 Volume in drive C has no label.
 
 Directory of C:\found.000
 
File Not Found
Please help determine why I am getting this response. Thank you.

---

### Post by Impavidus on 2017-03-24
When you write "cd \found.000\dir" at the prompt "C:\>" and it tells you "File not found", the filename may be wrong. But your full transcript shows that you listed the contents of \found.000 and it appeared empty. I don't know why chkdsk would create an empty directory for recovered stuff, but that's a windows problem and I don't know much about windows.

I'd like to point out though that wubi is old and no longer supported: [https://ubuntuforums.org/showthread.php?t=2229766](https://ubuntuforums.org/showthread.php?t=2229766). It was never really meant for long term use anyway and doesn't work on most more recent Windows systems. It isn't really a dual boot system. Ubuntu 12.04 is almost end of live too.

When you recover your root.disk, you can back it up by simply copying it to a safe place. You can put it on a usb drive, for example. Then I suggest you install a more recent U/Xu/Lubuntu, like 16.04 LTS, as a true dual boot or, if you don't care about Windows, as the only system. From *buntu you should be able to access your files stored in root.disk.

---

### Post by hakuna_matata on 2017-03-25
> **elvis6 said:**
> 
However, at the time, I was not educated of the process of how to create such a backup, and before I had the chance to learn how, the problem re-occurred, with the error message I quoted above. 

If the Windows program chkdsk doesn't move the root.disk to a hidden FOUND folder, the root.disk should be visible e.g. with the standard graphical interface of Windows. In your case the [file path]("https://en.wikipedia.org/wiki/Path_(computing)") is **C:\ubuntu\disks\root.disk** on Windows or **/host/ubuntu/disks/root.disk** on a Wubi installed Ubuntu.

So I thought few weeks ago that it was possible for you to copy an existing root.disk to a safe place as backup.

Can you check, if the root.disk is still within folder **ubuntu** and sub-folder **disks** ?
If you find it there, has the root.disk a size of zero bytes?

Are there important personal files on your root.disk ?

---

### Post by elvis6 on 2017-04-04
> **hakuna_matata said:**
> If the Windows program chkdsk doesn't move the root.disk to a hidden FOUND folder, the root.disk should be visible e.g. with the standard graphical interface of Windows. In your case the [file path]("https://en.wikipedia.org/wiki/Path_(computing)") is **C:\ubuntu\disks\root.disk** on Windows or **/host/ubuntu/disks/root.disk** on a Wubi installed Ubuntu.

So I thought few weeks ago that it was possible for you to copy an existing root.disk to a safe place as backup.

Can you check, if the root.disk is still within folder **ubuntu** and sub-folder **disks** ?
If you find it there, has the root.disk a size of zero bytes?

Are there important personal files on your root.disk ?

Hi, thank you very much for the responses. I apologize, as I have been delayed in responding due to health issues.
To answer your questions, when I follow that path, there is no "root.disk" folder inside the "disks" folder.
When I get to the disks folder, there is a "Swap Disk" file (about 262 MB) and a "boot" folder. Inside the boot folder is just a "grub" folder, and that is completely empty.
So I can't seem to find anything named root disk.
I do have somewhat important files on it, mainly bookmarks in my browser that I prefer not to lose, due to reinstalling it.

---

### Post by elvis6 on 2017-04-07
> **hakuna_matata said:**
> If the Windows program chkdsk doesn't move the root.disk to a hidden FOUND folder, the root.disk should be visible e.g. with the standard graphical interface of Windows. In your case the [file path]("https://en.wikipedia.org/wiki/Path_(computing)") is **C:\ubuntu\disks\root.disk** on Windows or **/host/ubuntu/disks/root.disk** on a Wubi installed Ubuntu.

Can you check, if the root.disk is still within folder **ubuntu** and sub-folder **disks** ?
If you find it there, has the root.disk a size of zero bytes?



Since I was unable to find the root folder inside the disk folder, I wondered if the instructions on this page are relevant to my issue, to recover the apparent lost contents.

[https://answers.microsoft.com/en-us/windows/forum/all/recovering-files-in-found000-folder-to-its/bd987b89-c9a7-458a-b6a1-c7bcf18512f5](https://answers.microsoft.com/en-us/windows/forum/all/recovering-files-in-found000-folder-to-its/bd987b89-c9a7-458a-b6a1-c7bcf18512f5)

A poster stated :
> Try this:  
[LIST=1]
[*]Back up your existing files to an external medium. **This is important!**.
[*]Launch Windows Explorer.
[*]Right-click one of the folders that has files missing.
[*]Left-click the line "Restore previous version".
[/LIST]

However, when I get to the 4th step and right-click my ubuntu disk folder, it does not have that option to "Restore previous version".
I am curious if anyone can tell me why that is ?

---

### Post by hakuna_matata on 2017-04-09
> **elvis6 said:**
> I am curious if anyone can tell me why that is ?
As far as I know, there is a size limit for backups and the file root.disk is a very large file. But it is a question about a Windows 7 backup function, therefore a Windows forum offers better answers.

If the root.disk is really deleted for unknown reasons, there are a lot of guides for recovering of deleted files. e.g. a general guide: [https://www.howtogeek.com/169344/how-to-recover-a-deleted-file-the-ultimate-guide](https://www.howtogeek.com/169344/how-to-recover-a-deleted-file-the-ultimate-guide).

This guide also contains links to a how-to for [ntfsundelete]("https://www.howtogeek.com/howto/13706/recover-deleted-files-on-an-ntfs-hard-drive-from-a-ubuntu-live-cd/") and [photorec]("https://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/"). These tools are available on a current Ubuntu [live CD/DVD/USB]("https://en.wikipedia.org/wiki/Live_CD").

---

### Post by elvis6 on 2017-04-11
> **hakuna_matata said:**
> If the root.disk is really deleted for unknown reasons, there are a lot of guides for recovering of deleted files. e.g. a general guide: [https://www.howtogeek.com/169344/how-to-recover-a-deleted-file-the-ultimate-guide](https://www.howtogeek.com/169344/how-to-recover-a-deleted-file-the-ultimate-guide).

This guide also contains links to a how-to for [ntfsundelete]("https://www.howtogeek.com/howto/13706/recover-deleted-files-on-an-ntfs-hard-drive-from-a-ubuntu-live-cd/") and [photorec]("https://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/"). These tools are available on a current Ubuntu [live CD/DVD/USB]("https://en.wikipedia.org/wiki/Live_CD").

Thanks again.
Hopefully, this is my last question on this : will any of those recovery options work, if it's now been about a month, since the large file was somehow deleted ?

---

### Post by hakuna_matata on 2017-04-13
> **elvis6 said:**
> will any of those recovery options work, if it's now been about a month, since the large file was somehow deleted ?
The probability decreases every time you use the hard drive with the deleted file. As the [recovery guide]("https://www.howtogeek.com/169344/how-to-recover-a-deleted-file-the-ultimate-guide/") wrote about the safest thing
> If you deleted a file on a magnetic hard drive and you’re still using  that computer, the safest thing to do is shut down the computer  immediately. [..] With the computer shut down, you should boot from a file-recovery live  CD or USB drive or remove the hard drive from the computer entirely and  place it in another computer as a secondary drive. The key is to avoid  writing to the drive entirely.

So maybe, you cannot recover the whole root.disk but important personal data within the root.disk with photorec. 

But if you don't need important personal data from your root.disk, just reinstall a newer version of Lubuntu like 16.04 LTS. That saves time.

---

