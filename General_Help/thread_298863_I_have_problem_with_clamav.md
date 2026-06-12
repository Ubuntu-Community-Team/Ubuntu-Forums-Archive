---
title: "I have problem with clamav"
date: 2006-11-13
forum: General Help
---

### Post by nevlode on 2006-11-13
Hi All
This is my first post at this forum.
I have a problem with clamav. This problem mabie is elemenary, still I found it dificult to resolve, since I am a new user of ubuntu.

Terminal displays errors:
After unpacking 0B of additional disk space will be used.
Setting up clamav-base (0.88.4-1ubuntu1~dapper1) ...
chown: cannot access `/var/run/clamav': No such file or directory
dpkg: error processing clamav-base (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of clamav-freshclam:
 clamav-freshclam depends on clamav-base (= 0.88.4-1ubuntu1~dapper1); however:
  Package clamav-base is not configured yet.
dpkg: error processing clamav-freshclam (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of clamav:
 clamav depends on clamav-freshclam | clamav-data; however:
  Package clamav-freshclam is not configured yet.
  Package clamav-data is not installed.
  Package clamav-freshclam which provides clamav-data is not configured yet.
dpkg: error processing clamav (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of clamassassin:
 clamassassin depends on clamav (>= 0.66); however:
  Package clamav is not configured yet.
dpkg: error processing clamassassin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of clamav-daemon:
 clamav-daemon depends on clamav-base (= 0.88.4-1ubuntu1~dapper1); however:
  Package clamav-base is not configured yet.
 clamav-daemon depends on clamav-freshclam | clamav-data; however:
  Package clamav-freshclam is not configured yet.
  Package clamav-data is not installed.
  Package clamav-freshclam which provides clamav-data is not configured yet.
dpkg: error processing clamav-daemon (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of clamav-getfiles:
 clamav-getfiles depends on clamav (>= 0.83); however:
  Package clamav is not configured yet.
 clamav-getfiles depends on clamav-freshclam; however:
  Package clamav-freshclam is not configured yet.
dpkg: error processing clamav-getfiles (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sylpheed-claws-gtk2-clamav:
 sylpheed-claws-gtk2-clamav depends on clamav; however:
  Package clamav is not configured yet.
dpkg: error processing sylpheed-claws-gtk2-clamav (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sylpheed-claws-clamav:
 sylpheed-claws-clamav depends on clamav; however:
  Package clamav is not configured yet.
dpkg: error processing sylpheed-claws-clamav (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 clamav-base
 clamav-freshclam
 clamav
 clamassassin
 clamav-daemon
 clamav-getfiles
 sylpheed-claws-gtk2-clamav
 sylpheed-claws-clamav
E: Sub-process /usr/bin/dpkg returned an error code (1)


And when I am going to set up some new programs I have same errors :(
Please help me how to fix this problem, this is very urgent and important for me.
Thank you in advance! :)

---

### Post by Derspankster on 2006-11-13
I wish I had an answer to your clamav problem but I have the same problem as you. I'm not having any other issues installing however. If I find an answer to our problem , I'll return an post another reply.

---

### Post by ReaderRat on 2006-11-13
Have you enabled the other repositories?
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by tokschi on 2006-12-18
I have the same problem. Did anybody find a real solution. All official repositories are swiched on on my system...

tokschi

---

### Post by tokschi on 2006-12-18
I solved the problem as follows:

deinstalled the pakage "clamav-base" using Synaptic
reinstalled "clamav-base" using Synaptic
installed the gnome security suite again using automatix

Now everything workes fine...

tokschi

---

