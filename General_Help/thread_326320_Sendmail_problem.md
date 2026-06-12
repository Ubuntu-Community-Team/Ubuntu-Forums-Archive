---
title: "Sendmail problem"
date: 2006-12-27
forum: General Help
---

### Post by dannyboy79 on 2006-12-27
This is a log file every minute or so.
sendmail[25639]: My unqualified host name (localhost) unknown; sleeping for retry
Dec 18 00:52:08 localhost sendmail[25639]: unable to qualify my own domain name (localhost) -- using short name.

Is this bad?? I can say that I don't have a domain name yet but since my router supports using dyndns I was going to get a free one soon, will this solve this?

Another thing in my log file all the time is this
Dec 27 09:03:16 localhost sm-mta[13047]OTP unavailable because can't read/write key database /etc/opiekeys: No such file or directory

Are these related? Should I create a directory /etc/opiekeys so that this whatever database can be stored there? Why wouldn't it have been created when I installed sendmail?

Any help would be appreciated.

---

### Post by dcstar on 2006-12-27
> **dannyboy79 said:**
> This is a log file every minute or so.
sendmail[25639]: My unqualified host name (localhost) unknown; sleeping for retry
Dec 18 00:52:08 localhost sendmail[25639]: unable to qualify my own domain name (localhost) -- using short name.

Is this bad?? I can say that I don't have a domain name yet but since my router supports using dyndns I was going to get a free one soon, will this solve this?

Another thing in my log file all the time is this
Dec 27 09:03:16 localhost sm-mta[13047]OTP unavailable because can't read/write key database /etc/opiekeys: No such file or directory

Are these related? Should I create a directory /etc/opiekeys so that this whatever database can be stored there? Why wouldn't it have been created when I installed sendmail?

Any help would be appreciated.

Firstly, sendmail is obsolete, install the **postfix** package instead.

Check your Network settings or /etc/hosts file to ensure that there is the appropriate entry for your system.

---

### Post by dannyboy79 on 2006-12-28
sendmail may be older but it's not obsolete. all i use it for is sending me emails from cron, tripwire, rkhunter, and chkrootkit. i instaled postfix and couldn't get it to work. way to much configuration for what I want to have email for. I don't want an email server so sendmail is easy and perfect. my host file has a name in it! any other thoughts?

---

### Post by dpgraves on 2007-03-01
I have this same issue with send mail I am running two machines one old pII and an amd64 the pII has no problems but the amd64 has this same error message if someone can help this would be great I use send mail to send auto email once my machine has been automatically updated.

pII not problems at all but amd64 still sends mail but error in logs and if restart computer problem starting basic networking telling me to not rights to remove sendmail.cf 

will give as much info as required to fix.

Cheers

---

