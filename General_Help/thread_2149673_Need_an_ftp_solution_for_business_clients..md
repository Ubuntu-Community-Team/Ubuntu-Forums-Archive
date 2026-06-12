---
title: "Need an ftp solution for business clients."
date: 2013-05-29
forum: General Help
---

### Post by |{urse on 2013-05-29
Hey, the title sums it up, I was going to go the route of WebMin/ProFTPd. Was wondering if anyone had advice or maybe even a better solution. Server is a dual Opteron 6000 series with 64GB RAM. So what does the forums think? ProFTPd? I don't need help installing or configuring, just wondering if there is anything better out there.

---

### Post by Lars Noodén on 2013-05-29
If you are looking to upload/download securely, then should move on from FTP and use SFTP.  Clients are built into Nautilus and Thunar.  Of course FileZilla also supports SFTP.  

[list]
[*] [http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp)
[*] [http://www.openlogic.com/wazi/bid/188103/Stop-Using-FTP-How-to-Transfer-Files-Securely](http://www.openlogic.com/wazi/bid/188103/Stop-Using-FTP-How-to-Transfer-Files-Securely)
[/list]

---

### Post by |{urse on 2013-05-29
I was not aware how much more secure SFTP really was. Thank you! I may just go that route instead. ):P

Edit: After reading your links more thoroughly I will -definitely- not be using ftp.. Thanks again ^^

---

### Post by |{urse on 2013-05-29
All done! Works nicely. SFTP with chroot seems to do the job nicely. 

Here's the guide I followed if anyone is interested --> [http://yetanothercomputingblog.blogspot.com/2012/05/ubuntu-setup-sftp-server.html](http://yetanothercomputingblog.blogspot.com/2012/05/ubuntu-setup-sftp-server.html)

---

