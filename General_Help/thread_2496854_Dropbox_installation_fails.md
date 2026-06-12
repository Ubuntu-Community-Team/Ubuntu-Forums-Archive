---
title: "Dropbox installation fails"
date: 2024-04-14
forum: General Help
---

### Post by cbiweb on 2024-04-14
Running Ubuntu 22.04, fully updated

Trying to install the Dropbox app via terminal, using these instructions on the Dropbox site itself:

- - - - - - - - - -
```
cd ~ && wget -O - "https://www.dropbox.com/download?plat=lnx.x86_64" | tar xzf -
```Next, run the Dropbox daemon from the newly created .dropbox-dist folder.
```
~/.dropbox-dist/dropboxd
```
- - - - - - - - - -

All seem to be going well until this message appears in terminal, and it just stops there. Cursor blinking, never finishing:
```
(dropbox:15236): LIBDBUSMENU-GLIB-WARNING **: 23:06:30.953: About to Show called on an item wihtout submenus.  We're ignoring it.
```

Any suggestions for a fix?

---

### Post by cbiweb on 2024-04-23
Does anyone know how to get Dropbox installed on Ubuntu?

Instead of the above method, I tried installing the .deb file in terminal, and got dependency errors.

Any help would be greatly appreciated.

---

### Post by #&amp;thj^% on 2024-04-23
I'm not sure why you are having problems, possibly due to snap firefox.

And 24.04 is not quite out of beta stage yet.

Any who mine went well on 24.04 Noble
```
 cd ~ && wget -O - "https://www.dropbox.com/download?plat=lnx.x86_64" | tar xzf -
```
My return went like this:
```
--2024-04-23 10:07:25--  https://www.dropbox.com/download?plat=lnx.x86_64
Resolving www.dropbox.com (www.dropbox.com)... 162.125.4.18, 2620:100:6019:18::a27d:412
Connecting to www.dropbox.com (www.dropbox.com)|162.125.4.18|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: https://edge.dropboxstatic.com/dbx-releng/client/dropbox-lnx.x86_64-197.4.7571.tar.gz [following]
--2024-04-23 10:07:26--  https://edge.dropboxstatic.com/dbx-releng/client/dropbox-lnx.x86_64-197.4.7571.tar.gz
Resolving edge.dropboxstatic.com (edge.dropboxstatic.com)... 162.125.80.22, 2620:100:6030:22::a27d:5016
Connecting to edge.dropboxstatic.com (edge.dropboxstatic.com)|162.125.80.22|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 116465452 (111M) [application/gzip]
Saving to: ‘STDOUT’

-                   100%[===================>] 111.07M  5.94MB/s    in 20s     

2024-04-23 10:07:47 (5.49 MB/s) - written to stdout [116465452/116465452]

&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>
&#9474;~ 
&#9492;&#9472;> ~/.dropbox-dist/dropboxd
dropbox: load fq extension '/home/me/.dropbox-dist/dropbox-lnx.x86_64-197.4.7571/cryptography.hazmat.bindings._openssl.abi3.so'
dropbox: load fq extension '/home/me/.dropbox-dist/dropbox-lnx.x86_64-197.4.7571/cryptography.hazmat.bindings._padding.abi3.so'
dropbox: load fq extension '/home/me/.dropbox-dist/dropbox-lnx.x86_64-197.4.7571/apex._apex.abi3.so'
dropbox: load fq extension '/home/me/.dropbox-dist/dropbox-lnx.x86_64-197.4.7571/psutil._psutil_linux.cpython-38-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/me/.dropbox-dist/dropbox-lnx.x86_64-197.4.7571/psutil._psutil_posix.cpython-38-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/me/.dropbox-dist/dropbox-lnx.x86_64-197.4.7571/google._upb._message.cpython-38-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/me/.dropbox-dist/dropbox-lnx.x86_64-197.4.7571/tornado.speedups.cpython-38-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/me/.dropbox-dist/dropbox-lnx.x86_64-197.4.7571/wrapt._wrappers.cpython-38-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/me/.dropbox-dist/dropbox-lnx.x86_64-197.4.7571/PyQt5.QtCore.so'
dropbox: load fq extension '/home/me/.dropbox-dist/dropbox-lnx.x86_64-197.4.7571/PyQt5.sip.so'
dropbox: load fq extension '/home/me/.dropbox-dist/dropbox-lnx.x86_64-197.4.7571/PyQt5.QtGui.so'
dropbox: load fq extension '/home/me/.dropbox-dist/dropbox-lnx.x86_64-197.4.7571/PyQt5.QtWidgets.so'
dropbox: load fq extension '/home/me/.dropbox-dist/dropbox-lnx.x86_64-197.4.7571/PyQt5.QtDBus.so'



```
And a new tab to signin  to dropbox opens fine. See screenshot

The 64bit .deb has not been built for Noble properly yet.

---

### Post by cbiweb on 2024-04-25
> **1fallen said:**
> I'm not sure why you are having problems, possibly due to snap firefox.

And 24.04 is not quite out of beta stage yet.

Sorry, I mistyped.  I'm using 22.04.  Corrected in my original post.

---

### Post by #&amp;thj^% on 2024-04-26
Thanks for that, but what is your firefox installed as?
```
apt policy firefox
```

I'm not a snap user so mine will look different.
```
 apt policy firefox
firefox:
  Installed: 125.0.2~build1
  Candidate: 125.0.2~build1
  Version table:
     1:1snap1-0ubuntu5 500
        500 http://us.archive.ubuntu.com/ubuntu noble/main amd64 Packages
 [COLOR="#B22222"]*** 125.0.2~build1 1000
       1000 https://packages.mozilla.org/apt mozilla/main amd64 Packages[/COLOR]
        100 /var/lib/dpkg/status
     125.0.1~build1 1000
       1000 https://packages.mozilla.org/apt mozilla/main amd64 Packages
     124.0.2~build1 1000
       1000 https://packages.mozilla.org/apt mozilla/main amd64 Packages
     124.0.1~build1 1000
       1000 https://packages.mozilla.org/apt mozilla/main amd64 Packages
     124.0~build1 1000
       1000 https://packages.mozilla.org/apt mozilla/main amd64 Packages
     123.0.1~build1 1000
       1000 https://packages.mozilla.org/apt mozilla/main amd64 Packages
     123.0~build3 1000
       1000 https://packages.mozilla.org/apt mozilla/main amd64 Packages
     122.0.1~build1 1000
       1000 https://packages.mozilla.org/apt mozilla/main amd64 Packages
     122.0~build2 1000
       1000 https://packages.mozilla.org/apt mozilla/main amd64 Packages

```

---

### Post by cbiweb on 2024-04-27
> **1fallen said:**
> ...what is your firefox installed as?

```
firefox:
  Installed: 1:1snap1-0ubuntu2
  Candidate: 1:1snap1-0ubuntu2
  Version table:
 *** 1:1snap1-0ubuntu2 500
        500 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 Packages
        100 /var/lib/dpkg/status

```

---

