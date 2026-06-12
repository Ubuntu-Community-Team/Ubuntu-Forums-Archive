---
title: "MDADM email notifications not working."
date: 2013-08-02
forum: General Help
---

### Post by Roasted on 2013-08-02
Hello. I have had mdadm set up for quite a long time, but one thing I never set up was email notifications in the event a drive tanks. I Googled around and I got a lot of hits for one particular set of instructions. Basically I had to add my gmail account to the mdadm.conf file. I then ran the following command:

mdadm --monitor --scan --test

I even ran it with mdadm --monitor --scan --test --no-sharing, but no dice. All I get back is:

mdadm: Only one autorebuild process allowed in scan mode, aborting

At this point every link on Google search is purple as I was trying to dig up what I might be doing wrong. So far all sources suggest I am doing this right? Does anybody have any insight? Just add email adress to MAILADDR in mdadm.conf and call it a day?

Thanks!

---

### Post by dcstar on 2013-08-02
> **Roasted said:**
> Hello. I have had mdadm set up for quite a long time, but one thing I never set up was email notifications in the event a drive tanks. I Googled around and I got a lot of hits for one particular set of instructions. Basically I had to add my gmail account to the mdadm.conf file. 
........
At this point every link on Google search is purple as I was trying to dig up what I might be doing wrong. So far all sources suggest I am doing this right? Does anybody have any insight? Just add email adress to MAILADDR in mdadm.conf and call it a day?

Thanks!

You need a working local SMTP server (like Postfix) correctly set up and working on your system, or use one of the various scripts around that specifies an external SMTP server setting to send mail.

AFAIK the mail sending of MDADM assumes that you have the local SMTP going.

---

### Post by SaturnusDJ on 2013-08-02
You can use this one by Rubylaser: [http://zackreed.me/articles/39-send-system-email-with-gmail-and-ssmtp](http://zackreed.me/articles/39-send-system-email-with-gmail-and-ssmtp)

---

