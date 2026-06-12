---
title: "Thunderbird over a network?"
date: 2006-11-22
forum: General Help
---

### Post by FeraTech on 2006-11-22
I have an ubuntu server. I use it frequently. However, I also have a laptop and another computer I use. What's the best way to sync up all my e-mail? I was thinking of just downloading everything to my server and accessing it from the network on all my other PCs. 

Can this even be done? Currently I can only use my server to check my e-mail. Or sign on to each e-mail account individually.

---

### Post by awbassett on 2006-11-22
If your mail server supports the IMAP protocol, you can set your clients to access the mail that way. If not, you can make your own IMAP server.

I've used this before, however, I am not the author: [http://adomas.org/2006/08/postfix-dovecot/](http://adomas.org/2006/08/postfix-dovecot/)

---

### Post by CatKiller on 2006-11-22
Personally, I just ssh into my computer and run Thunderbird. It doesn't necessarily get you kudos for doing it "properly", but it does work.

---

### Post by CombatGod on 2006-11-23
Well the problem is that I'm using both windows and linux. Over the network I could easily use Samba and access my mail like that if it's possible.

How do you set up IMAP? It seems strikingly similar to pop3. Do you just use the network name?

---

