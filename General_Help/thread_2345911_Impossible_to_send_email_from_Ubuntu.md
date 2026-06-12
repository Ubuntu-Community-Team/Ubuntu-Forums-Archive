---
title: "Impossible to send email from Ubuntu"
date: 2016-12-09
forum: General Help
---

### Post by yodathrawn on 2016-12-09
Hi

I am new to Ubuntu and I am trying to set emails (hotmail).

I received email with Thunderbird correctly. But when I try to send email, it seem that Thunderbird is not able to connect to the smtp server.

"Sending of the message failed.
The message could not be sent because the connection to Outgoing server (SMTP) smtp.live.com timed out. Try again."

I tried to change outgoing server properties (port, connection), use Evolution, disable the firewall, but nothing happened. I cpoied properties of email account from Windows and also my phone but also nothing happened.

I precise that I work on university network and it works well with Windows before.

Does anyone have a solution ? 

Thanks !

---

### Post by howefield on 2016-12-09
I just used the account set up wizard with a hotmail address to automatically detect the servers. It used smtp-mail.outlook.com for smtp.

Try changing your server to that.

---

### Post by yodathrawn on 2016-12-09
It does not solve the issue, still trying to connect to smtp server.

---

### Post by SeijiSensei on 2016-12-09
Probably your ISP is blocking outbound connections via SMTP.  This became a common policy when thousands of malware-infested Windows machines were turned into spambots.  Here's a simple test.  Open a terminal and run this command:

```

telnet gmail-smtp-in.l.google.com 25

```

If your traffic is not blocked, you will see the following:
```

Connected to gmail-smtp-in.l.google.com.
Escape character is '^]'.
220 mx.google.com ESMTP i2si20209327qti.35 - gsmtp

```

If you don't see that reply, then your ISP is blocking outbound SMTP connections.  You'll need to ask if they offer any options like using one of their servers as a relay.

---

### Post by yodathrawn on 2016-12-09
I did this test and it failed... I am working on an university network, I hope the guys from informatics department will have an answer !
Thanks for your help !

---

### Post by kpatz on 2016-12-09
Try port 587 or 465 instead of 25.

---

### Post by yodathrawn on 2016-12-13
I have the same problem with those 2 ports.

---

### Post by yodathrawn on 2016-12-15
I run a port scan using [http://mxtoolbox.com/](http://mxtoolbox.com/) and it said that my port 25 and 587 are open. On the console I have still no coonection using those ports tested with telnet command.
I join a screen of the result here [IMG]https://i.imgsafe.org/2696ac6268.png[/IMG]

How is it possible ?

---

### Post by HermanAB on 2016-12-15
As pointed out above and proved with your own telnet test, you have to sent email via your ISP (in this case your university) SMTP server (probably on port 465), because they drop all outgoing mail packets on the floor.

The other option is to use webmail from your browser.

---

### Post by yodathrawn on 2016-12-16
I will ask to those guys from informatic department how I can have an open smtp port from Ubuntu (on Windows smtp is not blocked). For now I send email using the web browser and manage my received emails with Thunderbird. I really want to use it or Evolution so I hope those informatics guys will have a solution !

---

