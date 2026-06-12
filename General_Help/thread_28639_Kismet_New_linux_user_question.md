---
title: "Kismet New linux user question"
date: 2005-04-21
forum: General Help
---

### Post by groban on 2005-04-21
Hi

I am trying to install kismet and in configure i found the message
that can't find the curses lib...

How can i install it???

Also i have a problem with the lpcap because he wants the flex
instead of lex. How can i install it too???

Thanx for your time

I wil apreciate any help....

grob

---

### Post by fdoving on 2005-04-21
[QUOTE=groban]Hi

I am trying to install kismet and in configure i found the message
that can't find the curses lib...

How can i install it???

Also i have a problem with the lpcap because he wants the flex
instead of lex. How can i install it too???

Thanx for your time

I wil apreciate any help....

grob[/QUOTE]
 Hello,

You can install kismet from the universe repository.

[http://ubuntuguide.org/#repositories](http://ubuntuguide.org/#repositories)

---

### Post by fdoving on 2005-04-21
[QUOTE=groban]Hi

I am trying to install kismet and in configure i found the message
that can't find the curses lib...

How can i install it???

Also i have a problem with the lpcap because he wants the flex
instead of lex. How can i install it too???

Thanx for your time

I wil apreciate any help....

grob[/QUOTE]
 STEP 1. - Adding universe repository to you setup
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

Do as explained. 
Change the country-code to something close to you, if you don't live in the US.

STEP 2. - Installing kismet
Run this command: sudo apt-get install kismet

That should be it, kismet should be automagically get installed.

- Frode

---

