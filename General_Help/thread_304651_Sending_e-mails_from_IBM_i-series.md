---
title: "Sending e-mails from IBM i-series"
date: 2006-11-22
forum: General Help
---

### Post by jmvidalvia on 2006-11-22
We have an IBM i-series server in the office.
As it has no mail-server and we want so send automatic e-mails from  our ERP, I am considering to use an old pc with ubuntu for this purpose.:-k 
The idea is I configure the IBM with the IP of this pc so e-mails will go from IBM to the PC and then to the Internet.
As i don't need to receive mails from outside, ¿is there any easy way to do that? I've read how to configure a linux mail server, but i just need a system to get local mails and send them outside.
I am usually using mailx and sendmail, so I wonder if they woukd be able to do this work...
Thanks a lot!

---

### Post by awbassett on 2006-11-22
Just to clarify - 

You are looking for something on for an AS/400 to generate emails to send to your Ubuntu box which will then forward the e-mail out to internet hosts?

You can set the Ubuntu box to use a smarthost to forward to your Corporate e-mail servers. 

As far as the AS/400 goes, I'm checking into it...

---

### Post by jmvidalvia on 2006-11-22
Yes.
Mi AS400 is already configured.
It sust needs an ip where the mail server is suposed to be.
I would like that ip to be my Pc with ubuntu, so every help I need is from ubuntu, not for AS400.
Thanks a lot.

---

### Post by awbassett on 2006-11-22
yeah, just do: 

sudo apt-get install postfix

sudo dpkg-reconfigure postfix 

answer all the questions and make your Ubuntu box forward the mail on.

---

### Post by jmvidalvia on 2006-11-23
Thank your very much!

---

