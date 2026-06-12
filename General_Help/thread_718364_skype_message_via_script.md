---
title: "skype message via script?"
date: 2008-03-08
forum: General Help
---

### Post by snowmann on 2008-03-08
Hi @all :)

First, sorry for my bad english :roll:
ok here's my question:

Can i send a skype message in the console? 
I have no X-window system installed but i need this in my bash script... 

Have anyone en idea?
Thank 
SowMann

---

### Post by snowmann on 2008-03-10
*push* ;)

---

### Post by snowmann on 2008-03-16
Hi
I found the python- api "Skype4Py". 
Its really easy to send a message with it... \\:D/

Example:

[php]
import Skype4Py

skype = Skype4Py.Skype()
skype.Attach()

skype.CreateChatWith(' CONTACT ').SendMessage('This is a Test')[/php]

cu

---

