---
title: "Disk Partition Mounting issue"
date: 2022-10-25
forum: General Help
---

### Post by fabjapan on 2022-10-25
Hi Community,

Although not an expert, I have been using Ubuntu for years now.
As one of my disk partition got full, I decided to do some formating and reorganization on the partitions of my secondary Disk (Hitachi HDD) using DISKS application; with 2 partitions (on sdc1):
- DATA
- WINDOWS (where I eventually want to store my VBOX windows images).

After doing it, I started to load files on DATA but eventually I got the message that I had no more space on my /home folder, which is located on my main Disk (Sandisk SDD, called fd-desktop on sda1) ?!?!?
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291176&stc=1[/IMG]
This did not make sense to me but I understood that although the 2 partitions above where physically on a different drive, the contents was mounted on /media/fd/home.

Then I starting digging into documentation and support to try to understand how to change the mounting point to /mnt/WINDOWS and /mnt/DATA using fstab but I could only see the physical disks being mounted at the right location, but not the 2 partitions.
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291177&stc=1[/IMG]
So bottom line is that I don't know what to do to mount my partitions 'contents' on my secondary HDD instead of main HDD.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291178&stc=1[/IMG]
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291174&stc=1[/IMG]
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291175&stc=1[/IMG]

I put above some snapshots of my system so you hopefully can lead me towards resolution.
Your support would be more than highly appreciated.

---

### Post by oldfred on 2022-10-25
Please do not use screen shots and post in line. Just attach them.
And if terminal output, just copy and post in code tags.
Both easy to use in Forum's advanced editor.

How to use Code tags, # in Forum's advanced editor
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
 If you use the Forum's advanced editor, you can use the paperclip icon to attach screenshots or other info. Post #4 , also no larger than1024x768 if photo
[https://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098](https://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098)

I do prefer to use gpt over MBR which is from 1980s. But conversion may erase drive.
I have only used gpt on new drives since 2010. 

This shows more info in one command. Use Code tags.
lsblk -e 7 -o name,fstype,size,fsused,label,partlabel,mountpoint,uuid

You should label all partitions.
Post this in code tags to see what you have in fstab.
cat /etc/fstab

I do not like using disks to create mounts in fstab. Its default settings are generally terrible. 
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Create mount point, mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.

---

### Post by ActionParsnip on 2022-10-25
You could make symlinks to the folder to make it appear as you wish. Personally I suggest using BASH aliases to make accessing the folders easier

---

### Post by fabjapan on 2022-10-26
@oldfred
Thank you so much for:
- giving me advice on how to write properly a thread. I will definitely do better next time
- proving the solution to my issue as a result, after applying the Template in fstab, it worked !!

Problem solved!

---

