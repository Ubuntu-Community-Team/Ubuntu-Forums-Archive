---
title: "How do I send mail from the command line?"
date: 2008-06-16
forum: General Help
---

### Post by jonlemur on 2008-06-16
I'm trying to send email from the command line, but so far I have not been able to find how to configure everything properly.  It seems that eventually I'll be able to send mail by using a command such as the following:

mail -s "Subject" [email]receiver@example.com[/email]  < body.txt

I want to be able to send the email from my gmail account though, and I don't know how to tell it what address to send it from, or what my password is.  I also need to be able to send emails temporarily without entering my password every time it sends one.

Thanks for any help you can provide.

---

### Post by tamoneya on 2008-06-16
I havent ever done it straight through command line but I once wrote a script in python that sent a bunch of automated emails.  It worked fine with gmail.  
Take a look at these two links: [http://docs.python.org/lib/module-smtplib.html](http://docs.python.org/lib/module-smtplib.html)
[http://codecomments.wordpress.com/2008/01/04/python-gmail-smtp-example/](http://codecomments.wordpress.com/2008/01/04/python-gmail-smtp-example/)

Then you can just run the python script from commandline.

---

### Post by jonlemur on 2008-06-16
Thanks, I'll take a look at those.

---

### Post by tamoneya on 2008-06-16
my version one of the script i think took 15 minutes or so to get perfected and was 20ish lines.  Since then I added a bunch of other crap in there and it has become more like 100+ lines.  I however would also be interested if there was away to run directly from command line so if any other forum members know of a way to do that please tell.

---

### Post by jonlemur on 2008-06-16
I'll keep looking at those python examples, but I haven't been able to figure it out yet.  

It seems that mail should be able to do it though, after some configuration, and that I could write a simple bash script to automate it.

---

