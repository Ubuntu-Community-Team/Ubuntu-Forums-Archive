---
title: "how to connect from Windows to Ubuntu"
date: 2007-12-11
forum: General Help
---

### Post by lulon on 2007-12-11
Hi!

This is my situation:

I have one computer with Ubuntu. In this computer I have an application with a Web Server, an Application Server and a DataBase.

I have another computer, a laptop, with Windows XP.

And now, this is my question:

How can I connect to the computer (with Ubuntu) from the laptop (with Windows XP) for doing operations like these: delete, create, modify files from the Application Server, stop and start the Web Server, etc.?

I hope that I have explain well, I'm not an English speaker...

Thanks a lot.

---

### Post by pointone on 2007-12-11
[http://www.openssh.com/](http://www.openssh.com/)

---

### Post by buntunub on 2007-12-11
Putty from the windows computer handles openssh. You also have samba. Wiki's for all that are on the community documentation area.

---

### Post by skymera on 2007-12-11
to control ubutnu from windows try PuTTY

---

### Post by r-mo on 2007-12-11
The 2 technologies you'll want to use are

SSH [https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)
and Samba [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

Although you could do it all with ssh, samba is probably a better way to transfer the files

---

### Post by el escocés on 2007-12-11
I like winSCP [http://winscp.net/eng/index.php](http://winscp.net/eng/index.php) for a GUI program or you can install cygwin [http://www.cygwin.com/](http://www.cygwin.com/) and command line your way in...

---

