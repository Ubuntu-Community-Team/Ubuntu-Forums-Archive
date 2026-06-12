---
title: "How can my friend throw few files to a folder on my computer?"
date: 2006-11-02
forum: General Help
---

### Post by brynjarh on 2006-11-02
I tried clicking on a folder and choosing Share and configured it but then nothing happend, how can my friends connect to my folder?

I set it to samba, windows, smb.

---

### Post by Sef on 2006-11-02
What operating system does your friend have and you have?

---

### Post by brynjarh on 2006-11-02
I have Ubuntu Edgy Eft and he has Windows XP.

---

### Post by marianom on 2006-11-02
If you just need that sometimes he transfers a few files to your machine and nothing more, try pscp:
[http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)

---

### Post by giants_fan on 2006-11-02
The best and most secure way for you to do this would be to:

1 - create an account for your friend (System->Administration->Users&Groups)

2 - install sshd (via apt-get or something)

3 - have your friend install winscp  ([winscp.net]("http://winscp.net")) or cygwin.

4 - then you can remove his account and/or stop the ssh service

---

### Post by matthewstory on 2006-11-02
yeah i'd use SFTP as well, have your friend get filezilla, install sshd make an account for him and tell him to SFTP to your box.

---

