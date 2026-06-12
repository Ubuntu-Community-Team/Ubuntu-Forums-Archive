---
title: "fdisk which type of formatting to select, storing .img file"
date: 2015-04-22
forum: General Help
---

### Post by J_Me on 2015-04-22
I need to make a backup image of windows 8.1 to a 32gig sdcrad.
What should I format the sdcard to exFAT/EFI/GPT or doesn't it matter.

Thanks

---

### Post by dino99 on 2015-04-22
when it comes to work with an OS, its preferable to use its own apps. But that forum answer/help ubuntu user for their ubuntu installation(s)
Getting help here for a closed OS is amazing dont you. You might find what you need if you search about winhelp.us

---

### Post by TheFu on 2015-04-22
I'd use NTFS and use fsarchive to create the backup.  Be certain that Windows actually unmounts the file systems at shutdown - this is NOT the windows default.

Not sure I understand what fdisk has to do with this question.

---

### Post by J_Me on 2015-04-22
Thanks for the replies

@dino99
I asked about windows in the Other OS Support and Projects subforum here[ http://ubuntuforums.org/showthread.php?t=2274276]("http://ubuntuforums.org/showthread.php?t=2274276") Tried using the Windows Recovery Drive Program but it failed.

@Thefu
I can see how my OP is confusing. All I wanted to know was, what should I format the sdcard to using the fdisk program.

My intention is to dd over the laptop's hard drive to a backup.img file on a sdcard. Please goto the above link if you want.
Thanks

---

### Post by TheFu on 2015-04-22
I don't think dd is what you want to use. There are a number of reason NOT to do it that way.
However, if you do, the format will be that of the source.

You should really look into fsarchive.

---

### Post by J_Me on 2015-04-22
I tired googleing for fsarchive and couldn't find it. Just for clarity do you mean fsarchiver

me@here:~$ apt-cache search fsarchive
fsarchiver - file system archiver

---

