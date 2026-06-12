---
title: "sendmail stalls... almost"
date: 2008-05-10
forum: General Help
---

### Post by bro on 2008-05-10
Hi, I installed sendmail which starts during startup. This however takes a very long time. It changes the splash screen to 'commandline look' (I don't know what to call but you see all the parts being started with [OK] behind. On sendmail it stalls for a minute or so. 
Why? Is this normal? (no!)

---

### Post by Monicker on 2008-05-10
Is your DNS configured correctly? Are your networks interfaces up before sendmail attempts to start?  Problems with either of those can cause sendmail, and other services, to take a very long time starting.

---

### Post by bro on 2008-05-10
A that is probably the cause.. but how to solve it? I installed sendmail because I'm using xampp as server for developping. I couldn't mail from there and I can with sendmail installed. Ofcourse while booting nothing is there. 

I don't know anything about configuring DNS. I just start up and it finds my wifi... My knowledge about networking goes as far right-click 'sharing options'. So .. a hint?
Is there a way for starting up sendmail later / manually?

---

### Post by Monicker on 2008-05-10
Is there a text error message about sendmail when it finally does start?

Its possible it might be this issue: [http://www.ubuntugeek.com/fix-for-sendmail-boot-error-in-ubuntu.html]("http://www.ubuntugeek.com/fix-for-sendmail-boot-error-in-ubuntu.html")

If that is not it you could try the following from a terminal:

```
sudo chmod -x /etc/init.d/sendmail
```

You may still see an error about sendmail not starting but it will not hang.

To manually start it do this from a command line:

```
sudo chmod +x /etc/init.d/sendmail && /etc/init.d/sendmail start
```

---

### Post by bro on 2008-05-10
It lost me completely. Sendmail doesn´t appear to work anymore from xampp powered sites. 
the first option you mentions didn't do it. 

The second dit solve the slow booting of my laptop. Strangely it also seemed te send a mail but i'm probably mistaken somehow.

the third which is supposed to go with the first i assume does not work but also doesn't appeal to me as a solution; chmod-ing and starting and undoing before every reboot... not nice. 

What could I do to configure my DNS / network so that sendmail gets it? 

When it installed (i reinstalled after the ubuntugeek option didn't work) it did gave this:
```
WARNING: local host name (matthijs-laptop) is not qualified; see cf/README: WHO AM I?
```

after which it started (with delay...)

---

### Post by Monicker on 2008-05-10
There are several posts in the forums about sendmail and the need for it to have a FQDN Fully Qualified Domain Name) specified in /etc/hosts.  A forum or google search should turn them up.  I recall having similar issues in the past, but I stopped using sendmail years ago after discovering postfix.

You never specified if you actually received an error initially or not, so the first option I gave was merely in case you did happen to be getting that particular error.

---

### Post by bro on 2008-05-11
I wouldn't know how to do this, neither can I find those posts. Thanx anyway. For now I'm just giving up. The time saved by solving this will never by more then the time wasted by solving it. It might miraculously work in 8.10.

---

