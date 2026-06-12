---
title: "XP PRO launch issue"
date: 2007-09-26
forum: General Help
---

### Post by lorent_tt on 2007-09-26
hi to all
I want to launch WUBI from XP PRO but nothnig append!
No windows, no thread = nothing...
I'm administrator and I've reloaded the wubi several times for the same result
What's going on ?
Thanks for your help

---

### Post by ago on 2007-09-26
What version of wubi are you using?
Do you see a dialog as in the screenshots?

---

### Post by lorent_tt on 2007-09-27
I'm using the latest version 7.04.04
And no windows appears to the screen (I've already install Wubi on an other pc so I'm a litlle bit familliar with)
Thanks for your help
:)

---

### Post by ago on 2007-09-27
> **lorent_tt said:**
> I'm using the latest version 7.04.04
And no windows appears to the screen (I've already install Wubi on an other pc so I'm a litlle bit familliar with)
Thanks for your help
:)

Hmm that's the first time I hear that. Which makes it that much more relevant :D
You may try to run "wubi --debug", but I'd have to set up more debug statements. You might need to recompile locally to spot the issue (which in turns requires you installing nsis version 2.29). In case I'll explain what to do.

PS if you are an advanced user, consider trying the new alpha version, we need some help testing. At the moment installation size 0 and 1 should work, but loopinstallations (size > 1) will not. 

[http://wubi-installer.org/devel/minefields/](http://wubi-installer.org/devel/minefields/)

---

### Post by lorent_tt on 2007-09-27
Incredible !
It's going on now !!!
What I've done = not a lot in fact, I've just installed SPYBOT...
The Pc is brand new and "virgin" so no spyware possible ;-)
certainly a issue of security somewhere

Anyway, many many thanks for your support and your energy to work on WUBI &/or Ubuntu and to help me

:KS

---

### Post by ago on 2007-09-27
hmm, well if you can pinpoint the issue it may help others are as well

---

