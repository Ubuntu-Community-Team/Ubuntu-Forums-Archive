---
title: "sync folder via FTP at start up"
date: 2014-12-15
forum: General Help
---

### Post by markosjal on 2014-12-15
I have a shared FTP space on a web server. I have files there that I want to sync to an ubuntu client at boot up. I need to know first off if I should or can do this with the simple FTP comand like

$ ftp server.com

If I do this however i then need to be abe to also automate the login username password as well as the file transfer commands

Additionally, where would I put this to have it autorun at boot up and how given I need to authenticate and run specific ftp commands.

---

### Post by kpatz on 2014-12-16
Does the web server allow ssh/sftp?  If it does, you can use rsync to sync your folders/files.

If you can install a ssh key on the server (may require shell access or something in the control panel) you can then log in and rsync without a password if you like.

---

### Post by nerdtron on 2014-12-16
> **markosjal said:**
> I have a shared FTP space on a web server. I have files there that I want to sync to an ubuntu client at boot up. I need to know first off if I should or can do this with the simple FTP comand like

$ ftp server.com

If I do this however i then need to be abe to also automate the login username password as well as the file transfer commands

Additionally, where would I put this to have it autorun at boot up and how given I need to authenticate and run specific ftp commands.

Closes answer to automating ftp commands is the ncftpput utility.
Check it out here: [http://www.cyberciti.biz/tips/linux-upload-the-files-and-directory-tree-to-remote-ftp-server.html](http://www.cyberciti.biz/tips/linux-upload-the-files-and-directory-tree-to-remote-ftp-server.html)
and here: [http://www.techrepublic.com/article/automate-your-ftp-transfers-with-ncftp-and-improve-your-efficiency/](http://www.techrepublic.com/article/automate-your-ftp-transfers-with-ncftp-and-improve-your-efficiency/)

You might also want to consider rsync it it support SSH/SFTP which is a much secure way.

---

