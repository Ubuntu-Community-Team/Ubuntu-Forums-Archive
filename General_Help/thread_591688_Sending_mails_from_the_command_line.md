---
title: "Sending mails from the command line"
date: 2007-10-25
forum: General Help
---

### Post by JMO707 on 2007-10-25
I've seen every thread in the firsth three pages of "sendmail" on titles search, and it seems that everyone has some grade of knowledge that I lack. Even looking on Google didn't help me.
Possibly, I'm not searching for what I need.

I just want to be able to read my mailbox and (above all) send mails from the command line, even to use this on some or other shell script.
But really: I found that Sendmail and Postfix are WAY too... mmm, complex?, big?, for what I want. 

My question is: is there any simpler solution to do this? If not, can you reccomend me where to start to learn how to configure any MTA?

Thanks -_-

---

### Post by Prospero2006 on 2007-10-25
I love pine. It's a great backup for those times when you can't access a gui.

apt-get install pine.


help?

Pros

---

### Post by Neostar on 2007-10-25
Elmo is also great, and it has a lot of very important features too. Give it a try, you'll like it :)

```
apt-get install elmo
```

---

### Post by JMO707 on 2007-10-25
Well, elmo is nice!, and alpine (somewhat the continuation of pine) did his work nicely too!

But I think that my approach is not the best.
You'll see, I made a script to backup some important configuration files. I just want to send the backup away from my computer, and my mail was an alternative, but I also need not to be asked by a password or anything at all. I need it to be done automagically.
In an example script I've saw scp used to copy the backup to a server, but...ehem, I don't have one to send it =p

Thanks for the answers1

---

### Post by Prospero2006 on 2007-10-26
do a google for rsync.

You can also set rsa authentication over ssh to eliminate the scp password 
prompt.

Pros

---

