---
title: "Ubuntu Server 512 MB - Enough to host my forum?"
date: 2013-08-02
forum: General Help
---

### Post by miklo2 on 2013-08-02
// Edited Post: My MYSQL PROBLEM  is Solved:

Hello everyone, I am pretty new in Ubuntu, and I have bought a Cloud Server to explorer Ubuntu and hopefully move my forum there. But I wanted some professional Advice befor openning my forum in public.

The server I am using is an Ubuntu Server, 512 MB, 2 Terra Byte Transfer, 20 GBs Disc Space! I pay monthly ofcourse! And I am trying to host my vBulletin forum there! I have right now Installed a few basic Packages such as:
> mysql
php + Curl
phpmyadmin
SMTP 
postfix >> For sending mails out
ProFTPD
Fail2ban 
CSF >> Firewall

I just wanted to know if I am ready to move my forum and open it for public! I wanted some professional advice, so hopefully I hope that my server is strong enough to host a healthy and secure vBulletin forum! If you have any advice please let me know!

PS, I also heard that instead of ProFTPD its better to Install "Pure-FTP".. Any advice to that

---

### Post by ranger1021994 on 2013-08-02
I can help a little in maintaining security.
You can take a look at these links

MySQL : [HTML]http://www.symantec.com/connect/articles/securing-mysql-step-step[/HTML]

PHP : [HTML]http://www.cyberciti.biz/tips/php-security-best-practices-tutorial.html[/HTML]
         [HTML]https://www.digitalocean.com/community/articles/how-to-install-and-secure-phpmyadmin-on-ubuntu-12-04[/HTML]

All the best

---

### Post by miklo2 on 2013-08-02
Thanks a lot ranger1021994! That was very helpfull and I will def have to do a bit of working on securing my server! Good articles mate.

Feel free to add any advice! God bless!

---

### Post by TheFu on 2013-08-02
I don't think there is anyway to secure any PHP-based webapps.  My security team will not allow php apps on the internet - period.

Also, web GUIs to control other systems have had security issues a few times recently.  phpmyadmin, cpanel, webadmin each have been attacked and penetrated allowing the attackers administrative access to the servers. Best to learn how to manage your server from the CLI via ssh.

Each of us has to weigh the risks of running services on the internet and need to be prepared for when a successful hack occurs.

vBulletin is what this forum runs and they were hacked 2 weeks ago, down for almost 6 days and completely swapped out their authentication system afterwards.  These folks are experts and they were hacked.  Just sayin' - I wish you luck.

The main 3 FTP servers running most places have each had security issues the last 3 yrs. Backdoors were added which allowed the entire system to be accessed. If you want everyone in the world to be able to download the files - great, FTP is perfect for that.  If you want logins and controlled access, then sftp is what you want.  

There are lots of great web articles about these things - google will find them. 

As to running any server  on the internet, I can only recommend that you seek out "best practices XXXX" googles and follow them to the best of your ability. "best practices php" would be a good start. If I couldn't put my php webapp behind a VPN, but had to have it on the internet, I'd only do so behind a great, extremely restrictive firewall, with a highly restrictive reverse proxy that filters unexpected and malformed requests. I'd run the DB in a different server.

Lastly, everyone will be hacked eventually, so backups that work perfectly and let you restore a website for yesterday, last week or last month is the most important thing you can do.  Breaches are seldom discovered immediately - usually it takes a few days or weeks to discover, so having offsite, versioned, backups is job-one for running a  secure system and being able to recover after a breech.

---

### Post by miklo2 on 2013-08-02
@TheFu Amazing info! Yes you are def right and honestly I am a moderator myself in other vBulletin forums, and one of our forums were hacked for the 3rd time using vBulletin version 4.2 with a theme bought from ThemeForest! I am very thankfull for all your awesome notes and warnings you have added in your reply! I will be saving it and hopefully I might change server as soon as possible, but I will def be using ubuntu for my home work and my private server at home! God bless and Thank you very much!

---

