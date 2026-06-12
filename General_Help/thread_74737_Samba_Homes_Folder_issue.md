---
title: "Samba Homes Folder issue"
date: 2005-10-12
forum: General Help
---

### Post by HappyPappy on 2005-10-12
Hi gang, got my Ubuntu 5.04 done and am very happy so far.

One minor issue is that I can't get write access to my homes folder by using the homes share.

If I define a specific share to /home/happy everything works fine and I can read and write to that folder.

If I try to use the homes share for the happy user I can read the folder but can't write. 

I tried making the homes share writable = yes, read only = no, and all kinds of other parms with no luck.

Every time I to write I get "access denied". The error definitely appears to originate from Samba, all my system level rights appear ok.

The logs don't reveal anything noteworthy that I could see.

Any tips appreciated.

Thanks,

Happy

---

### Post by wylfing on 2005-10-12
It's kind of hard to understand what you're trying to do. Are you sharing your Ubuntu home directory, and then trying to access it from a Windows computer?

---

### Post by HappyPappy on 2005-10-12
Hi, I'm trying for each home folder to be accessible remotely from a Windows workstation where each user has a valid userid and home folder on the Ubuntu box.

---

### Post by Hobgoblin on 2005-10-12
[Did you do](http://www.ubuntuguide.org/#sharehomefoldersreadwritesecurityuser)?

I missed that bit and couldn't write to the home folders.

---

### Post by wylfing on 2005-10-12
And while reading the part about editing your smb.conf file, don't forget to follow the link about "adding network users." Follow all those instructions and you should be doing fine.

---

