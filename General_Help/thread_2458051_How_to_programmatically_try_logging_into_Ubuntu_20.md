---
title: "How to programmatically try logging into Ubuntu 20.04"
date: 2021-02-15
forum: General Help
---

### Post by shyam1287 on 2021-02-15
Lets imagine our workstation is been locked out. What are the commands or programmatic way to try logging into Ubuntu 20.04.

---

### Post by Impavidus on 2021-02-15
Forum policy doesn't allow us to tell you how to brute force a password, but I can direct you this this guide, telling how to reset your password: [https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword)

---

### Post by HermanAB on 2021-02-15
If you want to connect to a workstation over a network, use SSH.  

If you forgot your password, boot into Single User Mode and reset the password.

---

### Post by shyam1287 on 2021-02-15
Im not brute forcing the password. I just wanna know which maybe if there is a bash shell script that is capable of being an exe which can be accessed from cmdline?

---

### Post by HermanAB on 2021-02-15
Yes, it is called ssh.  Read the Snailbook.
[http://www.snailbook.com/](http://www.snailbook.com/)

---

### Post by shyam1287 on 2021-02-15
ya thats fine. But is it possible to anyone who doesnt have access to my system to successfully trying ssh into mine, and if so how do they generally do it. What methods do they use to break in? First of all the IP address doesnt stay constant and must mostly be the DHCP address. Also mostly the external adversaries must be able to access only my ISPs address. So how would they find mine within the subnet?

---

### Post by #&amp;thj^% on 2021-02-15
A few basic steps: [https://phoenixnap.com/kb/linux-ssh-security](https://phoenixnap.com/kb/linux-ssh-security)

---

### Post by HermanAB on 2021-02-15
There are script kiddies that will try tens of thousands of logins per hour and run alphabetically through all entries in large dictionaries of user names and passwords.  Generally, if you don't use the default SSH port number and use a long password of 14 characters or more, then you are safe.

---

### Post by grahammechanical on 2021-02-15
You start off by asking us to imagine someone locked out of a workstation. There is a way to overcome that if a person has physical access to the machine. Now. you have moved on to asking us how to access an computer remotely. You seem to already know something about this. If you need assistance in securing a machine, then this forum can help you. But as stated above it is against forum policy to advise on how security can be broken.

Regards

---

