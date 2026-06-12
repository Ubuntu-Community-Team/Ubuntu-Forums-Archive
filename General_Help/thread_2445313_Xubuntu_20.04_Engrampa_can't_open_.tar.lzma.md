---
title: "Xubuntu 20.04 Engrampa can't open .tar.lzma"
date: 2020-06-12
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2020-06-12
[ATTACH=CONFIG]286191[/ATTACH]
file created using:
[FONT=courier new]tar cfa /tmp/archive.tar.lmza ./[/FONT]

EDIT:
Please not post 7 here: [https://ubuntuforums.org/showthread.php?t=2445313#post13965346](https://ubuntuforums.org/showthread.php?t=2445313#post13965346)
Engrampa only seems to fail if the tar.lzma was made using tar 1.3, if you make it using 1.32 it works fine

EDIT: Sample archives: [https://github.com/mate-desktop/engrampa/files/4781327/testArchives.zip](https://github.com/mate-desktop/engrampa/files/4781327/testArchives.zip)

---

### Post by ActionParsnip on 2020-06-12
[https://www.cyberciti.biz/faq/open-extract-lzma-under-rhel-centos-debian-ubuntu/](https://www.cyberciti.biz/faq/open-extract-lzma-under-rhel-centos-debian-ubuntu/)

---

### Post by pqwoerituytrueiwoq on 2020-06-12
That is not the point, i know i can extract it with other software
If i make the archive using Engrampa it is able to open it, am i making the archive correctly?
if i rename the archive i made using the tar command to [FONT=courier new]archive.tar.xz[/FONT] Engrampa can open it

---

### Post by norobro on 2020-06-12
I don't see "lzma" in the list of supported file extensions for engrampa: [https://github.com/mate-desktop/engrampa/blob/master/README#L16](https://github.com/mate-desktop/engrampa/blob/master/README#L16)

From the xz man page:> [FONT=monospace][SIZE=2][COLOR=#000000]The native file format is the [/COLOR][COLOR=#000000]**.xz**[/COLOR][COLOR=#000000] format, but the legacy [/COLOR][COLOR=#000000]**.lzma**[/COLOR][COLOR=#000000] format ...[/COLOR][/SIZE]
[/FONT]I guess that the decision was made not to support the legacy format. If I try to create an lzma archive with the GUI, the add files and add folder icons are disabled.

---

### Post by Yellow Pasque on 2020-06-12
Try naming the file something.tzma
Any difference?

---

### Post by pqwoerituytrueiwoq on 2020-06-12
Step 1:
[ATTACH=CONFIG]286194[/ATTACH]
Step 2:
[ATTACH=CONFIG]286193[/ATTACH]

```
$ mimetype *.tar.lzma
guimade.tar.lzma: application/x-lzma-compressed-tar
tarMade.tar.lzma: application/x-lzma-compressed-tar
```

---

### Post by pqwoerituytrueiwoq on 2020-06-14
Seems that Engrampa is unable to open the file if it is made using tar 1.3, if made using 1.32 it works fine
[https://github.com/mate-desktop/engrampa/issues/393#issuecomment-643774230](https://github.com/mate-desktop/engrampa/issues/393#issuecomment-643774230)

---

### Post by norobro on 2020-06-14
Fooled around with this a little and noticed that the window that opens when a .lzma file is clicked in engrampa is from file-roller. So I removed file-roller from my system (apt-get remove file-roller) and engrampa works fine. So it looks to me that the problem is with file-roller and not engrampa or tar.```
$ lsb_release -dc
Description:    Ubuntu 19.10
Codename:    eoan
```

---

### Post by pqwoerituytrueiwoq on 2020-06-14
file roller was not installed for me
```
$ apt-cache policy file-roller 
file-roller:
  Installed: (none)
  Candidate: 3.36.2-0ubuntu1
  Version table:
     3.36.2-0ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages
     3.36.1-1ubuntu0.1 500
        500 http://security.ubuntu.com/ubuntu focal-security/main amd64 Packages
     3.36.1-1 500
        500 http://us.archive.ubuntu.com/ubuntu focal/main amd64 Packages
```

---

### Post by norobro on 2020-06-14
**EDIT: ignore - using wrong file name**


Odd. As I said, I experienced the error with file-roller installed but engrampa works fine after removing it.```
$ apt-cache policy tar engrampa
tar:
  Installed: 1.30+dfsg-6
  Candidate: 1.30+dfsg-6
  Version table:
 *** 1.30+dfsg-6 500
        500 http://us.archive.ubuntu.com/ubuntu eoan/main amd64 Packages
        100 /var/lib/dpkg/status
engrampa:
  Installed: 1.22.1-2
  Candidate: 1.22.1-2
  Version table:
 *** 1.22.1-2 500
        500 http://us.archive.ubuntu.com/ubuntu eoan/universe amd64 Packages
        100 /var/lib/dpkg/status
```

---

### Post by norobro on 2020-06-14
**EDIT:** ignore - using wrong file name


Just FYI, I upgraded to 20.04 and engrampa still handles .lzma files.```
$ lsb_release -dc
Description:   Ubuntu 20.04 LTS
Codename:    focal

$ apt-cache policy tar engrampa
tar:
  Installed: 1.30+dfsg-7
  Candidate: 1.30+dfsg-7
  Version table:
 *** 1.30+dfsg-7 500
        500 http://us.archive.ubuntu.com/ubuntu focal/main amd64 Packages
        100 /var/lib/dpkg/status
engrampa:
  Installed: 1.24.0-2
  Candidate: 1.24.0-2
  Version table:
 *** 1.24.0-2 500
        500 http://us.archive.ubuntu.com/ubuntu focal/universe amd64 Packages
        100 /var/lib/dpkg/status
```

---

### Post by Yellow Pasque on 2020-06-14
> **norobro said:**
> Just FYI, I upgraded to 20.04 and engrampa still handles .lzma files.

Plain .lzma files do not seem to be an issue. It's .tar.lzma that is the issue.

---

### Post by norobro on 2020-06-15
DOH! @Yellow Pasque you are correct. Apologies for wasting bandwidth!

---

### Post by ActionParsnip on 2020-06-15
Does unp extract it OK? It's one of my favourites.

---

### Post by pqwoerituytrueiwoq on 2020-06-15
I can extract using nautilus, tar, and file-roller just fine
added a link to sample archives in the 1st post

---

