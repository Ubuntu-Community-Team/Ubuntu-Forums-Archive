---
title: "Windows My Documents"
date: 2007-05-06
forum: General Help
---

### Post by mnmmichael on 2007-05-06
I have a shared partition that I use for both Windows and Ubuntu. It is a FAT32 partition.

I am able to share things between the operating systems fairly well for the most part.

There is one problem: when I change the location of "My Documents" in Windows to a partition on the shared drive, I can read the folder fine in Windows. However, in Ubuntu, the folder shows up as "Read Only" and I can't access it. Any suggestions?

Basically, I get no problem until I "mount" the My Documents folder to the new folder. I know that I can have the folder shared without it, but it's a nice feature because a lot of programs [Microsoft Office, OpenOffice.org] default file saving to the My Documents folder.

---

### Post by Theimon on 2007-05-06
Take ownership of the folder. Since your not the owner Ubuntu will not allow you to write to the folder. Type "man chown" and " man chmod" (without quotes) in the terminal for the right commands.

---

### Post by mnmmichael on 2007-05-06
Hello,

When I try chmod and chman, I get a message saying:

*changing permissions of `My Documents': Operation not permitted*

These are the file permissions:

*drwxr-x---  7 root plugdev 16384 2007-05-06 15:42 My Documents*

Compared to a folder which I can access:

*drwxrwx--- 12 root plugdev 16384 2007-04-22 14:46 Music*

These were the original perissions of the My Documents folder:

*dr-xr-x---  7 root plugdev 16384 2007-05-06 15:42 My Documents*

But I managed to change it to allow the first "w"...no clue what it means though.

Any clue on what to do now?

---

### Post by GuitarRocker2562 on 2007-05-06
did you make sure do type sudo before chmod?

---

### Post by mnmmichael on 2007-05-06
I did "sudo su" before all of this. Would doing just plain "sudo" help?

---

### Post by mnmmichael on 2007-05-06
I found out that I needed to change permissions for the entire partition, even though this was the only problematic folder.

I did *sudo chmod r+w -R /media/sda3* and my problem was solved.

---

