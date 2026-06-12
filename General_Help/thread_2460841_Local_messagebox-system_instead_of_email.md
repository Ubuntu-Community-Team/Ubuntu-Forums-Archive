---
title: "Local messagebox-system instead of email?"
date: 2021-04-20
forum: General Help
---

### Post by Elmi77 on 2021-04-20
Hi,

nowadays email communication is quite insecure - not only in terms of encryption but there is also the spam-issue. When one sends a mail to an other person, one can not be sure it really arrives in their inbox. Often mails are lost in spam-folder although they are not spam but normal, regular and valid messages. So when somebody wants to be really sure an information arrives, email is not the proper solution.

So my question is: are there other possibilities available (beside of letters on paper or fax)? What I could imagine is e.g. some kind of mailbox system that does not send the messages through the internet but all stays on the same server. So communication would work like this:

- A wants to send a message to B
- A signs up at the message server of B, writes the message and sends it
- B logs into the message server, finds the message and answers it
- later A checks back if there is an answer, log into the message server, finds the answer and can respond to it again

In such a scenario no message will get lost. Captchas could be used to ensure A is always a real person and not a spambot. Ad the working principle is more like a dead letter box that is not supplied by a postal service but where all participants go to personally.

So my question: does such a solution exist? Or something similar which overcomes the problem of emails that do not arrive due to a too aggressive spam-filter?

Any idea and suggestion is welcome!

---

### Post by HermanAB on 2021-04-20
There are several ways to do that.  
a. You can open a Google/Yahoo/Whatever Mail account and give the login details to all the parties.  Then use the Drafts Folder as a drop box and don't actually send the email, so it never leaves the mail server.
b. You can use Google Docs and collaborative edit a document.
c. Retroshare: [http://retroshare.cc/index.html](http://retroshare.cc/index.html) 

Use your imagination...

---

### Post by Elmi77 on 2021-04-21
This is unfortunately not the solution I'm looking for. Similar to "normal" mail people of course should not see what others are writing. So sharing general access like you suggest it is far away from being a usable solution.

---

### Post by HermanAB on 2021-04-21
So set up a Retroshare system.

---

### Post by dragonfly41 on 2021-04-21
One untested idea off the top of my head .. send messages via RabbitMQ.
It allows one-to-one and one-to-many messages.
Also serve messages via CloudAMQP.
I use the Python bindings.

Confirmation comes from the consumer acknowledging receipt.

---

