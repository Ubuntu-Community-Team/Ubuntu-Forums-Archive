---
title: "MSN (preferably on Pidgin) problem"
date: 2007-09-13
forum: General Help
---

### Post by Joje on 2007-09-13
Well, I've tried, for what feels like a week now, to connect to the msn messenger network. Before that gaim worked like a charm. Finally today, after trying aMSN and Mercury (wich I didn't even manage to install, I think, at least it wont start), I got Pidgin to work. Or so I thought. I realised that even though I'm finaly logged in I can't send messages to anyone but myself. The problem is that the error message is in Swedish and though I'm Swedish I'm not sure how to translate it, but it's something like "Message could not be sent* as a connection error arose". Very detailed :P Btw, ICQ works fine on Pidgin, but not MSN (important) or google (not very important).

*Could also mean "delivered", not sure about the first English -> Swedish translation. Often Swedish translators fail to see the difference between a message being sent and a message being delivered :P So I'm not even sure where the problem is, other than it's somewhere between me and my peeps (no sh**!).

Anyhow, anyone got an idea for solving this problem? I might be really stupid since Ubuntu is teaching me every day how little I really know about administrating a PC so don't hold back the obvious answers, I probably havn't tried them :P

---

### Post by Vadi on 2007-09-13
I suspect it means the message couldn't be sent.

Try clearing your MSN account and setting up a new one? It's pretty simple really, I have no idea where can what mess up.

---

### Post by Joje on 2007-09-13
Hmm, interesting... It seems the problem shifted back to not logging on at all ^^ That's really strange though :S

---

### Post by tszanon on 2007-09-13
There's a bug report about it. If I recall correctly, when using that "HTTP connection" flag (or something like that), you can connect, but can't send messages. It seems that Microsoft changed the protocol.

If I find it again, I'll post it here.

Edit: I didn't find the link to the bug report, but it's not "HTTP connection", it's "Use HTTP method".

---

### Post by ijn on 2007-09-13
something has definitely changed for worst. my pidgin was working excellent since ever. than one day i was able to connect and get the list, but can send and receive messages. this is what I get: Message could not be sent because a connection error occurred.
don't know what happened. I looked around and saw that this problem happens in msn via http.I cant use pidgin with a direct connection and proxy.http is the only way for me to connect to msn in ubuntu 7.04.
help needed

---

### Post by mcduck on 2007-09-13
There is really nothing we can do about it but wait until somebody figures out what changes Microsoft id to the protocol and then changes our messaging clients to work with them.

Or you could send mail to MS and ask them to fix the problem/give the needed information. But I wouldn't hold my breath waiting for their help ;)

As far as I know every single IM program expect Microsoft's own have the same problems now with MSN. One more reason to stay away from proprietary formats/protocols..

---

### Post by w4ett on 2007-09-13
MSN has changed protocols see:

[http://developer.pidgin.im/ticket/2638](http://developer.pidgin.im/ticket/2638)

---

### Post by tszanon on 2007-09-13
> **w4ett said:**
> MSN has changed protocols see:

[http://developer.pidgin.im/ticket/2638](http://developer.pidgin.im/ticket/2638)
Thanks, that's the link I just couldn't find.

> 09/12/2007 11:14:01 PM changed by [email]datallah@pidgin.im[/email]  ¶

    * status changed from new to closed.
    * resolution set to fixed.
    * milestone changed from Merge MSNP14 Branch to 2.2.0.

(In [5d4b00a88466bb9e851eaca42ab3fd3f2c4093ef]) A fix from Laszlo Pandy to make the MSN HTTP Method work again. Fixes #2638 and should make a number of people happy. This introduces a new string that isn't marked as translatable for 2.2.0 because it is so late in the game.
It seems that the next version, 2.2.0, will fix the problem.

---

