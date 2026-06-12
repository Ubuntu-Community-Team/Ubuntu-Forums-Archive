---
title: "killed 12.04 lts"
date: 2017-06-29
forum: General Help
---

### Post by joe672 on 2017-06-29
i ran an update from webmin.. it has since killed my server and am unable to log in via putty, no websites connection etc etc

i am able to connect via my  vps host cp, get this now:

:/# sudo service apache2 status                                                           
No apache MPM package installed 

running unbuntu 12.04 lts, is this still the best os for webservers or is there a newer/better version?

---

### Post by Autodave on 2017-06-29
I am thinking that 12.04 might be past it's end of life support. Are you running the server edition or regular Ubuntu?

---

### Post by joe672 on 2017-06-29
it was running the server edition i think lol, hosted a couple websites and voice server

---

### Post by Autodave on 2017-06-29
I am not sure about the server edition: it may have a longer service life. Hopefully, some one else will jump in here.

Server 16.04 is the newest release: may be time to consider upgrade? If so, I would propably do a clean install. Copy EVERYTHING you may need before you go there!!!

---

### Post by ajgreeny on 2017-06-29
Yes, on the assumption that your 2.04 is actually 12.04, it has indeed now gone beyond its lifespan and is EOL.

I also thoroughly recommend that you do a clean install of the 16.04 server version which is supported till 2021.

You can not upgrade simply as you can only go from 12.04 to 14.04 and would then need to upgrade again from 14.04 to 16.04; save yourself a lot of time and potential problems by backing up all the files and folders you need to keep and then clean install 16.04.

---

### Post by joe672 on 2017-06-29
aye 12.04 lts

can you guys help me get the server live again? need to get copys of myphp databases

then upgrade

---

### Post by QIII on 2017-06-29
From the terminal/command line, are you able to ping the server by IP?

---

### Post by joe672 on 2017-06-29
dont think so, it just keeps requesting the ping having to log in  via html5 in browser, cant use putty or the details id normaly use to log in.. its a uber newbie mistake

---

### Post by joe672 on 2017-06-30
got a restore, ill save and upgrade later. cheers

---

