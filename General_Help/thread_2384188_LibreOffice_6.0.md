---
title: "LibreOffice 6.0"
date: 2018-02-03
forum: General Help
---

### Post by techee1-5 on 2018-02-03
Hi, I'm having fits getting this installed. I guess I need someone to help me, from where to download the file, to every single terminal entry. I couldn't even change directory right. Now I have a file that I can't delete. I really would appreciate the help. Thank you! I'm using Ubuntu 16.04, 64 bit, dual boot windows 7
(If this post belongs somewhere else, please move it and let me know, Thanks)

---

### Post by slickymaster on 2018-02-03
*Thread moved to **General Help**.*

---

### Post by irv on 2018-02-03
Go to [https://www.libreoffice.org/download/download/?type=deb-x86_64&version=6.0.0&lang=en-US]("https://www.libreoffice.org/download/download/?type=deb-x86_64&version=6.0.0&lang=en-US")
Download the .deb file.
It will download a zip file with all the .deb files you need to install.
It requires the recent version of Java Runtime Environment (JRE) for full functionality.
There is a readme file in the zip. You need to extract all the files and install each one.
Just install it and it should go to the right place.
I am using 5.0 and will wait until 6.0 comes with the install version of Ubuntu before installing it.
If you are a new user to Linux then I would wait until it comes with Ubuntu. 5.0 works great, and when new releases come out there are bugs that need to be worked out.

---

### Post by techee1-5 on 2018-02-03
Thanks irv. i installed this 16.04 awhile ago, and never added JRE.

---

### Post by TheFu on 2018-02-04
> **techee1-5 said:**
> Thanks irv. i installed this 16.04 awhile ago, and never added JRE.

I'm happy with whatever version is installed, but if I had this same issue, then I would look for a PPA.  Installing from files directly usually breaks the wonderful package management. If not today, then in 3-6 months as the rest of the system package are updated, but the .deb file isn't.  

1) If you can't use the default release, then use a PPA from a trusted source. 
2) If you can't do that, then get the .deb file, but set a reminder to get a new .deb file every month and manually patch it.  
3) If you can't do that, then get the source code and compile, install, manage the system 100% manually.

Only #1 integrates with the system maintenance, which is what I really, really, want.  The other choices are worse.

Package management on Ubuntu is an amazing thing. It is one of the main reasons I avoid Windows.

---

### Post by rbmorse on 2018-02-04
Is there a .ppa for 6.0?  I haven't been able to find it.

---

### Post by wildmanne39 on 2018-02-04
Hi rbmorse, the link is in post three, please do not hijack someone else's thread it is always better to create your own.

Thanks

---

### Post by rbmorse on 2018-02-04
Hardly a hijack. TheFu indicated (correctly) indicated that using the .ppa was more desirable than installing LibreOffice from the downloadable file packages. I can't find the .ppa for LibreOffice 6.0 and I don't see any reference to it in in the page linked on post three.

---

### Post by QIII on 2018-02-04
Yes, by definition that is a hijack:  you are not the OP and you sought and answer for your own question in the OP's thread.

Again:  Please do not hijack the threads of other users.  You have been asked by a Super Moderator and now an Admin.  

Thank you.

---

### Post by TheFu on 2018-02-05
Google found this: [https://wiki.ubuntu.com/LibreOffice#Installing_a_newer_version_of_LibreOffice_than_available_via_Ubuntu_repositories](https://wiki.ubuntu.com/LibreOffice#Installing_a_newer_version_of_LibreOffice_than_available_via_Ubuntu_repositories) v6 doesn't appear to be included, yet.  I'd wait until that group (LibreOffice PPA team) gets to it. 

"New" is the enemy of "stable" in my book.

---

