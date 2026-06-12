---
title: "urgent: how can I mount a loopdevice in a LIVEDVD session"
date: 2007-02-10
forum: General Help
---

### Post by rupert on 2007-02-10
Hi,
when i try to open an encrypted loopdevice i get the message that 
ihave to check the kernel support for aes-cbc-essiv:sha256 and I should check that the loopdevice has at least 133 sectors.
What can I do now?

Can someone please help, I have to get this working today .


thx

rupert

sorry for the wrong headline

---

### Post by ciscosurfer on 2007-02-10
> **rupert said:**
> Hi,
when i try to open an encrypted loopdevice i get the message that 
ihave to check the kernel support for aes-cbc-essiv:sha256 and I should check that the loopdevice has at least 133 sectors.
What can I do now?

Can someone please help, I have to get this working today .


thx

rupert

sorry for the wrong headlineThe solution to this problem will go beyond the scope of this answer, but to start, if you want to mount a loopback device you would use syntax similar to the following [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount.2Funmount_Image_.28ISO.29_files_without_burning](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount.2Funmount_Image_.28ISO.29_files_without_burning)

These links may be of further assistance as well:
[http://www.kerneli.org/howto/node3.php](http://www.kerneli.org/howto/node3.php)
[http://www.ppcnerds.org/displayarticle186.html](http://www.ppcnerds.org/displayarticle186.html)
[http://cryptmount.sourceforge.net/](http://cryptmount.sourceforge.net/)
[http://www.linuxjournal.com/article/6481](http://www.linuxjournal.com/article/6481)

---

