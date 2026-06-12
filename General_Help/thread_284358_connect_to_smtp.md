---
title: "connect to smtp"
date: 2006-10-25
forum: General Help
---

### Post by mikeymouse on 2006-10-25
I cannot send email from thunderbird or evolution.
When i try it says 'no route to host'
I can receive email but not send.
I have tried using network logon and gnomeppp and i cannot send email.
 I know the information i have entered for smtp is correct as i have Xandros,puppy linux and xp all working just fine.
 If anyone can help it would be appreciated.
 thanks mikeymouse

---

### Post by matthewstory on 2006-10-25
are you sure that you're allowed to access the SMTP server from the IP you're at?  Is the SMTP server on the same network?  Can you access the SMTP server from other machines on the network?  Is the SMTP server running?  And have you specified the correct port?  e.g. if it's SMTP with SSL it's not port 25, (don't remember the exact port, but it should be an option in thunderbird, and if not a google search should do the trick).

---

### Post by mikeymouse on 2006-10-25
Hi:
 I have 4or 5 other operating systems and all are working ok. 
 Its only in Ubuntu I cannot send email thru my server. I am on dialup. everything in the configuration is fine. Its as much of a mystery to me, figured maybe someone else might have run into this problem..
 thanks for you interest.
 mikeymouse](*,)

---

### Post by matthewstory on 2006-10-25
Ok, well . . . check the firewall on the SMTP server, to make sure it's allowing from, and check your ubuntu firewall settings as well to make sure nothing funky is going on their either:

iptables -L -n

In addition to this, it might be a networking error on the Ubuntu machine, try to ping the SMTP server . . . 


ping <mail server IP>

If this doesn't work, the issue is probably a general network set up thing, as opposed to a ubuntu SMTP client specific problem.

---

### Post by Roberto Rosselli on 2006-11-29
I have exactly the same problem with Evolution, I can receive mail but can't send, and the smtp server doesn't seem to be blocked by the firewall because I can telnet and ping it just fine.

This is getting quite frustrating, it started a couple of weeks ago with no apparent cause.

Any ideas? 

Roberto

---

### Post by manwell77 on 2007-11-05
Same problem!

I cannot send mail : NO ROUTE TO HOST. And also i cannot sign with PGP keys : secret key not found even if it exists (list from bash!); but the problem seems appear only when i reply to a mail : if i send a new one everything's going ok!

---

