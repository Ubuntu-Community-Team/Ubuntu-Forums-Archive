---
title: "Webmail extension in Thunderbird time-out"
date: 2007-05-15
forum: General Help
---

### Post by Hansje on 2007-05-15
Hey, 

My windows machine let me down again, so i was tired of it. I copied my mail and files to Linux. No big deal... In windows I used Hotpop to get my hotmail-mail in Thunderbird, but hotpop is windows only, so i can't use it in linux. After some searching i installed the webmail extension and the hotmail extension for thunderbird.  I changed the server from my hotmail account from 127.0.0.1 to hotmail.com. He tries to connect to hotmail.com, but after a while he is just telling me the server timed-out. I know that this can happen if the ports are blocked. So my question is: how can i verify whether ports are blocked in ubuntu? Port 25 and 110 should be open for both incoming and outgoing connections (i hope i got it correct here)

Greetz
Hansje

---

### Post by vtel57 on 2007-05-16
I set my Webmail ports to 1100 and 2500.

[I]From the [Webmail FAQ]("http://webmail.mozdev.org/faq.html"):

Q: The Webmail server status is "ERROR"


A: Check your firewall isn't blocking Thunderbird from opening a connection to localhost.

**Some OS's block ports below 1024, set the ports used by Webmail to values higher then 1024**[/I]

Luck! :)

---

### Post by Hansje on 2007-05-16
Can you change the ports without any consequences? I was looking for a way to unblock port 110 to localhost, but I'll try this. I'm not at home this moment, I'll let you know results.

Greetz and thanks
Hansje

---

### Post by vtel57 on 2007-05-16
Sure. In Webmail Extension --> Preferences, just set the ports to whatever you want. 1100 and 2500 are unused ports. That's why I chose them. Works fine on all of my operating systems (1 Windows and 7 Linux). :)

---

### Post by Hansje on 2007-05-21
I get this error after giving my password: "negative vibes from [email]hansvery@hotmail.com[/email]"

I looked up the problem, i found this: "A security fix from DeerPark has been included in to Aviary which breaks 
the extension.  This  breakage has been fixed in DeerPark but this fix 
hasn't been included in TB 1.0.7. 

The only component which could work in TB1.0.7 is Lycos."

I am working with TB 2.0.0.0 (20070326)
Is there a way arrount this issue?

Greetz

---

### Post by vtel57 on 2007-05-21
Sorry. :( 

I don't know if the Webmail extensions are compatible with TB 2.0. You can go the the Webmail extension's website to read more about their app.

---

### Post by darknightuk on 2007-05-25
webmail works fine with 2.0 needs permission change in /.mozilla-thunderbird/rhsditow.default/WebmailData

---

