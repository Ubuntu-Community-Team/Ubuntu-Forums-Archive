---
title: "Change mail from adress with postfix"
date: 2006-07-07
forum: General Help
---

### Post by El_Matthews on 2006-07-07
Gents


it seems my providor is blocking mails from my system because the mail adress from which it is sent from isn't correct. all my logs etc are sent to my ISP adress but the mail generated has as sender adress [email]root@localhost.com[/email].

How can I change this so that it appears that my system is sending mail from [email]MyAccount@ISP.com[/email]. This should be done for all outgoing mails.

---

### Post by mgor on 2006-07-07
take a look at /etc/mailname, the file should contain a valid domain from which the mails will appear to come from, i.e.
```
ISP.com
```

regarding the username, did you setup an alias for root in /etc/aliases?
```
root: MyAccount@ISP.com
```

don't forget to run 'newaliases' after chaning the aliases file.

it might just be that your ISP dosen't allow you to send mail directly from your own mailserver. to fix that you just have to relay your mails throught theirs, edit /etc/postfix/main.cf and change the 'relayhost' parameter:
```
relayhost = mail.ISP.com
```

save the file and restart postfix.

---

### Post by El_Matthews on 2006-07-07
Thank you for the fast replay

so what did a do :
- i added root in /etc/aliases
[INDENT][/INDENT]entry = root: [email]myname@isp.com[/email]
- runnend command newaliases
- changed /etc/mailname to isp.com
- restarted postfix

tested with telnet localhost 25
mail from: root
rcpt to: [email]myname@isp.com[/email]
data
test
.
quit

now I checked my mailbox and the mail I receive comes from:
[email]root@isp.com[/email]

also the to field = undisclosed-recipients

Any idea how we can translate the root part to myname ?


PS: I am testing this for the moment on a non-restrictive smtp at my work.

---

### Post by mgor on 2006-07-07
oops, my bad. changing aliases will ofcourse not rewrite the username sent from.
check out the postfix documentation[0], 
> Replace an internal address by an external address. For example, replace "username@localdomain.local" by "isp-account@isp.example" when sending mail from a home computer to the Internet.

[0] [http://www.postfix.org/ADDRESS_REWRITING_README.html#delivering](http://www.postfix.org/ADDRESS_REWRITING_README.html#delivering)

---

### Post by El_Matthews on 2006-07-10
Hello mgor,

- I changed my /etc/mailname back again to localdomain.local
- I added smtp_generic_maps = hash:/etc/postfix/generic to my main.cfg
- created file /etc/postfix/generic with content :
[INDENT]mg@localdomain.local[INDENT]surname.name@domain.com[/INDENT][/INDENT]
- restarted postfix


tested it with :
telnet localhost 25
mail from: [email]mg@localdomain.loca[/email]l (should be changed)
rcpt to: [email]surname.name@domain.com[/email]
data
test
.
quit


Now I don't receive anything anymore, what am I doing wrong ?

---

