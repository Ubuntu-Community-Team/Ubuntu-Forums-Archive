---
title: "Can't login GDM Desktop broken?"
date: 2007-09-14
forum: General Help
---

### Post by psyguy92 on 2007-09-14
Hi. I am unable to get to the files on Desktop. A normal login screen appears, and the other accounts work fine, but my main account logs in, then nothing appears on the desktop and nothing works.  

I tried to get the files from the desktop using another user. I had to boot directly into a root shell, and add another user to the admin/sudo group.  I could then access my main user's home folder, but when I try to cd to Desktop, ls ~Desktop, zip -r foo Desktop, ls Desktop > list.txt, or anything else, it acts like it is trying to do something, then freezes and won't give me a shell prompt back.  Additionally, I have a utility/driver installed on WinXP that allows read/write to the linux partition by assigning it a windows drive letter name.  It does not work either (says it is unformatted).

I am guessing it is not a GDM configuration error, because I can't even access ~/Desktop with a shell.  Also, I believe it is not a permissions problem, because I went as far as to login as root both with a shell and with a Gnome desktop, and still couldn't access the files.  I would really like to retrieve the files in ~/Desktop, and ideally would like to be able to fix my main user account, as I am unable to usefully login to it.

I don't have a problem wiping that user and making another, or even reinstalling, but I want my files back. /home/user/ is available, just not /home/user/Desktop.

Any ideas? :)

---

