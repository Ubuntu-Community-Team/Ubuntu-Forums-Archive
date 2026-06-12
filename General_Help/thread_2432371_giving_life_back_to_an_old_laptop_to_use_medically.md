---
title: "giving life back to an old laptop to use medically, and slack chat and clam av email."
date: 2019-12-01
forum: General Help
---

### Post by vanquishedangel on 2019-12-01
So the old laptop in question is a Dell Lattitude D430. 2 gigs ram.

The story, I got a promotion and I manage a group home for special needs. 

I had a choice of an Ipad or a laptop, I picked the iPad because I can take pictures and email them in an instant for house repairs etc. However, I have to write ISP's (individual service plans) and other things like articles and such. I decided to use an old laptop for these things that I had lying around collecting dust. I am typing this on it now. However, it runs Linux (lubuntu 19.10 64bit) and I need to meet a few standards legally required. 

1. Secure Emails, they need to be encrypted and the company uses sendinc. Only thunderbird has worked with the company email but has issues with send inc. A link to instructions is here, but it does not work right ([http://docs.sendinc.com/docs/smtp-api](http://docs.sendinc.com/docs/smtp-api)). I also need to scan emails automatically with an AV, however, clam does not have a supported plugin for Thunderbird. I did create a filter wrapper for sylpheed in the past, but it does not seem to work with Thunderbird. 

2. The managers chat we use is slack, I would like to access it via a messenger but I can not get pidgin to see the intalled plugin, are there any others that might work?

---

### Post by DuckHook on 2019-12-02
> **vanquishedangel said:**
> …1. Secure Emails, they need to be encrypted and the company uses sendinc. Only thunderbird has worked with the company email but has issues with send inc. A link to instructions is here, but it does not work right ([http://docs.sendinc.com/docs/smtp-api](http://docs.sendinc.com/docs/smtp-api)).
I have no understanding of sendinc, but others may be able to help if you expand with details on what you mean by "does not work right".
> I also need to scan emails automatically with an AV, however, clam does not have a supported plugin for Thunderbird.
AFAIK, this is correct. The only CLAM plugin I was aware of was nerfed in T-Bird a few upgrades ago. I don't know of any workarounds.
> 2. The managers chat we use is slack, I would like to access it via a messenger but I can not get pidgin to see the intalled plugin, are there any others that might work?
A web search yielded this: [https://github.com/dylex/slack-libpurple](https://github.com/dylex/slack-libpurple)

Is there a reason for trying to roll it into a messenger app like *pidgin*, or is standalone okay? There is a standalone snap app, though it is technically still in beta: [https://snapcraft.io/slack](https://snapcraft.io/slack)

---

### Post by SeijiSensei on 2019-12-02
Most providers of secure email services have a webmail interface. Looks like sendinc does, too: [http://docs.sendinc.com/docs/sending-a-secure-message](http://docs.sendinc.com/docs/sending-a-secure-message)

It sounds like you have two different types of email services, one that is HIPAA-compliant using sendinc, and another for all your other mail.  Where is that mail stored? Is it on a server you manage? If so, I strongly recommend installing [MailScanner]("http://mailscanner.info/") which will use ClamAV and SpamAssassin to scan all your mail.  If the server is elsewhere, why do you think its administrators aren't already scanning for viruses and spam?

---

### Post by vanquishedangel on 2019-12-02
> **SeijiSensei said:**
> Most providers of secure email services have a webmail interface. Looks like sendinc does, too: [http://docs.sendinc.com/docs/sending-a-secure-message](http://docs.sendinc.com/docs/sending-a-secure-message)

It sounds like you have two different types of email services, one that is HIPAA-compliant using sendinc, and another for all your other mail.  Where is that mail stored? Is it on a server you manage? If so, I strongly recommend installing [MailScanner]("http://mailscanner.info/") which will use ClamAV and SpamAssassin to scan all your mail.  If the server is elsewhere, why do you think its administrators aren't already scanning for viruses and spam?

It is a legal requirement I believe. Yes our company has its own mail server, but I do not manage it. I suppose you are correct that they most likely have mail scanning, but it is required on all the computers we use. We use the company email for all correspondence and connect to other website, like say we buy movie tickets on $5 night as an activity for the residents and other things. 

We use sending for their teams, like guardians, doctors, nurses, and information between us. We also use slack to talk between managers.

---

### Post by vanquishedangel on 2019-12-02
> **DuckHook said:**
> I have no understanding of sendinc, but others may be able to help if you expand with details on what you mean by "does not work right".

AFAIK, this is correct. The only CLAM plugin I was aware of was nerfed in T-Bird a few upgrades ago. I don't know of any workarounds.

A web search yielded this: [https://github.com/dylex/slack-libpurple](https://github.com/dylex/slack-libpurple)

Is there a reason for trying to roll it into a messenger app like *pidgin*, or is standalone okay? There is a standalone snap app, though it is technically still in beta: [https://snapcraft.io/slack](https://snapcraft.io/slack)

I did not run across the standalone app so I may give that a go, I tried to compile the lib purple one before and the make/ make install seemed to work but the plungin is not showing in pidgin. As for sendinc. It gets the information from the server when setting it up, but then denies the connection. I tried the alias email they give, but it fails to. I suspect maybe this was an update to thunderbird that is cause ink the problem.

---

### Post by SeijiSensei on 2019-12-03
> **vanquishedangel said:**
> It is a legal requirement I believe.
Yes, it's known as "HIPAA" after the law that brought these requirements into effect.  You must not send "patient health information" over an insecure channel. (I designed an appointment system for a medical client once and had to abide by these rules.)  However, if you use a web-based service to send secure mail, then you should be compliant.  The connection from your computer to sendinc is encrypted using SSL, and sendinc employs whatever methods it uses to send the secure message.  You'd give up having all the mail in Thunderbird, but it's the easiest solution.

> Yes our company has its own mail server, but I do not manage it. I suppose you are correct that they most likely have mail scanning, but it is required on all the computers we use.
I suspect that's not true. If you use the company's mail server, and the mail arriving there is scanned, there is no further need to scan it at the client end as well. Talk to the company's lawyer.

[Sophos]("https://www.ubuntupit.com/best-linux-antivirus-top-10-reviewed-compared/") apparently does on-demand scanning on Linux desktops. Or you could write a script that runs the clamscan program from ClamAV periodically. Use the -i and -r command line switches and mail the results to you.  Install ClamAV with the command "sudo apt install clamav". The clamscan program will be installed as part of the package. After you've installed it, run the command "man clamscan" to get details on the options it supports.

---

### Post by Skaperen on 2019-12-03
a friend of mine works in IT at a big local hospital (i've had the pleasure of staying there a few times).  he tells me that the main medical network is totally isolated from the internet.  doctors can get to the internet on request but their access is through a firewall that blocks port 80.

---

