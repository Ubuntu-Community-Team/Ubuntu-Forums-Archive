---
title: "Thunderbird Hangs when connecting to gmail pop server."
date: 2007-02-13
forum: General Help
---

### Post by HIGHLIFE on 2007-02-13
I've been using Thunderbird with gmail for a while though, but in the last few days it has stopped connecting to the gmail pop server.  I also tried kmail and Evolution without luck. I'm sure I have my setting write in the mail clients can someon please help me?

By the way I can connect to the gmail smtp servers.

---

### Post by dexter on 2007-02-13
You could try creating a new temporary gmail account and see if that one works with gmail. If it does, it has something to do with your account, if not, the problem is located after your computer. (you can delete the temporary gmail account afterwards)

---

### Post by HIGHLIFE on 2007-02-13
No that's not working for me either.

---

### Post by MCSE_Crossover on 2007-02-13
What version of Ubuntu are you using? What type of processor do you have in your PC? The only reason that I ask is that I believe in Ubuntu 6.06 using a Dual Core chipset, there was a bug with Thunderbird having trouble connecting remotely via POP and IMAP...

---

### Post by HIGHLIFE on 2007-02-13
I am using Edgy although I do have an athlon X2 4400.

---

### Post by MCSE_Crossover on 2007-02-13
I am using a DualCore 6400 I think or something with Edgy, and mine seems to work ok now. Every once and awhile though, I have trouble connecting to the GMAIL pop server, but it usually clears itself up. Could be the server...they are pretty saturated I think... How long has this issue been going on?

---

### Post by HIGHLIFE on 2007-02-13
It's been going on for the past 2 days.  I've started looking for help becuase this has never happened in the past.

---

### Post by dcstar on 2007-02-13
> **HIGHLIFE said:**
> I've been using Thunderbird with gmail for a while though, but in the last few days it has stopped connecting to the gmail pop server.  I also tried kmail and Evolution without luck. I'm sure I have my setting write in the mail clients can someon please help me?

By the way I can connect to the gmail smtp servers.

Check you network connectivity in a terminal:
```
telnet your-gmail-pop-server-ip 110
```
If you get a response, then you don't have a network issue, if it just hangs then you have to check what is blocking your packets.

If you get a response you can also try logging in with your user account name and password.

---

### Post by szf on 2007-02-13
Have you followed the [help topics]("http://mail.google.com/support/bin/topic.py?topic=1555") to properly access your gmail account? 

Possible problem areas:
[LIST]
[*]You haven't enabled POP access on your gmail account 
[*]Incorrect port number (it would be a good thing if access defaulted to secure POP)
[*]An earlier configuration ran afoul of 1 mailbox check per 5 (?) minute period
[/LIST]

---

### Post by HIGHLIFE on 2007-02-14
> **szf said:**
> Have you followed the [help topics]("http://mail.google.com/support/bin/topic.py?topic=1555") to properly access your gmail account? 

Possible problem areas:
[LIST]
[*]You haven't enabled POP access on your gmail account 
[*]Incorrect port number (it would be a good thing if access defaulted to secure POP)
[*]An earlier configuration ran afoul of 1 mailbox check per 5 (?) minute period
[/LIST]

Like I said I have all of these settings right.  And my mail had been working for the past few months.

Dcstar how would I find my gmail pop server ip?

---

### Post by MCSE_Crossover on 2007-02-14
You aren't behind a firewall or anything are you? Are you accessing from work? A University? From what I remember, the POP gmail connections do not use the default POP and SMTP ports...

For your POP settings, they need to be configured as port 995 using SSL (Secure POP)

your SMTP settings need to bec onfigured as port 587 with TLS secure connection.

Also, again, make sure POP is enabled in GMAIL.  I don't doubt you have taken these steps already, but it doesn't hurt to quadruple check. I have over looked things when I had already looked at it 15 times :)

---

### Post by HIGHLIFE on 2007-02-14
> **MCSE_Crossover said:**
> You aren't behind a firewall or anything are you? Are you accessing from work? A University? From what I remember, the POP gmail connections do not use the default POP and SMTP ports...

