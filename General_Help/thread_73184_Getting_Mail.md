---
title: "Getting Mail"
date: 2005-10-08
forum: General Help
---

### Post by nihilism on 2005-10-08
Hey, I know you guys might get this alot, but, I have a gmail account, and I have been getting a really hard time reciveing mail in linux. See, I set my gmail acount to accept pop access, I've been using linux for atleast a year now, and after a few months of using odd package names in suse, I decided to switch to ubuntu, cause even if it did have those problems, what am I gonna need to build thats not in apt? Anyway, I digress. Since suse it has been a pain in the ass trying to recive mail on things like evolution and kmail, I think it might be a firewall problem, but I'm not sure, I see it go for smtp access no problem. But when I see it go for pop, no dice. Anyone that can help?

---

### Post by aysiu on 2005-10-08
Have you tried Thunderbird?

---

### Post by dougr on 2005-10-08
I would highly recommend thunderbird.  It is the only mail problem that has not given me any headaches.  Also migrating from computer to computer is extremely simple.  I used evolution for years, but finally moved to thunderbird about 6 months ago...im sold.  I do miss the built in palm sync integration with evolution, but I just use j-pilot now.  I must say evolution even had problems with that though.  To me evolution has always been broken...thunderbird just works.

On the original topic however, there is no reason gmail should be any more difficult to grab mail from than any other pop3 account.  One suggetion is if you have a pop account that works well in your chosen app, just forward your gmail mail to that account, and then get it all.

---

### Post by jimcooncat on 2005-10-08
Open a terminal, and type "telnet pop.gmail.com 995". You should get the following. If you don't, then you probably have a firewall or network problem.

Trying 66.249.83.109...
Connected to pop.gmail.com.
Escape character is '^]'.

If you are getting a message like that, though, then check your client. See instructions at:

[http://gmail.google.com/support/bin/answer.py?answer=12103](http://gmail.google.com/support/bin/answer.py?answer=12103)

---

### Post by nihilism on 2005-10-08
Thanks, Im gonna apt-get thunderbird right now, I think it should work, I tried the telnet thing, so no firewall problems.

---

### Post by jimcooncat on 2005-10-08
Just a little note for other folks with the same problem with Gmail: I think nihilism's email client was trying to use the standard POP3 port, 110. Gmail uses the SPOP (Secure Post Office Protocol) port, 995.

---

### Post by odin on 2005-11-23
[QUOTE=jimcooncat]Open a terminal, and type "telnet pop.gmail.com 995". You should get the following. If you don't, then you probably have a firewall or network problem.

Trying 66.249.83.109...
Connected to pop.gmail.com.
Escape character is '^]'.

If you are getting a message like that, though, then check your client. See instructions at:

[http://gmail.google.com/support/bin/answer.py?answer=12103](http://gmail.google.com/support/bin/answer.py?answer=12103)[/QUOTE]

Well I tried that but I get an error of unknown host or something loke that,is this because of the proxy we have or a name resolution problem?

---

