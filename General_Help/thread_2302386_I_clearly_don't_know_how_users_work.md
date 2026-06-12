---
title: "I clearly don't know how users work"
date: 2015-11-10
forum: General Help
---

### Post by averageschmoe on 2015-11-10
Hello, I've been using Ubuntu for longer than I'd care to admit given my knowledge level. After WMC was officially dropped from Windows 10 and my guide data stopped updating in W8.1 I decided that maybe it was time to officially make the switch and am currently running Ubuntu 14.04.3. I initially went with MythTV as the backend for my TV watching and, in fact, managed to have it working successfully. Unfortunately, I didn't quite understand how MythTV saved episodes at the time and felt that the hoops needing jumping through to get my recorded episodes to show up under TV Shows in Kodi were more than my simple needs should require. This led me to TVHeadend.

When I installed TVHeadend I apparently did so under newly created userr 'hts'. This wasn't an issue until I managed to stumble my way through downloading my Schedules Direct data with MC2XML. The problem I'm having is following a walkthrough that involves changing user via 'sudo su - hts' making tv_grab_file executable and then editing the resulting file. When I get to this point the terminal asks for my hts password, which from what I can remember doesn't exist. I can't leave it blank and nothing I wrote down during TVHeadend's setup works either. So, I reopened a terminal under my standard username and used passwd for user 'hts' to assign a new password. This appeared to work but when I go to edit the tv_grab_file under user 'hts' and enter the password to enter nano I get a message saying "hts is not in the sudoers file.  This incident will be reported."

At this point I admit that I have no idea what I'm doing. Ultimately, all I want is to edit this file, but I should also understand why TVHeadend created a new user to install and run under. I don't, and it's frustrating being stupid. Why is my normal user account not good enough? Is there an easy way to move TVHeadend under my normal user or should I keep it as is and, if that's the case, can someone explain what I'm not getting?

---

### Post by grahammechanical on 2015-11-10
If we are not careful when using sudo su we can make root the owner of  files. Which means that only the administrator can edit the file by  opening the editor in the terminal and pre-pending sudo to the command.

Perhaps  you need to open nano using sudo to edit this file anyway. It  all depends on who has ownership of the file and who has read/write  access. If TVHeadend has created (with your agreement) a user called  "hts" then it seems that hts is set up as a standard user and not as an  administrator. Which is sensible. This application will no doubt be  accessing the internet. You do not want it having administrator  privileges.

I am unfamiliar with TVHeadend and its methods but it  seems to me that you do not need to be the hts user or to give hts  administrator privileges to edit the tv_grab-file. Opening nano with  administrator privileges should give you the authority.

Regards.

---

### Post by sotiris2 on 2015-11-10
```
sudo su hts[code] Runs sudo first which is a program to run the rest of the command as a different user, by default root. Most importantly sudo asks for the already LOGGED IN user's password (f.e. averageschmoe ) not the password of the target user hts (because it may not actually exist as in your case).After it gets the password if the already logged in user is in the sudoers file (aka is an administrator such as the first user of the ubuntu install) it runs the commands. If he is not you get the error message "hts is not in the sudoers file. This incident will be reported."as because you tried to run sudo when you were logged in as hts. 

Running the commands as root will work if it's just editing existing files but if any command creates new files they will be owned by root and not hts and may cause problems later. Since you got hts a password for hts you can login normally as hts in the login screen and run the rest of commands after sudo su hts. You don't need it you are already hts. You can also just do [code]sudo su hts
``` from your normal account with your normal password.  
Or even ```
su hts
``` which will ask for hts password (which you have created).

---

### Post by deadflowr on 2015-11-10
Hmm, I think you only need to add/change the cat line in the tv-grab_file
Your user can do this
looking at it the line states
```
cat ~/.xmltv/tv_grab_file.xmltv
```
but you need to simply change it to
```
cat /home/hts/mc2xml/xmltv.xml
```
There should be no need to su into any other user.

Basically, from a quick reading of this rather old tut: [https://tvheadend.org/boards/4/topics/10322/](https://tvheadend.org/boards/4/topics/10322/)
you should be able to configure the whole thing as your usual user.

---

