---
title: "Cloning a small HD to a bigger HD"
date: 2017-08-30
forum: General Help
---

### Post by mountainman70 on 2017-08-30
I am dual booting W10 home(64bit) & Ubuntu 27.4.2(64bit) on a 500GB HD. I want to use ddrescue to clone it to a 1TB HD. What steps should I use concerning the present 500gb partitions to the 1TB hd? Should I clone W10 to the 1TB and then set the right size Partitions and then clone Ubuntu? 
Thanks for any advice.

---

### Post by oldfred on 2017-08-30
If UEFI/gpt you can only clone an entire drive. The use of gpt prevents any clone of partitions as gpt partition table and backup gpt partition at end of drive have details from each partition that must match. May be possible to repair with major effort from gdisk, sgdisk & reinstall of boot loaders, chkdsk & fsck.

Better to just clone Windows, make sure it works and then reinstall Ubuntu. Then copy /home, and list of apps and perhaps some settings from /etc, or what should be your normal backup into new install.

       discussion of alternatives/strategy backups
[https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224](https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224)
[URL="https://help.ubuntu.com/community/BackupYourSystem"]https://help.ubuntu.com/community/BackupYourSystem

      [/URL]
 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)
Microsoft Windows 8.1 reinstall/refresh
[http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media](http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media) 
    [URL="https://help.ubuntu.com/community/BackupYourSystem"]
[/URL]

---

### Post by mountainman70 on 2017-08-31
> **oldfred said:**
> If UEFI/gpt you can only clone an entire drive. The use of gpt prevents any clone of partitions as gpt partition table and backup gpt partition at end of drive have details from each partition that must match. May be possible to repair with major effort from gdisk, sgdisk & reinstall of boot loaders, chkdsk & fsck.

Better to just clone Windows, make sure it works and then reinstall Ubuntu. Then copy /home, and list of apps and perhaps some settings from /etc, or what should be your normal backup into new install.

       discussion of alternatives/strategy backups
[https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224](https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224)
[URL="https://help.ubuntu.com/community/BackupYourSystem"]https://help.ubuntu.com/community/BackupYourSystem

      [/URL]
 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)
Microsoft Windows 8.1 reinstall/refresh
[http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media](http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media) 
    [URL="https://help.ubuntu.com/community/BackupYourSystem"]
[/URL]
Thanks oldfred. 
I thought that reinstalling Ubuntu may be the way to go.

---

