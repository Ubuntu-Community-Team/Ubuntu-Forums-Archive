---
title: "Installing Picasa"
date: 2007-10-27
forum: General Help
---

### Post by gavinjb on 2007-10-27
Hi,

I have been trying to install Picasa and found the following web page ([http://picasa.google.com/linux/faq.html](http://picasa.google.com/linux/faq.html)) which has a Debian/Ubuntu Repository listed on it, only problem is that when I run apt-get update after adding the entry to the source I get the following error message.

```

W: GPG error: http://dl.google.com stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: You may want to run apt-get update to correct these problems

```

Does anyone know where I can get the key from or get this to work.

Thanks,



Gavin,

---

### Post by jayaramk on 2007-10-27
why use the apt get.. if you double click the debian package its istalled automaticallyyy

---

### Post by gavinjb on 2007-10-27
yes, but at least with apt-get I will get update notifications when/if new versions are released while if installing manually I have to remember to check

---

### Post by gavinjb on 2007-10-27
I found the key at the following web page, trust google not to include both on the same page.

[http://www.google.com/linuxrepositories/aboutkey.html](http://www.google.com/linuxrepositories/aboutkey.html)

---

