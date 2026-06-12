---
title: "ftp troubles"
date: 2007-07-11
forum: General Help
---

### Post by foug on 2007-07-11
I'm having trouble connecting to an ftp server of my friends. I need to enable secure listing and use AUTH SSL. Trying to connect through konqueror works somewhat, it shows me connected on his end but I don't see any files. I've tried kftpgrabber and I stay at waiting forever.

---

### Post by jarrett on 2007-07-11
where does kftpgrabber stall? after you've logged in? or doesn't it even connect?

---

### Post by Espreon on 2007-07-11
For FTPing I use FileZilla, It is a pretty good FTP client, it is fast, small and feature-filled. To install goto Applications>Add/Remove Applications
In the search box type filezilla and check the check box next to FileZilla. Hit apply after installation goto Applications>Internet>FileZilla
Enjoy!

---

### Post by foug on 2007-07-11
jarrett: not sure if it connects or not, didn't ask my friend if he saw me connected on the other end. But it opens a new tab where it shows my files, but they are all greyed out and it just says "waiting" at the bottom

Espreon: I need to add a repository I think, add/rmove showed nothing and apt-get firezilla couldn't find the package

---

### Post by munroe on 2007-07-11
```
sudo apt-get install filezilla
```

not fiRezilla. That should help.

---

### Post by dabl on 2007-07-11
gftp works pretty good for me, although I don't know about "auth ssl"  :)

---

### Post by foug on 2007-07-11
filezilla isn't working me either. My connection times out. I also tried Kasblanca and it crashes when i try to connect

---

### Post by foug on 2007-07-11
got filezilla working, thanks guys

---

### Post by divali on 2007-07-12
> **foug said:**
> got filezilla working, thanks guys

How?     Let's try to help other chaps in a similar situation.

:confused:

---

