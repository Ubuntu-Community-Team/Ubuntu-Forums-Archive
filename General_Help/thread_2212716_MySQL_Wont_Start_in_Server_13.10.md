---
title: "MySQL Wont Start in Server 13.10"
date: 2014-03-22
forum: General Help
---

### Post by Alan_Killian on 2014-03-22
[SIZE=4][FONT=times new roman]Hello,
I have been trying to install a new box with Ubuntu server 13.10 and LAMP package. Long story short I used the commands listed here [http://landofthefreeish.com/linux/how-to-move-or-migrate-linux-user-accounts/](http://landofthefreeish.com/linux/how-to-move-or-migrate-linux-user-accounts/) to migrate the users and groups over[COLOR=#333333]. I could see the shadow file did not match the one on the old server. I managed to so hose passwd & shadow files I couldn't even log in using recovery mode. I was able to boot with PartedMagic and took copies of passwd, shadow,group, and gshadow as is off of my current working server (12.10) and just copied them into /etc, no crazy awk commands like in the link I sighted. On reboot I could login OK and also checked several users and they work now? My concern was that is it OK to just copy the four files? Would I run into troubles with groups or UIDs which I'm not familiar with down the road? Sure enough on trying to start mysql from webmin no good. At first I had an error message pertaining to app armour and googled it and found several who had problems with app armour and mysql. So i followed guide I found and removed the the mysql profile from app armour and checked that it was indeed gone. But now MySQL still doesnt start and I get no error messages in the logs what so ever and when I try starting from terminal I just get a pause for several seconds and a cryptic message that MySQL could not start.  Should I just start over or can I save this install?
[/COLOR][/FONT][FONT=arial][COLOR=#333333]P.S. - I should add I changed the values on the commands from the site to 1000 & 29999 respectively.[/COLOR][/FONT][/SIZE]

---

