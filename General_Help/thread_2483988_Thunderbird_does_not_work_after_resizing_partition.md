---
title: "Thunderbird does not work after resizing partition using GParted"
date: 2023-02-14
forum: General Help
---

### Post by sgrhome on 2023-02-14
I am running Ubuntu 22.10 and I can classify myself as "slightly more competent" than a basic user. :P

I partitioned my single in-built SSD so that my data is moved into a separate partition. The data partition is now mounted under /media/user/xxxx/FolderName. The Email mbox folder is nested within "FolderName". 
In Thunderbird, I tried to update the above file path to point to the folder containing the mbox file. However, when I browse this file-path, I get a completely different path (/run/user/1000/doc/xxxxxxfx/user_mbox) that is displayed and Thunderbird promply displays a message that "The Local Directory Path /run/user/1000/doc/xxxxxxfx/user_mbox is invalid. Please pick a different directory. Furthermore, when I click on retrieve messages, I get an error message that "Unable to write the email to the mailbox. Make sure the file system allows you write privileges, and you have enough disk space to copy the mailbox.. 

I would be grateful for some tips on how to proceed here.

---

### Post by howefield on 2023-02-14
Thread moved to the "*General Help*" forum.

---

### Post by ajgreeny on 2023-02-14
Why have you tried to make things work this way; is the data shared between Windows and Ubuntu? I believe this is possible but have never needed to do so. However, is the partition where you have the data formatted as a Linux filesystem, eg, ext4 or some other non-Linux filesystem such as NTFS?

Show us the current ownership and permissions of the folder where you have your T'bird data with command ```
ls -la /media/user/xxxx/FolderName
```using the full pathway of course and not /xxxx/Foldername which I assume you wrote to avoid giving us private information.

It all seems a lot more complicated a method of doing things however than simply leaving the T'bird data, normally the hidden .thunderbid folder in your home, wherever it was and just using a symbolic link to it in your /home folder.
Perhaps I'm just misunderstanding exactly what you've done, so please clarify things a bit more for me.

---

### Post by oldfred on 2023-02-14
I for years shared Firefox & Thunderbird profiles with multiple installs. 
Years ago they were in a NTFS partition. When XP removed & new UEFI system, moved to ext4 data partition.

In my data partition I created a mozilla folder for both Firefox & Thunderbird. Now Firefox not working and had to copy into .mozilla in /home.
[http://kb.mozillazine.org/Thunderbird_:_FAQs_:_Changing_Profile_Folder_Location](http://kb.mozillazine.org/Thunderbird_:_FAQs_:_Changing_Profile_Folder_Location)

Profiles.ini
```
[InstallFDC34C9F024745EB]
Default=/mnt/data/mozilla/thunderbird/lyu25irb.default
Locked=1

[Profile0]
Name=default
IsRelative=0
Path=/mnt/data/mozilla/thunderbird/lyu25irb.default
Default=1

[General]
StartWithLastProfile=1
Version=2

```

This is my shared data partition. But now finding Firefox will not work in shared partition. Thunderbird still does.
[https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909](https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909)
[http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198) &
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)

---

### Post by MAFoElffen on 2023-02-15
As noted by oldfred... For Linux (Ubuntu), that 'profiles.ini' file is locate at ~/.thunderbird/profiles.ini... That is where Thunderbird looks to see where the profile file is. Could you please post the contents of yours?

---

### Post by sgrhome on 2023-02-17
Thank you for taking time to respond. Unfortunately since my system crashed, I ended up re-installing Ubuntu and Thunderbird and hence unable to provide specific info required for trouble-shooting

---

