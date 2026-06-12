---
title: "setting up an SFTP the easiest way?"
date: 2007-06-04
forum: General Help
---

### Post by bone2006 on 2007-06-04
I want to setup a secured FTP, but was wondering what is the easiest way.  I was looking at the guide for Gproftp, which I saw a section for installing ssh for SFTP, which is what I'd like to do ,but everything was command based, which I don't mind, but since the guide was for the Gproftp, I was wondering if there's an easier way to install a secured FTP server?

On the computer I want to run a secured FTP server, i already have openssh-server installed.  The reason I have it installed, is because this has mythtv already running on it, which required me to install it.  I'm bring it up, because I was doing a lot of searching and ran into people talk about installing openssh-server maybe?

---

### Post by frodon on 2007-06-04
I have a part about TLS encryption (FTPS) in guide if you are ineterested :
[http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588)

If you want a really secure server i don't advice you Gproftpd but to edit directly your proftpd.conf file.

---

### Post by bone2006 on 2007-06-04
That was the guide I was referring to.
Originally I was just going to use the easy part of the guide, but I wanted to make it more secure.  The easy installation seems so easy, but then as I was looking into the ways it says to make it more secure, I was just wondering if there's an easier application or way of setting up a secured FTP than proftp?

Thanks in advance

---

### Post by frodon on 2007-06-04
Easiest than that to create an encrypted FTP server maybe but i think it's a matter of feeling. The instructions in my guide are not that hard to follow, it's mainly cut and paste, the only part you need to adapt is the directory path in the proftpd.conf if you use some custom directories or maybe also the port if you want your server on port 21 but it's not a big deal.

Otherwise you can look for vsftpd, it's another popular FTP server maybe you will prefer it, anyway when you want a really secure server you can't trust a GUI, it's far better to edit  yourself by hand the config file.

---

