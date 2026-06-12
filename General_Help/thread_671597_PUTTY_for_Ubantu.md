---
title: "PUTTY for Ubantu??"
date: 2008-01-18
forum: General Help
---

### Post by dodgingspam on 2008-01-18
On a Windows PC I use PuTTY: a free telnet/ssh client. Can I use it with Ubantu or is there something else compatible?

Thanks

---

### Post by PinkFloyd102489 on 2008-01-18
sudo apt-get install putty



or you can use the termina by doing "ssh hostname/ip"

---

### Post by Joeb454 on 2008-01-18
It's easier to use the normal terminal...you can just use ssh exactly as described above...eg

[CODE]ssh joe@joeb454.co.uk,/CODE] or whatever :)

---

### Post by scorp123 on 2008-01-18
> **dodgingspam said:**
> On a Windows PC I use PuTTY: a free telnet/ssh client. Can I use it with Ubantu or is there something else compatible? OK, I suppose you are new to Linux? There are shell commands:
```
telnet
ssh

```
And yes, there is even **putty** too (available via the repos, so you have to install it, it's not there per default), but you don't really need it (that's why it's not there per default).

[B]ssh youruser@remotesystem
telnet remotesystem[/B]

That's all you need here.

---

### Post by sports fan Matt on 2008-01-18
> **scorp123 said:**
> OK, I suppose you are new to Linux? There are shell commands:
```
telnet
ssh

```
And yes, there is even **putty** too (available via the repos, so you have to install it, it's not there per default), but you don't really need it (that's why it's not there per default).

[B]ssh youruser@remotesystem
telnet remotesystem[/B]

That's all you need here.

My question is, what does this do and what are advantages or disavantages of it? ive never heard of it

---

### Post by PinkFloyd102489 on 2008-01-18
PuTTY is just a seperate program that does the same thing that the terminal does.

---

### Post by dodgingspam on 2008-01-18
OK, if I can use terminal I can try to figure it out. Just to make it clear, when I use PUTTY I'd enter IP, then USER ID and then I'm prompted for password.

When I tried to use terminal, I typed

> ssh 444.333.222.11 

Bu after that I'm prompted for password...?

I've tried: 
> ssh my Ip @loginp too. But I keep getting >  Name or service not knownI bit lost.

---

### Post by dodgingspam on 2008-01-18
Got it to work.... Not sure why it did not work initially.:)

---

### Post by PinkFloyd102489 on 2008-01-18
Input the password for the remote machine when prompted.

---

### Post by scorp123 on 2008-01-18
> **sox fan Matt said:**
> My question is, what does this do and what are advantages or disavantages of it? ive never heard of it "putty" was originally written for Windows, so that's why people coming from Windows maybe know it: It's the only free + good Telnet + SSH client. There are other packages but either those aren't free or not good.

So when users change from Windows to Linux it could be that they ask "Where can I find putty?" because they don't know yet that they could use "ssh" and "telnet" commands right away, and that unlike in Windows they in fact don't really need "putty" here on Linux.

---

### Post by PilotJLR on 2008-01-18
```

ssh loginname@ipaddress

```

I hope the "loginname@" part answers your question

---

