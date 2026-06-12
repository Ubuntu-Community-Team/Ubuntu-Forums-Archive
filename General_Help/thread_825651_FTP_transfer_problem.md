---
title: "FTP transfer problem"
date: 2008-06-11
forum: General Help
---

### Post by dont_give_me_that_look on 2008-06-11
Hey
I got my music collection stored on a linux ftp server in my network. After transfering the files with FileZilla I noticed that some files were missing, in particular all files with special characters like é, ö, ...

The files are all on the server, but I can't get them on my PC. I tried this:

FileZilla: Doesn't recognize files with spezial characters
The built-in FTP client: Can only copy single files, not folders ('File is not available')
Terminal: ftp login, then 'get folder' gives me error 550

Does anyone have a suggestion?

---

### Post by Habbit on 2008-06-11
Try using Nautilus for the copy, it can sure as hell copy whole folders since I regularly use it for backing my website files up. Just enter the ftp address in the address bar and you're set.

---

### Post by anindya_m on 2008-06-11
gftp is also pretty good.

---

### Post by dont_give_me_that_look on 2008-06-11
> **Habbit said:**
> Try using Nautilus for the copy, it can sure as hell copy whole folders since I regularly use it for backing my website files up. Just enter the ftp address in the address bar and you're set.

That's what the default ftp client does, and when I copy/paste the folder it gives me 'file unavailable'. Then when I copy single files it works.

Trying gftp now. edit: works. Ty :)

---

