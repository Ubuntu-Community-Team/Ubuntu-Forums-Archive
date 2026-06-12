---
title: "Any thoughts on how to save password for alpine?"
date: 2008-02-28
forum: General Help
---

### Post by desper on 2008-02-28
I've been using alpine for a while, and recently feel tired of typing password everytime. Is there any way to save password for alpine? 
Thanks.

---

### Post by ncstate01 on 2008-04-25
cd /to/your/home/dir
touch .pine-passfile

run alpine.  

It will prompt you for password then prompt you to save it.  The same thing will happen when you go o send an email.  

A word of warning.  It appears that the file use to be .alpine-passfile but was changed at some point.  The name of the file that alpine is looking for is determined at compile time.  As long as they keep packaging alpine to look for .pine-passfile you will be fine.

---

### Post by desper on 2008-05-09
It works. Thank you

---

### Post by svaens on 2008-05-27
alpine seems to act a little strange.... 

I did as was mentioned above, and while it in the end works, there is something wrong inside .... 

On opening of alpine, it first proceeds to try to log in. 

It first attempts... then I get a "rsh to IMAP server timed out", 
but then immediately it seems to log in anyway. 
strange behaviour.. i should be glad that it works though. It has to be better than using thunderbird or evolution. Frankly, i've had enough of this bulky gui email clients. Thunderbird can't even update my preview pane, and evolution, ha! It's stupid constant failing 'ping' of my imap server drove me away from that client. Very annoying when an error message steals focus every 20 minutes telling me it was unable to ping my imap server.  I'm glad to be back to the simple console based email client, after being a long time user of pine.

---

### Post by dantheta on 2008-06-08
Alpine (and Pine before it) will try to use RSH or SSH to connect to the server before using IMAP.

To stop it doing this (and remove the 30second wait when logging into the server) add:

/norsh

to the end of the server address.  For example:

Server name: my.imap.server.com/norsh

Hope that helps!

D.

---

### Post by svaens on 2008-06-23
hey thanks!
That worked perfectly!

p.s. Sorry for the slow reply, was away for a while.

---

