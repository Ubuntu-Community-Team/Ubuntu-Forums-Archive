---
title: "Ubuntu Server Problems - FTP &amp; resolv.conf"
date: 2007-08-02
forum: General Help
---

### Post by regnumimbrium on 2007-08-02
Hey All,

I've got a few questions/problems with a recent Ubuntu Server 7.04 installation. I'm still pretty new to linux and so far have been following this guide:  [http://onlyubuntu.blogspot.com/2007/05/ubuntu-704-feisty-fawn-lamp-server.html](http://onlyubuntu.blogspot.com/2007/05/ubuntu-704-feisty-fawn-lamp-server.html)

I did the DNS/LAMP installation and have done just about everything else in the guide, except for install the desktop environment and webmin. Now, here's my questions:

1) The author writes that you need to edit "/etc/resolv.conf" and "You need to add look something like this":

search domain.com

nameserver xxx.xxx.xxx.xxx

So if I purchased my domain through [www.aplus.net](www.aplus.net) and am using [www.dnsexit.com](www.dnsexit.com) for my dynamic dns management (because I'm running a personal server from home) should my resolv.conf file look like this?:

search domains.aplus.net  [or, perhaps, "search dnsexit.com" ?]

nameserver ns1.dnsExit.com
nameserver ns2.dnsExit.com

Any help here would be great.

2) I completed the section "Install SSH Server" and that seemed to work fine. Since then, I've been able to connect to the server via PuTTY but only after port-forwarding (on my router) ports 80 and 20-22 for the specific server. So...
   a) Was I supposed to forward those ports or am I putting my home network at some major security risk (and how should I fix it, if so)?
   b) Although I can connect via PuTTY, I can't connect via Filezilla. Do I need to do some extra steps to allow FTP connections (and how do I do that, if so) or am I just making some simple mistake?

3) In the same guide I've been using, the author writes, "[After installing GNOME desktop] Now you can install webmin for their server web interface to configure apache,mysql servers."  Since I'm just trying to get a simple personal web page and possibly little forum going, would that be the next best step to that end? I've already tried entering my domain name on the internet and I get an FTP-like page which has only an Apache folder which defaults to the message "It Works!"; do I still have a lot of Apache/MySQL configuring to do before I can get things up and running?

Thanks so much for any time spent helping with all of this. Let me know if I need to clarify anything!

Thanks Again,
-ri

---

### Post by Terry of Astoria on 2007-08-02
I think you put in resolv.conf the nameservers for your ISP where your server is connected to the internet.  You didn't say what your connection is, or where your server is.
   Filezilla can do sftp. It is recommended by some not to run an ftp server, since all file transfer and controlling the server can be done by ssh. You're definitely on the right track.

---

### Post by Terry of Astoria on 2007-08-02
Just put your index.html page in /var/www/html and you are online, it sounds like.

---

### Post by regnumimbrium on 2007-08-02
Terry - great info, thank you. I think I follow you completely. One newbie question, then: I've downloaded WinSCP to handle my file transfers but I can't seem to copy anything to the directory you specificed (/var/www/html); I get a "permission denied" error. I know how to get appropriate permissions through PuTTY but not in any file transfer program.

Thanks,
-ri

Update: I think this guy was in the same position as me: [http://forums.fedoraforum.org/archive/index.php/t-105280.html](http://forums.fedoraforum.org/archive/index.php/t-105280.html)   ...unfortunately, I don't have any idea how to do what they're doing. It seems that to transfer files to my server (remotely) I'll need a user with permissions to do so but that that user has to simply be part of the group which owns the directory (/var/www/html). So, can anyone tell me how to add the group, modify the group members, make the group own the directory, etc.?

Thanks Again,
-ri

---

