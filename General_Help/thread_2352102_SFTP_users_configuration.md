---
title: "SFTP users configuration"
date: 2017-02-09
forum: General Help
---

### Post by lochness123 on 2017-02-09
Hello,

I configured SFTP on my server and now I want to configure some users. I had one users who can see everything (he had unlimited rights) and I want another user who will have limited rights. How can I do that?

---

### Post by TheFu on 2017-02-09
Learn about Linux file and directory permissions. 
sftp connections follow those.

There are lots and lots of books and online tutorials about this.  Standard, Unix, file and directory permissions.  
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions) is one.  Most colleges that teach Unix will have a similar page. There isn't any "short-cut" - just learn this now. That knowledge will pay off the rest of your life.

Unlimited is a bad idea for any remote file transfer.  Have an upload directory, then ssh in and move the files and set the permissions as needed.

---

