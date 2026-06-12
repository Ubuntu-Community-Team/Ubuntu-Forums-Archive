---
title: "Need help to write a (simple) script"
date: 2016-04-13
forum: General Help
---

### Post by Le3eVolfoni on 2016-04-13
Hello,

Im installing ubuntu on my parent's computer (former vista..). I found everything to please my mother but one script. And she won't use ubuntu unless this small tiny script is here.

The script purpose is merely to save changes that have been made in the "documents" folder on the external HDD to the "documents" folder on the computer's HDD (even if it seems so, I didn't say it backward. Not my computer)

My sister already wrote the script, but for windows.

```
xcopy/Y/S/D "xxxxxx" "xxxxx"

pause
```

I would probably place the script in the launcher, or, if not possible, on the desktop.

Any help would be highly appreciated.

---

### Post by T.J. on 2016-04-13
> **Le3eVolfoni said:**
> Hello,

Im installing ubuntu on my parent's computer (former vista..). I found everything to please my mother but one script. And she won't use ubuntu unless this small tiny script is here.

The script purpose is merely to save changes that have been made in the "documents" folder on the external HDD to the "documents" folder on the computer's HDD (even if it seems so, I didn't say it backward. Not my computer)

My sister already wrote the script, but for windows.

```
xcopy/Y/S/D "xxxxxx" "xxxxx"

pause
```

I would probably place the script in the launcher, or, if not possible, on the desktop.

Any help would be highly appreciated.

Sorry about the delay. I actually had to look up documentation on xcopy.  I haven't bothered to write a Windows script in about 15 years.  

Linux uses the standard "cp" to copy files. So if you wanted to just copy the files, cp -R "~/<name of documents folder>" "<name of mounted folder on external drive>".  If you want something that copies only changed files I would use rsync instead:  rsync -avz --update --existing source/ destination.  You might need to install rsync first.


I'm sorry I can be more specific - give you a working script -  without knowing the path of the Documents folder and the path of the external drive after it is mounted.  The default folder for Documents is usually named "Documents" but the external hardrive's path can vary depending on your version of Linux, and drive's ID, and who mounted it - for security reasons.

If you can provide me with more information I'll help you knock together a working replacement.

---

### Post by coldraven on 2016-04-13
This solution is probably complete overkill but as I only discovered it today I thought it might be worth a look.
It also might be difficult because you are using an external drive. Anyway I put it for future reference but wait for a more practical solution from someone else.
[https://www.howtoforge.com/tutorial/how-to-run-commands-on-file-or-directory-changes-with-incron-on-ubuntu-15-10/](https://www.howtoforge.com/tutorial/how-to-run-commands-on-file-or-directory-changes-with-incron-on-ubuntu-15-10/)

---

### Post by Le3eVolfoni on 2016-04-14
Thanks for these fast answers.

The rsync script works great. I slightly changed the line you proposed to have

```
rsync -avz --update /media..../ /mnt...
```

It seems to be exactly what I needed (the folder is a few gb big, that's why I didn't use the cp command).

Thanks for the help

---

### Post by T.J. on 2016-04-14
You're very welcome. Please mark the thread as solved or post again if I can be of help. :D

---

