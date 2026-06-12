---
title: "Sudo not working [Resolved]"
date: 2007-01-20
forum: General Help
---

### Post by 2kthunder on 2007-01-20
Hello,
I recently came a cross a bit of a problem, Sudo does nothing. I cannot restart the server, or execute any commands.


Running sudo does this:

john@iridium:~$ sudo reboot
john@iridium:~$ sudo -k
john@iridium:~$ sudo reboot
Password:
john is not in the sudoers file.  This incident will be reported.
john@iridium:~$ sudo reboot
john@iridium:~$


It just goes back to the prompt, it should be giving me the reboot line, and then restarting lol.

Anyone have any ideas?

TIA,
J

---

### Post by taurus on 2007-01-20
Did you change anything on your machine before this happened?  What are the outputs of these commands?

```
id
cat /etc/hostname
cat /etc/hosts
```

---

### Post by PilotJLR on 2007-01-20
Is this username "john" listed in the "admin" group in /etc/group?? Cause he needs to be...

---

### Post by 2kthunder on 2007-01-20
I dont even see an admin group, but I cant add it since I cant sudo nano the file.


I actually was trying to give a user access to a file, and did run usermod -Gblah to add a group, and everything else I did before I noticed was pretty run of the mill

Here is the output of the given commands:

john@iridium:~$ id
uid=1000(john) gid=1000(john) groups=33(www-data),1000(john)
john@iridium:~$ cat /etc/hosts
127.0.0.1       localhost
127.0.1.1       iridium

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
john@iridium:~$ cat /etc/hostname
iridium
john@iridium:~$



If I am not mistake, I recall being a member of a bunch  more groups than I am now

Thanks for the replies

---

### Post by taurus on 2007-01-21
Boot into recovery mode from GRUB menu and add john to both adm and admin.

```
adduser john adm admin
id john
```

---

### Post by 2kthunder on 2007-01-21
Alright thanks, I will have to wait a while though, the box is 200 miles away lol. Thanks for the help, I will reply when I can get to it and update.Thanks again.

---

### Post by 2kthunder on 2007-02-02
It worked! Thanks a bunch

---

