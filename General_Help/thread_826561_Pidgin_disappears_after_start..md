---
title: "Pidgin disappears after start."
date: 2008-06-12
forum: General Help
---

### Post by Vanderdan on 2008-06-12
dje tried to help in another thread and suggested starting a new one. 

After following his advice I still get errors. This is one of them. Any suggestions? I'm running ubuntu on a AMD64 machine. 

Reading package lists... Done
Building dependency tree 
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 13 not upgraded.
1 not fully installed or removed.
Need to get 572kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main pidgin 1:2.4.1-1ubuntu2 [572kB]
Fetched 572kB in 6s (94.4kB/s) 
(Reading database ... 117583 files and directories currently installed.)
Preparing to replace pidgin 1:2.4.1-1ubuntu2 (using .../pidgin_1%3a2.4.1-1ubuntu2_amd64.deb) ...
Unpacking replacement pidgin ...
Setting up msttcorefonts (2.4) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility". This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
subprocess post-installation script returned error exit status 1
Setting up pidgin (1:2.4.1-1ubuntu2) ...

Errors were encountered while processing:
msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by MmmmJoel on 2008-06-12
If you do not use a proxy, make sure "Direct internet connection" is chosen from: System -> Preferences -> Network Proxy. Then try again.

---

### Post by Vanderdan on 2008-06-12
That seems to have fixed it. Thank you.:)

---

