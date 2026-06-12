---
title: "How can I get evolution to access my &quot;unix mail&quot;?"
date: 2007-12-14
forum: General Help
---

### Post by lastpork on 2007-12-14
I don't know if that's the right name, it's the user's mail, the one that you access when you run mail command. I want to have a graphical means to view the results from my daily chkrootkit and rkhunter runs. Or is there a better way to do this? Ideally I'd have the results automatically displayed on my screen, be it a terminal or any other way, every day, but i'm new in ubuntu and linux in general and have no idea how to do this.. Anyone have a better idea? thanks

---

### Post by cmnorton on 2007-12-14
You should be able to import your mbox into Evolution perhaps even with a cron job, rather than manually. However,  this sounds like you need to have your jobs send email to the account you are using with Evolution. I changed /etc/crontab to send my account email, using its full address.

---

### Post by lastpork on 2007-12-14
well how would I do it? how can i access my mail from evolution? I can't get it working, all I get is the evolution "welcome" mail, not my mail....

---

### Post by daengbo on 2007-12-14
In Evolution, go to Edit -> Preferences and choose to add a new account. In your e-mail address, type something like lastpork@localhost

Click next and choose Server Type = Local delivery and Path = /var/mail/lastpork

That should do it for you.

---

### Post by lastpork on 2007-12-14
thanks for the answer! the problem now is that my account does show up in /var/mail but it's faded, I  can't select it... why do you think this is? the only way I can select the file for my mail is by choosing "standard unix mbox spool file" in server type, but then when I click send/receive nothing happens and there are no mails in my inbox

---

### Post by lastpork on 2007-12-14
bump

---

### Post by daengbo on 2007-12-18
Do you have a mail server installed for local delivery? If you don't, there won't be any mail there.

---

### Post by wactuary on 2008-01-26
Here is a bump because I have exactly the same problem.  Trying to get local mail, there is mail in /var/spool/mail/user.  I can read the mail with mutt or pine.  When configuring evolution to read from "local delivery", I can see the user file, but can't select it.  It is greyed out.

I have checked that user has rw access to the file name.  I have also tried adding user to group mail.

Any suggestions?

Also Gutsy, also using evolution.  Evolution does currently get my other e-mails, just a problem with local delivery.

Thanks.

---

