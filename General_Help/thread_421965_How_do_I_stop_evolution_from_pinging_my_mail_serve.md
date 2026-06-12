---
title: "How do I stop evolution from pinging my mail server?"
date: 2007-04-24
forum: General Help
---

### Post by xdevnull on 2007-04-24
First, this doesn't always seem to work, as I get an error pop-up.

Second, why does it do it in the first place?  I mean, I understand ping and icmp, but lots of mail and web servers drop icmp for good reasons - so just b/c evolution can't ping it doesn't mean its down.

Third:  HOW do I get it to STOP?!  Sometimes when I come back from a hibernate, the first thing evolution does is try and ping the mail sever, which doesn't usually work because the wireless hasn't connected yet - and it will hang there.  GRRR!  I haven't been able to find an option anywhere - I hope I don't have to compile it without some option to get the pinging to stop.

---

### Post by ramjet_1953 on 2007-04-25
OK, open Evolution and click on [COLOR="Blue"]Edit>Preferences[/COLOR]

A window should now open

Click on the relevant email account to highlight it (Don't click on the button with the X in it)

Click on the[COLOR="Blue"] edit [/COLOR]button

Another window should open

Click on the [COLOR="Blue"]Receiving Options[/COLOR] tab

Un-check the [COLOR="Blue"]Automatically check for new mail button[/COLOR]

Click on [COLOR="Blue"]OK[/COLOR]

Close down Evolution and re-start it.

Regards,
Roger 8)

---

### Post by xdevnull on 2007-04-25
Thanks for taking the time to reply :).  However, I do know about that option.  I guess my point is evolution doesn't need to ping a server to check for mail.  In fact icmp can't get any information about whether a mail server is even running, much less whether there is mail there.  I would like evolution to continue to check if I have email.  It should be able to do that without pinging it.:confused:

---

