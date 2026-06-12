---
title: "How to connect to IRC server?"
date: 2021-01-28
forum: General Help
---

### Post by jmichaels29 on 2021-01-28
Using HexChat, I'm trying to connect to the irc server irc.freenode.net 
to participate in ubuntu channels.

See 3 screenshots

---

### Post by &amp;KyT$0P# on 2021-01-29
The problem is shown in your first screenshot.  Instead of
```
newserver/6667
```
you need to put in freenode's servers as [documented in their knowledge base]("https://freenode.net/kb/answer/chat").

---

### Post by jmichaels29 on 2021-01-29
> **halogen2 said:**
> The problem is shown in your first screenshot.  Instead of
```
newserver/6667
```
you need to put in freenode's servers as [documented in their knowledge base]("https://freenode.net/kb/answer/chat").

See screenshot

---

### Post by &amp;KyT$0P# on 2021-01-29
No, I meant set it up in the dialog shown in your first screenshot: the one titled "Edit irc.freenode.net - HexChat" and that actually shows "newserver/6667".  You need to replace "newserver/6667" there with the info from freenode knowledge base.

---

### Post by jmichaels29 on 2021-01-29
> **halogen2 said:**
> No, I meant set it up in the dialog shown in your first screenshot: the one titled "Edit irc.freenode.net - HexChat" and that actually shows "newserver/6667".  You need to replace "newserver/6667" there with the info from freenode knowledge base.

Attached

---

### Post by QIII on 2021-01-29
Try ***irc.freenode.net***, not ***chat.freenode.net***. You will find #ubuntu and also our chat #ubuntu-forums.

If you are on a mobile device you will need to identify through SASL.

Edit: by way of explanation -- the problem is not mobile devices *per se*, but the fact that their ranges of IP addresses are often suspect.  If you are on a desktop and the IP assigned by your ISP is in a suspect range, you may also have to identify through SASL.

---

### Post by jmichaels29 on 2021-01-29
i get kicked off because I don't "identify as SASL"
I'm assuming I need to register with nickserv - a name and email and password
Kind hard to register with nickserv when you can't log on

---

