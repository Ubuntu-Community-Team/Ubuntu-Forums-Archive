---
title: "Changing file extensions ending with the ~-sign"
date: 2014-08-30
forum: General Help
---

### Post by DeMus on 2014-08-30
Hi,

I just restored my .thunderbird folder from an external harddisk to my home folder. I started thunderbird and normally it will find my mail, contacts and appointments automatically. Now it didn't and I could open a new account.
I looked in the hidden .thunderbird folder and saw that all my files have an extension ending with ~
I don't really know how that happened although I suspect making the back-up using grsync might have caused it. This is not important right now.
First I need to know how I can batch rename all the files ending with ~ to the original names.
The .thunderbird folders contains subdirectories and sub-sub directories. In all those subfolders files also have wrong names now.

Please help. This is my only back-up of all my e-mails and I sure don't want to loose them.

Thank you so much.

Edit: it is not only the file extensions, also files without extensions have their names ending with the ~ sign.

---

### Post by DeMus on 2014-08-30
I mark this thread as solved since my e-mail is working again. Working after a lot of work.
I started with this instruction I found using Google:
```
find . -name '*.jpg~' -exec sh -c 'mv "$0" "${0%jpg~}jpg"' {} \;
```
Since I had a lot of different extension names I used this instruction often, each time with a different extension name.
I then had to manually change some more files without extensions where the filenames had a ~-sign at the end.
Now it is all working again.

Short explanation:
I always used Thunderbird as my mail program. 2 Weeks ago I moved to Kmail, which worked at the beginning. I soon found out making a back-up copy is not that easy (with Thunderbird it is just copying the whole folder .thunderbird).
I then wanted to move back to Thunderbird where I found out that importing mail from Kmail is not that easy.
I decided to use my 2-weeks old backup from Thunderbird and import the newer mails from Gmail. Unfortunately my old back-up was misformed. I still don't know why, something I have to find out now.

---

