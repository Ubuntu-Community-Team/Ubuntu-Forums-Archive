---
title: "how to make amule support big file download?"
date: 2007-01-07
forum: General Help
---

### Post by henryluo on 2007-01-07
Hi, everyone.

I am using amule@ubuntu 6.06 , when I wanted to download a file big than 4GB, I got error " Invalid ed2k link! Error: Invalid file size", I knew the lastest emule version for windows had fixed this problem, can you give me any suggestion to fix this problem? thanks very much.

here is my amule version info:
aMule CVS using wxGTK2 v2.6.1 (Unicoded) (Snapshot: Wed Nov 30 07:01:58 CET 2005) (OS: Linux)

---

### Post by jjgomera on 2007-08-02
> **henryluo said:**
> Hi, everyone.

I am using amule@ubuntu 6.06 , when I wanted to download a file big than 4GB, I got error " Invalid ed2k link! Error: Invalid file size", I knew the lastest emule version for windows had fixed this problem, can you give me any suggestion to fix this problem? thanks very much.

here is my amule version info:
aMule CVS using wxGTK2 v2.6.1 (Unicoded) (Snapshot: Wed Nov 30 07:01:58 CET 2005) (OS: Linux)
Amule can't support big archive, maybe in next version

---

### Post by Hallvor on 2007-08-02
You can`t. But eMule has had large file support for a long time now, and it runs OK in Wine with a few glitches. If you have to download files larger than 4 gb on the ed2k network, you should use eMule + Wine. It also supports UPnP and protocol obfuscation, and is available in a lot of languages.

---

### Post by henryluo on 2007-11-14
the Amule CVS version support large file than 4GB now.  you can just add those link to your /etc/apt/sources.list
```
deb http://www.vollstreckernet.de/debian/ stable amule
deb http://www.vollstreckernet.de/debian/ stable wx
```

---

