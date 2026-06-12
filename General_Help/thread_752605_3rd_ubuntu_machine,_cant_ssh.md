---
title: "3rd ubuntu machine, cant ssh"
date: 2008-04-11
forum: General Help
---

### Post by Voorhees1979 on 2008-04-11
Hi all

I installed openssh on my daughters machine by typing sudo apt-get install openssh-server

Now when i load Konqueror I can put the details in and connect ie 10.1.1.3 and away it goes I can transfer files and everything.

Now I set up a 3rd machine running ubuntu for my son. The reason being is, is I want to send vobs to there machines so they can watch films, they always scratch dvds :(

Anyway I can do this with the first machine no worries after a simple install off openssh. BUT this 3rd machine, i did exactly the same as I did with my daughters machine but I just cannot connect. If i run this through the terminal for the 3rd machine i get:

voorhees1979@voorhees1979-desktop:~$ ssh james1@10.1.1.4
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
73:a5:07:fe:32:ee:51:0a:6f:67:53:cb:9a:8e:dc:b2.
Please contact your system administrator.
Add correct host key in /home/voorhees1979/.ssh/known_hosts to get rid of this message.
Offending key in /home/voorhees1979/.ssh/known_hosts:1
RSA host key for 10.1.1.4 has changed and you have requested strict checking.
Host key verification failed.
voorhees1979@voorhees1979-desktop:~$ 

If i do ssh james@10.1.1.3 to my daughters machine, it connects stright away.

Now i can vncviewer 10.1.1.4:0 and see his desktop with no worries.

Notice my daughter is james and my sons is james1

Amy help would be great. Many thanks

---

### Post by pointone on 2008-04-11
Simply deleting /home/voorhees1979/.ssh/known_hosts should solve the problem. This file will be regenerated the next time you ssh (you will be asked if you want to add a key to your known hosts).

---

### Post by Voorhees1979 on 2008-04-12
Hi there

Many thanks for that. That cured it, wish I thought of that at 2am last night :)

Thanks again for your time

---

