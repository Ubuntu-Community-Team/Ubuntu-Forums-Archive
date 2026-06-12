---
title: "postfix gethostbyname error after edgy upgrade"
date: 2006-11-02
forum: General Help
---

### Post by harty83 on 2006-11-02
I upgraded my server to edgy.  I use courier-imap and postfix to handle my mail server.  Of course I had issues getting courier updated but was able to get it working again using the various bug reports and threads here. 

However, I am now having trouble with postfix.  I am not recieving my mail.  Looking through /var/log/mail.log I see an error as follows:

postfix/local[5254]: fatal: gethostbyname: Success

Then it has a bunch of warnings then finally ends in "unknown mail transport error."  Any clue what is going on?

I'm assuming that it has something to do with the fatal error since it is listed before all the warnings.

Help please.... :-? 

Thanks!

---

