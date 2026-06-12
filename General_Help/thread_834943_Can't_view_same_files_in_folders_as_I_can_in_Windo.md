---
title: "Can't view same files in folders as I can in Windows"
date: 2008-06-20
forum: General Help
---

### Post by johnnyxxxcakes on 2008-06-20
I was browsing through the folder where I have my MP3 songs located. I was viewing them on Ubuntu, and noticed that I can't view all of my songs, such as the The Arcade Fire. I can only see about 7 out of 11 of the songs I have by them, while when I go to the same folder under Windows Vista, I can view all of the files.

---

### Post by ryanhaigh on 2008-06-20
This might perhaps have something to do with the way the filenames are named or encoded, there are a few threads that talk about this, here for example: [http://ubuntuforums.org/archive/index.php/t-141434.html](http://ubuntuforums.org/archive/index.php/t-141434.html)

---

### Post by johnnyxxxcakes on 2008-06-20
> **ryanhaigh said:**
> This might perhaps have something to do with the way the filenames are named or encoded, there are a few threads that talk about this, here for example: [http://ubuntuforums.org/archive/index.php/t-141434.html](http://ubuntuforums.org/archive/index.php/t-141434.html)

Well I have 2 hard drives, each 70 GB. I have Windows Vista and Ubuntu on the first hard drive, but the other hard drive is completely empty and there is nothing on it when I click in within Windows Explorer.

---

### Post by cariboo on 2008-06-20
You do relize the windows cannot read other file system natively, you have to use another program to view the files, that is if it formated as an ext3 drive. Check this link out for a program that can read ext3 drives from windows.

[http://www.diskinternals.com/linux-reader/](http://www.diskinternals.com/linux-reader/)

Jim

---

### Post by ryanhaigh on 2008-06-20
You have made the problem a little unclear. From your first post it sounded like you were trying to access files on an ntfs (windows) partition from linux and only some files were being shown while all files are shown in windows. Now you are talking about a second disk what that is empty in windows, should there be something on it? If as cariboo907 suggests you are trying to access a linux ext3 partition from windows you will need a driver for the ext filesystem for windows. I have personally not used the software cariboo907 links to but I have had success [with this]("http://fs-driver.org/").

I think you need to clarify the problem you are having before we can assist you further.

---

