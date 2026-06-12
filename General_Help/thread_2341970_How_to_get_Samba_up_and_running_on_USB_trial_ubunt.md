---
title: "How to get Samba up and running on USB trial ubuntu"
date: 2016-11-02
forum: General Help
---

### Post by McBeef on 2016-11-02
So I have a USB trial ubuntu on an otherwise dead laptop and I want to backup some data from this laptop to another laptop running windows 10. I did a bit of reading and mostly the internet seemed to point me in the direction of a package called Samba. With Samba I *should* be able to create a shared directory on the ubuntu laptop which would be accessible to the windows laptop over the network. Moving the data then becomes a simple matter of copying it to the shared directory and then retrieving it over the network from the windows 10 laptop. However, when I entered "sudo apt-get install Samba" I get the response "E: unable to locate package Samba". So do I get Samba up and running? Or is that even necessary, does the basic install already have everything I need to setup a share that can visible to windows?

---

### Post by kpatz on 2016-11-02
Linux and Ubuntu is case sensitive, and the package is called samba with a lowercase s, not Samba.

This command should work:```
sudo apt-get install samba
```

---

### Post by McBeef on 2016-11-02
> **kpatz said:**
> Linux and Ubuntu is case sensitive, and the package is called samba with a lowercase s, not Samba.t
This command should work:```
sudo apt-get install samba
```

a. thanks for responding and b. wow I feel pretty dumb. If I could trouble you just a bit more:

The next step is to add a user and password, per the example I found online:

> ubuntu@ubuntu:~$ sudo smbpasswd -a Shais
New SMB password:
Retype new SMB password:
Failed to add entry for user Shais.

Through several attempts I can attest the probem is not due to the passwords not matching. The UI mentioned something about restarting the session when I setup the share. Might that have something to with it? Since I'm running off of the USB, everything resets back to its original state across reboots which would be self defeating. At least that is how I understand it?

Any suggestions?


EDIT: nvm. I figured it out. Thank you for your help.

---

