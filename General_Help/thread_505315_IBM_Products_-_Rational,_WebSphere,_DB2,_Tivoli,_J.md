---
title: "IBM Products - Rational, WebSphere, DB2, Tivoli, JDK"
date: 2007-07-20
forum: General Help
---

### Post by Aurorion on 2007-07-20
Hi

I have been using Ubuntu for about 8 months now. These forums and all of you have helped me a lot in these months, I could solve any problems I had till now from earlier posts here. Keep up the good work. :)

I have a software project for which I will need to use the following software from IBM:-

[B]
Rational Software Architect 7
Rational Application Developer 7
Rational Web Developer 7

WebSphere Application Server v6.1
DB2 9
Tivoli Storage Manager

IBM JDK J2SE 5.0
[/B]

Ubuntu is not a "recommended" OS for any of these products as far as I know. However, I love Ubuntu too much to move to another distro like Fedora or SUSE. And I can't imagine myself moving back to Windows either... :(

My question is, do these products work on Ubuntu? If yes, which release should I opt for? I don't mind using an earlier release, as long as it helps me use the above products perfectly.

From previous threads here, I understand that Feisty has some issues with the IBM JDK and with DB2. Also, RSA seems to have troubles with Edgy:-

[http://ubuntuforums.org/showthread.php?t=358588](http://ubuntuforums.org/showthread.php?t=358588)

This page seems to indicate 6.06 LTS will be the best, if not only, option:-

[http://linuxplanet.com/linuxplanet/newss/6379/1/](http://linuxplanet.com/linuxplanet/newss/6379/1/)

Has anyone here used the above products on any Ubuntu release? Can you please advice me on what path to take?

By the way, I know there are (probably better) alternatives to the above products, but I need to use them. I don't make the rules, I just follow them. :( So I can't just use NetBeans or MySQL or WebLogic or PHP, I have to use the IBM products.

Thanks!

---

### Post by yetanothersteve on 2007-08-14
I installed RAD 7.0 and the Fixpack to 7.0.0.3 tonight.
The one gotcha I ran into was that Ubuntu links /bin/sh to /bin/dash and not /bin/bash.
The installer kept failing near the end when running some .sh scripts. I temporarily linked /bin/sh to /bin/bash and the install completed perfectly.

I have not tried creating a web application yet but basic functionality all appears good.

---

### Post by Aurorion on 2007-08-16
^ Thanks for the reply.

I have installed RSA 7 and the RSA v7.0.0.3 fixpack on Edgy. Besides that, I have also installed WebSphere Application Server Community Edition v1.1.0.2, IBM J2SE 5 SDK and DB2 Express-C 9 v9.1.2 on Edgy. All of them are working perfectly, as far as I know.

I also encountered the problem you have mentioned, but this thread helped me with that problem:-

[IBM DeveloperWorks: V7 installation/transition issues]("http://www.ibm.com/developerworks/forums/dw_thread.jsp?message=13957317&cat=67&thread=144425&treeDisplayType=threadmode1&forum=430#13957317")

Besides that, I faced another problem as explained [HERE]("http://ubuntuforums.org/showthread.php?t=358588"), but I solved that too with [mdailey]("http://ubuntuforums.org/member.php?u=236894")'s help.

---

### Post by -JB- on 2008-04-12
I recently managed to install websphere application server 6 with updates, websphere portal 6 with updates and rad7 for portal development. On Hardy 8.04  
Works great! 
(Lenovo T61 2 gig ram)

---

