---
title: "Superuser password does not work..."
date: 2014-02-05
forum: General Help
---

### Post by daedalus2 on 2014-02-05
I installed ubuntu today, and set it up as a dual boot.  Once I got on ubunut however, and tried to install Adobe flash, my realm of knowledge ended.  I tried to do it with the "sudo get" command in the terminal, along with trying to isntall it from Adobe's website, and the Ubuntu store.  From what I can tell, all of these would have worked, however whenever I try to enter in my root (i think superuser aswell) password, it tells me it is incorrect.  If I am missing any information, ask me and I will probably remember.

Thank-you

---

### Post by grahammechanical on 2014-02-05
What exactly was the command that you typed. Usually we type

```
sudo apt-get install <package name>
```

After pressing enter we are asked for a password. The password that we set up when we installed Ubuntu is the one that works. Did the error message say the password was wrong or that the command was wrong.

If we search for "adobe" in the Ubuntu Software Centre we get directed to page that will offer to install for us "Adobe Flash Plugin - downloads and installs the Adobe Flash Player Plugin." So, we only install the installer. Note the warning given in the Info page. If we want to install it from the terminal then this is the correct command:

```
sudo apt-get install flashplugin-installer
```

I have just tested that command. Using an incorrect name for a package will get us a package not found error message.

Regards

---

### Post by bc.haynes on 2014-02-05
Do you have CAPS LOCK turned on?

---

