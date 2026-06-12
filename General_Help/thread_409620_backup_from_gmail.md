---
title: "backup from gmail"
date: 2007-04-14
forum: General Help
---

### Post by jmvidalvia on 2007-04-14
I am pretty happy with Gmail, but just set up my first ubuntu-server at home and feel like I must do something with e-mail server capabilities: just wondered if it would be possible to use e-mail server like Postfix or whatever to download all e-mails from Gmail and keep a copy of them in my server.
I am not really skilled in that: I assume an e-mail server can not only send but also receive e-mails, but I am not sure about that. 
I know I can do that with Evolution, or other e-mail clients, but my server as no GUI and I would like to keep it that way.
Next step: I would be really happy if I could access my server from my laptop and check those e-mails.
Many thanks!

---

### Post by aysiu on 2007-04-14
I don't know all the details, but there should be email clients available that don't have a GUI. Couldn't you install one of those and use that to download copies of your GMail emails using POP3?

---

### Post by jmvidalvia on 2007-04-15
Yes, that's what I need!
Does anybody know any non-GUI-email-client that could run in my server?
Thanks!

---

### Post by aysiu on 2007-04-15
I don't know quite how to set it up, but *alpine* is a text-based email client.

---

### Post by jmvidalvia on 2007-04-15
I've been also advised about [mutt]("http://www.mutt.org/").
I shall check both: thank you very much!

---

### Post by etola on 2007-04-27
I suggest fetchmail. It is very easy to configure 

[URL="http://download.gna.org/hpr/fetchmail/FAQ/gmail-pop-howto.html"]http://download.gna.org/hpr/fetchmail/FAQ/gmail-pop-howto.html
[/URL]

I'm using it for quite some time now and haven't had  any problems. 

Also, if you would like to move away from gui based email send/receive, you should try emacs + gnus

---

### Post by andrew.46 on 2007-07-02
Hi,

 Came across your page while searching for mutt posts:

> **jmvidalvia said:**
> I've been also advised about [mutt]("http://www.mutt.org/").
I shall check both: thank you very much!

 I have just setup a page that deals specifically with Mutt / Gmail:

[http://people.aapt.net.au/~adjlstrong/mutt.html](http://people.aapt.net.au/~adjlstrong/mutt.html)

               Andrew

---

### Post by jmvidalvia on 2007-07-02
Great guide!
Thank you very much.

---

### Post by Di@blo on 2007-07-02
So you basically want an Exchange server, but for Linux?

---

### Post by jmvidalvia on 2007-07-02
I think not really. Just something to download all my mail from gmail so I can keep a copy of everything in my server, appart from the original I will "always" find in gmail.
Thanks!

---

### Post by andrew.46 on 2007-07-05
Hi,

 Read your post with interest:

> **jmvidalvia said:**
> I think not really. Just something to download all my mail from gmail so I can keep a copy of everything in my server, appart from the original I will "always" find in gmail.
Thanks!

 Just a few things to be cautious with:

[LIST=1]
[*]Make sure and specify the 'keep' option in Fetchmail
[*]Make sure and adjust the "Forwarding & POP" section of Gmail to: "Keep Gmail's copy in the Inbox".
[/LIST]

 Then all should be well!

      Andrew

---

### Post by jmvidalvia on 2007-07-05
> **andrew.46 said:**
> [LIST=1]
[*]Make sure and specify the 'keep' option in Fetchmail
[*]Make sure and adjust the "Forwarding & POP" section of Gmail to: "Keep Gmail's copy in the Inbox".
[/LIST]


Many thanks for your advises!

---

