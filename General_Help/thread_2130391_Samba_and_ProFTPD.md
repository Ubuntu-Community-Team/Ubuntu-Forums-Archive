---
title: "Samba and ProFTPD"
date: 2013-03-29
forum: General Help
---

### Post by roe74979 on 2013-03-29
I fully understand that Samba and ProftpD are not part of Ubuntu.  But I am using Ubuntu 12.10 to attempt to use those programs and hoping that someone can help me.  I am building a Samba server and FTP server for my capstone project in College. For Samba, I have created a user and PW and created correct permissions. But I still can not log into Samba via a Windows machine.  So I'm not sure what I'm missing. for FTP, I have installed ProftpD and that's about it.  I have installed Filezilla client on the Windows machine but I can not connect to the FTP server.  So if there is anyone that uses these forums that's familiar with either, please get in touch with me.  I have 6 weeks left and I'm stuck.  I'm still a but of a noob when it comes to Linux, but I'm pretty good at following directions..  thank you for your time and help

---

### Post by roe74979 on 2013-03-29
bump

---

### Post by roe74979 on 2013-03-31
bump

---

### Post by roe74979 on 2013-04-01
bump

---

### Post by lykwydchykyn on 2013-04-01
Is the server merely facilitating your college project, or is creating a samba/ftp server central to the project?  I don't think step-by-step instructions are appropriate if your project is intended to acquire and demonstrate competence in Linux, samba, and ftp.

If you need some pointers on setting up samba in Ubuntu, this would be a great place to start:  [https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba)
And for proftpd: [https://help.ubuntu.com/community/ProFTPD](https://help.ubuntu.com/community/ProFTPD)

Both services log errors to their own directories under /var/log, so that's a good place to start investigating if there are problems.

---

### Post by roe74979 on 2013-04-01
Samba and FTP are the project.  I have to build the samba server and succfully share a file to a windows PC, edit the file and be able to share it back ...

FTP i have to build a directory of different classes and again share a file within a directory and have a student retrieve the file.  

i know its not a terribly hard project, but its hard for me non the less  lol  

so i guess the answer to your question is its central to the project.   Thanks for the link, i'll take a look at it.

thanks for the responce

---