For your POP settings, they need to be configured as port 995 using SSL (Secure POP)

your SMTP settings need to bec onfigured as port 587 with TLS secure connection.

Also, again, make sure POP is enabled in GMAIL.  I don't doubt you have taken these steps already, but it doesn't hurt to quadruple check. I have over looked things when I had already looked at it 15 times :)

As I said previosly I have everything properly configured, it's been working for the past few months and I haven't touched the settings (I also went and checked after it stopped working).

---

### Post by MCSE_Crossover on 2007-02-14
That is why I was wondering if you were behind some sort of corporate or university firewall or if you were trying to access from home. If you were at work or a university, perhaps they restricted some port or something...i'm beating my head trying to think why this wouldn't work. Have you done any recent upgrades? Added new software? Made any system changes?

---

### Post by HIGHLIFE on 2007-02-14
I'm at home and I recently installed ssh server.

---

### Post by MCSE_Crossover on 2007-02-14
Try disabling SSH server or configure it to listen on a different port. See if that resolves your problem. Could be a port conflict...

*EDIT* Could be a certificate issue as well if your POP traffic is attempting to tunnel.

Did your problems start occuring right around the same time as you installed SSH?

---

### Post by Collin White on 2007-02-14
I am having a similar issue with my Comcast account.  The connection to the mail server times out using both Thunderbird and Evolution, and also when I attempt to telnet.  It pings fine, however.

I'm pretty sure it's not a network issue as my wife's Windows box connects fine.  My account settings haven't changed in the several months I have been using Ubuntu.  In fact, it's only been having this issue for about a week, which makes me wonder if it is related to a recently installed update.

---

### Post by MCSE_Crossover on 2007-02-14
> **Collin White said:**
> I am having a similar issue with my Comcast account.  The connection to the mail server times out using both Thunderbird and Evolution, and also when I attempt to telnet.  It pings fine, however.

I'm pretty sure it's not a network issue as my wife's Windows box connects fine.  My account settings haven't changed in the several months I have been using Ubuntu.  In fact, it's only been having this issue for about a week, which makes me wonder if it is related to a recently installed update.

Are you using SSH on your Linux installation as well?

---

### Post by Collin White on 2007-02-14
> **MCSE_Crossover said:**
> Are you using SSH on your Linux installation as well?

Can't say as I know what SSH is, sorry.  Is it a default setting?

---

### Post by MCSE_Crossover on 2007-02-14
> **Collin White said:**
> I am having a similar issue with my Comcast account.  The connection to the mail server times out using both Thunderbird and Evolution, and also when I attempt to telnet.  It pings fine, however.

I'm pretty sure it's not a network issue as my wife's Windows box connects fine.  My account settings haven't changed in the several months I have been using Ubuntu.  In fact, it's only been having this issue for about a week, which makes me wonder if it is related to a recently installed update.

It is a tunneling program, in basic format.

Try using the IP address of 66.249.83.111 instead of pop.gmail.com

---

### Post by dcstar on 2007-02-14
> **HIGHLIFE said:**
> Like I said I have all of these settings right.  And my mail had been working for the past few months.

Dcstar how would I find my gmail pop server ip?

It is whatever you have in your e-mail client right now.

---

### Post by szf on 2007-02-15
For those on this thread that also have access to a Windows-boxen, the [Gmail POP troubleshooter]("http://mail.google.com/support/bin/answer.py?answer=44769") is available, too.

---

### Post by HIGHLIFE on 2007-02-17
Alright I shutdown ssh and changed it's port neither worked.

I went on my windows partition and thunderbird works, but not on linux. :(

---

### Post by HIGHLIFE on 2007-02-18
No ideas?  I'm still trying to figure this out.

---

### Post by maver1ck4000 on 2008-04-07
I had this trouble too, google service is used for our company and it was alittle different set up with ports and things, however the only thing that seemed to fix my problem is to go in to the account settings on web mail and change the pop mail to enable again, once I did that it started working again.  I am wondering if it's something to do with imap, it looked like mine was trying to access an IMAP connection which could be dependant on my service...I really don't have an answer but reading this thread convinced me to go in and start over and now it works for me.

---

