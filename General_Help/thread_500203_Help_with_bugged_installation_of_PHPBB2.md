---
title: "Help with bugged installation of PHPBB2"
date: 2007-07-13
forum: General Help
---

### Post by william_hunter on 2007-07-13
I searched the threads like mine, and I could not find an answer, so I am going to ask here. 

I recently set up a web forum using LAMP, and the directions on the howto's section. I symlinked my phpbb2 directory to var/www and now there is a phpbb directory in the www folder. Apache will link browsers to my site. ([www.rot.game-host.org/phpbb](www.rot.game-host.org/phpbb))

However...I am having a problem with people being able to log in successfully. I have triple checked the cookies, been to the phpbb forums for help and gotten their seal of approval on the cookie set up, and everything seems right, but people cannot log in without going through an extra step. 

I know nothing about how a symlink works, but I am grasping at straws here. When I make changes in the phpbb2 directory under usr/share, do those changes automatically get entered in the phpbb dir under var/www or do I need to do the changes directly in the var/www/phpbb directory? Also, do I need to change permissions in the var/www/phpbb directory? 

I am thoroughly stumped by this, and it is getting really annoying now. I have been looking for possible causes for days now, and I don't know what else to do. Any thoughts on this that are not mine would be appreciated.

---

### Post by william_hunter on 2007-07-13
Hey, while I am at it..

I want to make sure that incoming web traffic is automatically routed to the forum. Right now, if someone wants to they can link to phpadmin and/or see the apache successful install page, as well as the forum by omitting the /phpbb from my link above. The phpadmin is of course passworded, but I still would like to know how to make apache redirect traffic to the forum...anyone give me a step by step on that? I tried doing what was listed at the apache site, but I seem to have a blockage against doing things right lately.

---

