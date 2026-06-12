---
title: "vsftpd user management problems"
date: 2015-09-08
forum: General Help
---

### Post by thehappiestturtle on 2015-09-08
Hello, 

I have setup a vsftpd FTP server on a machine I recently built running Ubuntu 14.04 LTS.  We will be using this server to FTP lots of data to clients.   We have setup 20 FTP users within Ubuntu, so not virtual users within vsftpd.  These users have all been chroot to their home directories.  So far it has worked well with a few minor annoyances I would like some help solving. 

A) We have a 1TB SSD as the primary drive and a 4TB HDD as the secondary drive. We would like to move all of the FTP users home directories to a folder on the secondary 4TB drive.  something like "sdb /FTP Users/FTPuser1, FTPuser2, etc".  What would be the best way to accomplish this? 

B) Currently we have to use the command line and use a sudo mv command to move data to the home directory of the FTP user.  Is there anyway it would be possible to drag and drop the files to the home directories? After we move the home directory to the secondary drive it would be ideal for the end user to be able to simply open a folder from an external drive and drag it over to the the folder on the 4TB drive, rather than going through the trouble of typing out all the mv commands.  Especially because the user likes to use complex naming conventions for the files.

C) Some of clients are requesting SSH. Is there any easy way of granting SSH capabilities to a few of these users and still ensure they are chroot and cant get out? 

Thank you for any help!

---

### Post by XBNCPRk on 2015-09-09
A) Depending on how you have your users set up, the usermod command can move their home directories and their associated contents. It should also update the /etc/passwd file to reflect their new locations. Im fairly certain however that it will not update any .conf files you may have with expressly stated file paths. 

B) There is no drag and drop functionality for the terminal obviously, so what you can drag and drop with will be dependent on how you and your clients are accessing the ftp share. From a win machine there are many ftp clients that can enable this (I prefer filezilla), or you can mount the ftp share directly in windows explorer. *nix machines can similarly mount the share to a specified mount point. 

C) You can enable SSH/SFTP for the connection [http://xmodulo.com/secure-ftp-service-vsftpd-linux.html](http://xmodulo.com/secure-ftp-service-vsftpd-linux.html) It only changes how the connection is made, not the behaviour or permissions of the shares.

---

### Post by Lars Noodén on 2015-09-09
> **thehappiestturtle said:**
> C) Some of clients are requesting SSH. Is there any easy way of granting SSH capabilities to a few of these users and still ensure they are chroot and cant get out?

Chrooted SFTP is fairly easy but not full SSH.  Giving SSH would give them shell access.  Maybe what they meant was SFTP, which you get as part of the OpenSSH-server package.  The only catch with chrooted SFTP with OpenSSH-server is that the chrooted directory itself has to be owned by root, but the files and subdirectories can be owned by the user.  

[https://en.wikibooks.org/wiki/OpenSSH/Cookbook/SFTP#Chrooted_SFTP-only_Accounts](https://en.wikibooks.org/wiki/OpenSSH/Cookbook/SFTP#Chrooted_SFTP-only_Accounts)

Also, SFTP is not FTPS, and I'd avoid the latter and would go as far as possible to avoid plain FTP considering those accounts already compromised.

---

### Post by XBNCPRk on 2015-09-09
I thought that SSH is required for elevated privledges, not that it granted it by default? Wouldnt the same privledges and restrictions apply for a standard (non super) user apply regardless of what method is used to connect?

---

