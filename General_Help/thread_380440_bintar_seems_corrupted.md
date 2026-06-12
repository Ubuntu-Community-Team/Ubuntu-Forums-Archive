---
title: "/bin/tar seems corrupted"
date: 2007-03-09
forum: General Help
---

### Post by dcantin on 2007-03-09
Hi, I got the following on a fresh install of ubuntu edgy

# tar
bash: /bin/tar: Permission non accordée

#ls -l /bin/tar 
?r-sr-xr-t 22400 660959749 1508701261 1481379218 2008-01-21 20:35 /bin/tar

there is clearly a problem with this file.. and I cant delete or move it.. event with it's inode number

Any thought ??

---

### Post by llamakc on 2007-03-09
Has it been made immutable?

run:

lsattr /bin/tar

If you see an "i" in there, you have problems. Is this a shared system? You can change the immutable flag with:

sudo chattr -i /bin/tar

As for the file permissions for your /bin/tar, google JUST that and you'll see that you may have larger problems.

---

### Post by dcantin on 2007-03-09
ok, It looks like I got a problem ;)

No it's not a shared system.

this command failed to execute

# lsattr /bin/tar
lsattr: Ioctl() inappropré pour un périphérique Lors de la lecture des drapeaux sur /bin/tar

the problem first occurred when I have added the automatix2 repo line to my source.list and I did an apt-get update && apt-get install automatix2. Just before that, I successfully run an apt-get update && apt-get upgrade

---

### Post by dcantin on 2007-03-10
For the records..

I've just reinstall ubuntu edgy and everything is back to normal

On the web site of automatix, they said that their web site have been hacked.. so, maybe it's related, who known...

David

---

