---
title: "Mozilla Firefox wont run"
date: 2005-09-23
forum: General Help
---

### Post by arlie on 2005-09-23
I got this error after I tried updating mozilla and mozilla wont run 
anymore:

E: /var/cache/apt/archives/mozilla-firefox_1.0.7-0ubuntu0.1_i386.deb:  
trying to overwrite `/var/lib/mozilla-firefox/extensions.d/00classic', 
which is also in package firefox
E: 
/var/cache/apt/archives/mozilla-firefox-gnome-support_1.0.7-0ubuntu0.1_i386.deb:  
trying to overwrite 
`/usr/lib/mozilla-firefox/components/libmozgnome.so', which is also in 
package firefox-gnome-support

---

### Post by TristanMike on 2005-09-23
[Here's](http://ubuntuforums.org/showthread.php?p=368149#post368149) what I did to fix it.  :)

Oh, and as for the errors, I didn't worry about them cause this fixed it and the update is gone.

---

### Post by arlie on 2005-09-25
I did sudo apt-get update and below was the screen output. So I did not proceed with the rest of the instruction.

Failed to fetch [http://ph.archive.ubuntu.com/ubuntu/dists/hoary-updates/restricted/source/Sources.gz](http://ph.archive.ubuntu.com/ubuntu/dists/hoary-updates/restricted/source/Sources.gz)  Could not connect to ph.archive.ubuntu.com:80 (82.211.81.151). - connect (111 Connection refused) [IP: 82.211.81.151 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/main/source/Sources.gz)  Could not connect to us.archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/restricted/source/Sources.gz)  Could not connect to us.archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Mustard on 2005-09-25
The repositories are broken.  The problem is outside your system.

When they fix the repositories you should be able to follow the how to fix advice then.

---

### Post by arlie on 2005-09-25
[QUOTE=Mustard]The repositories are broken.  The problem is outside your system.

When they fix the repositories you should be able to follow the how to fix advice then.[/QUOTE]
 Ok. Thanks. I just wait until it's fixed. Is there an easy way to download and install an internet browser. I cannot surf with mozilla and cannot download konqueror also. I'm using another computer to surf. Please help.

---

### Post by Tiede on 2005-09-25
well, all the http repos are down, but the ftp ones are still holding on. Just temporarily change the entries in your sources.list from http to ftp to fix your problem.

---

