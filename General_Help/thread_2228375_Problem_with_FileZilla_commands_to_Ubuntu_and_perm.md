---
title: "Problem with FileZilla commands to Ubuntu and permissions"
date: 2014-06-07
forum: General Help
---

### Post by ronan_k on 2014-06-07
I have Ubuntu 10.4 on AWS EC2. I connect with mindterm then use a sftp to FTP bridge and use FileZilla or dreamweaver. I sudo bash to get root privileges from mindterm to access home directory. But I cannot delete or overwrite files. Get error 550. I see owner of files is root. Can't understand what is happening. Am I thick? What is best approach? Would prefer not to change file permissions. I thought maybe DELE command issued by FileZilla wasn't being recognised. Can anyone help? Thanks.

---

### Post by ronan_k on 2014-06-08
No one able to help? Just can't seem to crack it. Fairly inexperienced, mind...

---

### Post by ronan_k on 2014-06-09
All permissions for following file are open, and for good measure owner set to root:

-rwxrwxrwx  1 root  root   63746 2012-02-22 06:32 build.xml

I still get error 550...

---

