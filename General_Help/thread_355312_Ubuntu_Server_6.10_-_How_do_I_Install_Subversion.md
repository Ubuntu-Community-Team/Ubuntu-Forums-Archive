---
title: "Ubuntu Server 6.10 - How do I Install Subversion"
date: 2007-02-07
forum: General Help
---

### Post by Ozbboy on 2007-02-07
Hi Everyone,

Can someone help me out? 

I need the terminal commands to setup Subversion 1.4 with a web admin on Ubuntu Server 6.10 with or without LAMP.. No big deal there.. 

It Subversion needs to be accessible via networked WinXP machines (All of our development is .net).

Currently we're running subversion on an XP machine that's due for retirement, thought this we the perfect opportunity to start moving away from MS OS's.

Help much appreciated.

---

### Post by rogier.de.groot on 2007-02-07
If you mean you want subversion with apache, consult the official ubuntu server guide, chapter about version control. If it's standalone I always do the following:
sudo apt-get install subversion
sudo groupadd svn
sudo useradd -g svn svn
sudo svnadmin create /var/svn
sudo chown -R svn:svn /var/svn
sudo -u svn svnserve -d -r /var/svn
(not entirely sure the last line is exactly correct)
Don't know about the webadmin part, hope it helps.

---

### Post by Ozbboy on 2007-02-07
Thank you.. I'll play around with ti some more today..

Hopefully I can get this sucker working :D

---

### Post by jml75 on 2007-02-16
Hello rogier.de.groot,

I'm following the guide to subversion + apache throught webdav but it does not want to work!

When issuing the command svn co [http://server/svn/](http://server/svn/), I only get : 

svn: Échec de la requête PROPFIND sur '/svn'
svn: PROPFIND de '/svn': 301 Moved Permanently ([http://server](http://server))

What's wrong?

Thanx!

---

### Post by possumator on 2007-04-28
I got subversion up and running by following this guide:

[https://help.ubuntu.com/community/Subversion](https://help.ubuntu.com/community/Subversion)

and I just found this one too....

[https://help.ubuntu.com/6.10/ubuntu/serverguide/C/version-control-system.html](https://help.ubuntu.com/6.10/ubuntu/serverguide/C/version-control-system.html)

It works fine using TortoiseSVN, however....

The server guide shows enabling WebDAV access to the repositories by listing them in apache2.conf rather than in dav_svn.conf. This might explain why I cannot obtain read/write access to the folders from Firefox 2.0 or IE6 on Windows XP. 

I can see the folders by browsing to the URL, but they are read only. Then when I try to add them as a network location, my username and password are rejected (the same logon which works fine in TortoiseSVNl). 

TortoiseSVN supports quite a few protocols.....so I am unsure if it is really using http, but I am giving it an http address to access...so it must be.

---

### Post by ariejan on 2007-06-01
For a full Subversion + Trac installation using web_dav check out these two articles:

[http://ariejan.net/2006/12/01/how-to-setup-a-ubuntu-development-server-part-1/](http://ariejan.net/2006/12/01/how-to-setup-a-ubuntu-development-server-part-1/)
[http://ariejan.net/2006/12/02/how-to-setup-a-ubuntu-development-server-part-2/](http://ariejan.net/2006/12/02/how-to-setup-a-ubuntu-development-server-part-2/)

Cheers!

---

