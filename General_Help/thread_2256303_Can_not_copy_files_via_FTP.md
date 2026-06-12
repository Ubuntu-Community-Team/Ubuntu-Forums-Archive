---
title: "Can not copy files via FTP"
date: 2014-12-11
forum: General Help
---

### Post by sixdeuce062 on 2014-12-11
So I have Ubuntu 14.04.01 installed and I am trying to access a SDcard in a security camera via ftp from the command line. I can use filezilla all day on any OS and grab files 100% of the time however, I want to use a script and and stick in in cron and have it back up daily so I need to be able use FTP from the command line so I can script it. I am not worried about getting the script ironed out but I can not copy files via FTP from the command line with out getting a 550 permissions denied error every time I manually try copy a file. But like I said earlier I can open up filezilla client and copy files all day long. I have run FTP as root in passive and binary, turned of the firewall, put server/camera on a LAN and copied the settings of filezilla as close as I can tell but still cant copy files. I can login into the camera and look around but cant copy files what am I missing ?

---

### Post by nerdtron on 2014-12-11
What are you settings in filezilla? Host, user, password (xxxx), and port? You should use the same credentials on the command line.
What commands are you using in the command that you get permission denied errors? Are you sure you are on the correct folder?

---

