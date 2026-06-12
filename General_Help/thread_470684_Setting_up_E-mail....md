---
title: "Setting up E-mail..."
date: 2007-06-11
forum: General Help
---

### Post by Frozen001 on 2007-06-11
OK so I am an New Ubuntu/Linux User, but I am getting things running slowly piece by piece. 

I got Fetchmail set up to recieve my e-mail, and I can read the messages in Evolution, but  Evolution takes a long time to "get" my e-mail even though it is only reading from /var/mail/spool/myusername.  Have I setup something wrong?


A couple of things I want to do.

1)  I want to set up my own SMTP server so I do not need my ISPs server.  I installed Exim, and set it up, now how do I get Evolution to use it for out going email?

2)  I NEED to set up some sort of spam filtering.  What is the best way to do this?

3)  How do I get fetchmail to retrieve my e-mail with out me being logged in?  Right now I have to be logged in for it to retrieve it.

4)  I eventually plan on setting up a home network, and would like a server to do my email handling, and be able to access my e-mail on several computers... idealy I would like to have all my e-mail available at any computer.  Is this possible??  Also I would like some sort of web interface where I can access my mail server remotely.  Is this possible?

---

### Post by Frozen001 on 2007-06-12
Bump...

---

### Post by timcredible on 2007-06-12
as for getting a program to run when you're not logged in, just make an entry in your crontab (crontab -e) to do it every 10 minutes or so.  that will get fetchmail to run.

as for evolution, just point it to use localhost as your smtp server.

don't know about the other questions - sounds like it'd just be easier to use gmail.

---

### Post by Frozen001 on 2007-06-12
> **timcredible said:**
> as for getting a program to run when you're not logged in, just make an entry in your crontab (crontab -e) to do it every 10 minutes or so.  that will get fetchmail to run.

as for evolution, just point it to use localhost as your smtp server.

don't know about the other questions - sounds like it'd just be easier to use gmail.Thanks for the info...  

I will try setting Evolution to use localhost as the smtp server.

I would use gmail, but would rather not cange e-mail address or forward them to gmail.

---

### Post by Chayak on 2007-06-12
To get your email when you're not logged in run it as a service.  Yes it can run as a service despite what some people think.

[http://www.howtoforge.com/debian_etch_fetchmail]("http://www.howtoforge.com/debian_etch_fetchmail") <- to save me from typing so much

As for spam filtering I'm looking for something to do that myself.

---

### Post by Frozen001 on 2007-06-12
Thanks for the information... any idea on why Evolution takes so long to read the mail retrieved with FETCHMAIL??

---

### Post by andrew.46 on 2007-07-31
Hi,

 Read your post:

> **Frozen001 said:**
> Thanks for the information... any idea on why Evolution takes so long to read the mail retrieved with FETCHMAIL??

 Try another MUA? Have a look at:

[http://people.aapt.net.au/~adjlstrong/mutt.html](http://people.aapt.net.au/~adjlstrong/mutt.html)

 I think you would find mutt lightning fast after the incredibly cumbersome Evolution.

                  Andrew

---

