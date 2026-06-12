---
title: "GNOME --&gt; Places --&gt; Network Servers: Authentication required?"
date: 2005-10-31
forum: General Help
---

### Post by matthias_k on 2005-10-31
Hi,

whenever I open the "Network Servers" from the "Places" menu in the GNOME panel, I am asked to login to my own domain (192.168.1.10) in the MSHOME workgroup.

What do I have to enter there? My Unix login/password doesn't work.

Any ideas?

---

### Post by speedsix on 2005-10-31
I have the exact same problem :confused:

---

### Post by sphillips53 on 2005-10-31
I think the password it is asking for is the Samba password for your username.  If you have not set a Samba password you can do it by running the command:
sudo smbpasswd -a username
where username is the user on Ubuntu that you want to set up network acces for.  The -a option adds this user as a new user to the Samba configuration file and then asks you to supply a password which will be the one to use when you go into Network Servers in the future.

---

### Post by sphillips53 on 2005-11-01
See the thread   [http://www.ubuntuforums.org/showthread.php?t=80628](http://www.ubuntuforums.org/showthread.php?t=80628)  for another answer to this problem. You can get around having to set a Samba password for your Ubuntu user by editing the Samba configuration file smb.conf which is in the /etc/samba/ directory to change the line "security = user" to "security = share".  You lose some security, but the password to log in is not needed when you open Network servers in the Places menu.

---

