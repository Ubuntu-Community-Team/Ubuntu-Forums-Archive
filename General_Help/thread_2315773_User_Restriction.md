---
title: "User Restriction"
date: 2016-03-02
forum: General Help
---

### Post by Rakesh_vijayan on 2016-03-02
I am in serious doubt and need to implement to specific area 

Scenario 
1)  A normal user , he can create file and folder in his home directory .he wouldn't  not permitted to delete folder and file weather created by root or himself  .is it possible to do this 

2) I configured vsftpd for file transfer.I need to limit that user to download the file not more thatn  3mb size .  I dig in google but I got answer "Is not possible in vsftpd" 
On that occasion i found an another way to restrict from this  
[URL="http://I am in serious doubt and need to implement to specific area   Scenario  1)  A normal user , he can create file and folder in his home directory .he wouldn't  not permitted to delete folder and file weather created by root or himself  .is it possible to do this   2) I configured vsftpd for file transfer.I need to limit that user to download the file not more thatn  3mb size .  I dig in google but I got answer &quot;Is not possible in vsftpd&quot;  On that occasion i found an another way to restrict from this   [link ][1]     [1]: [http://www.linuxsolved.com/forums/index.php?topic=2742.0](http://www.linuxsolved.com/forums/index.php?topic=2742.0)       /etc/security/limits.conf I set the user with fsize 1024 like      rv    hard  fsize  1024  it affect on system that if I copy file I will get following message       File size limit exceeded (core dumped) but while I tried to copy file by filezilla I can able to download 500mb file from my test server .Is there any solution for this ? or Any other ftp server provide the Maxdownloadfile parameter ?  Thanks In Advance"]

 http://www.linuxsolved.com/forums/index.php?topic=2742.0[/URL]


    /etc/security/limits.conf
I set the user with fsize 1024 like

    rv    hard  fsize  1024 
it affect on system that if I copy file I will get following message 

    File size limit exceeded (core dumped)
but while I tried to copy file by filezilla  able to download 500mb file from my test server .Is there any solution for this ? or Any other ftp server provide the Maxdownloadfile parameter ?

Thanks In Advance

---

