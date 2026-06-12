---
title: "shell script - input password"
date: 2012-11-29
forum: General Help
---

### Post by icedutah on 2012-11-29
I am about to mass copy files from one server to another with rsync. It will be about 100 user accounts (below is just an example). I suck at shell code. But I am going to put this in a shell script to run. But the problem is after each line it will prompt for the server password. How can I automate this process? I know it would be insecure but it's just a one time thing to run.

#!/bin/sh
rsync -trl --progress -e ssh /home/scott/Maildir/ [email]scottm@172.16.0.58:/var/vmail/example.com[/email]/scott
rsync -trl --progress -e ssh /home/aaronp/Maildir/ [email]scottm@172.16.0.58:/var/vmail/example.com[/email]/aaronp
rsync -trl --progress -e ssh /home/allen/Maildir/ [email]scottm@172.16.0.58:/var/vmail/example.com[/email]/allen

---

### Post by papibe on 2012-11-29
Hi icedutah.

You can set SSH keys to automate unattended scripts. It should be a security issue as long as you follow the standard practices (file locations, permissions, etc).

Here are a couple of tutorials:  [SSH/OpenSSH/Keys]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys") and [Beginning SSH on Ubuntu]("http://principialabs.com/beginning-ssh-on-ubuntu/").

Hope it helps. Let us know how it goes.
Regards.

---

### Post by btindie on 2012-11-29
The above method would be the preferred solution but if you want to still use password then you can use sshpass. Take a look at "man sshpass" for an example.

You can then pass the password to ssh via a command line argument (not recommended), file, or environment variable SSHPASS.

If you then want to prompt for the password you can use
```
read -s -p "Password: " SSHPASS ; echo
```
The password will then be stored in the environmental variable SSHPASS.

---

