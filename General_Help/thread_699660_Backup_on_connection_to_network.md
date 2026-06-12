---
title: "Backup on connection to network?"
date: 2008-02-17
forum: General Help
---

### Post by drfox on 2008-02-17
Does anyone know if it's possible to have a daemon running that will sense when you're connected to your "home" network and backup then?
I'd like to automatically backup my files to a Buffalo Linkstation (maybe daily or so) when I'm at home, and not have it try to backup when i'm away (at my office or at Starbucks)

Thanks.  Larry

---

### Post by honeydew on 2008-02-18
I imagine you could write a little script that monitored a connection IE.. if your buffalo station is 10.10.1.2

then
while 1 = 0 
if ping 10.10.1.2 = true
   scp backup.tar.gz 10.10.1.2:/directory/backup`date`.tar.gz
else
   kick rocks

granted this wont work(it takes me longer then five seconds to write even the smallest scripts.. it may give you a idea.. you could set a script like this in rc.local.  A good while loop should demonize it(I know there have to be better ways todo that)

conversly instead of running it as a deamon you could have a cron script that runs hourly and checks for the connection.

good luck.. and if you get a script working please share ;)


btw: I looked at my script after posting it.. this would infact send your backup files hundreads of times.. it may be more prudent to have a script that checks for the connection every hour and then runs rsnapshot.....

---

