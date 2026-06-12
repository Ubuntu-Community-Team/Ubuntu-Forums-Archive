---
title: "Information on configuring Evolution?"
date: 2007-01-27
forum: General Help
---

### Post by Goober on 2007-01-27
Hello fellow Ubuntans!

I have never ever used an E-mail client, like Outlook, Evolution, Thunderbird, etc., I check all my of E-mail online, using Webmail and the such.  I was looking through this thread, and I have come to realize that using Evolution might be simplier then checking my 3 e-mails every morning (and faster!).  But then I realized that I know nothing about configuring Evolution (I'll use that because it comes with Edgy), configuring my E-mails, etc.

So I was wondering - is there a source, with as a wiki or a Howto, that would tell me how to configure my E-mails with Evolution?  I have searched this forum, and did a quick Google search, but came up with nothing.  I started up Evolution, but very quickly for confused with POP, SMTP and all of that.

I have 2 Hotmail E-mails and a Webmail through my College that I want to configure with Evolution.

If anybody could help me with this, I would muchly appreciate it. Thanks in advance!

---

### Post by finer recliner on 2007-01-27
gmail uses the POP3 protocol. 

heres the basic info: 
POP will download your emails messages from the mail server (i.e. gmail) directly to your computer. 
IMAP will leave your email messages on the server, and you syncronize your email client (i.e. evolution) with the server. usually you need to expunge messages to permantly delete them. 
SMTP (simple mail transfer protocol) is how you send email messages to someone else. usually the outgoing server is named something like smtp.domain.com where domain is the name of your email host (example: smtp.gmail.com). ISP's usually offer a smtp server as well.

to configure evolution, you need to look in the help documents of each of your email accounts. most of the time, its very easy to configure. however i know gmail is a little picky about which ports you use, and making sure you use the correct security protocols. not a big deal, they explain everyhting very cleary.

personally i will recommend you use thunderbird. i never bothered to try evolution though.

---

### Post by dcstar on 2007-01-27
> **Goober said:**
> 
..........
So I was wondering - is there a source, with as a wiki or a Howto, that would tell me how to configure my E-mails with Evolution?  I have searched this forum, and did a quick Google search, but came up with nothing.  I started up Evolution, but very quickly for confused with POP, SMTP and all of that.

I have 2 Hotmail E-mails and a Webmail through my College that I want to configure with Evolution.

If anybody could help me with this, I would muchly appreciate it. Thanks in advance!

You should be able to search - either in this forum or on the web - information on setting up your client.

You just have to keep the basics clear: POP3 is receiving your e-mails, SMTP is sending them.

You should be able to set up Hotmail access fairly simply using their instructions for various other e-mail clients.

The Evolution Webmail will only work if your college is running a Microsoft Exchange Web system.

---

### Post by ubromtoo on 2007-01-30
I'm still trying to configure Evolution, a week or so after going to a dual-boot.

  it is sharply disapointing that there is simply no one place to go for help.

     this lack of interest-by Ubuntu and by Evolution- in helping the complete beginner

is really similar to the general Microsoft Windows frame of mind.

   it absolutely should be simple to set up Evolution,  instead, I must go all over the 

 internet looking for help.

    is this any way to fight the Microsoft monopoly?  by turning a cold shoulder to the

 enthusiastic -but ignorant- newcomer?

---

