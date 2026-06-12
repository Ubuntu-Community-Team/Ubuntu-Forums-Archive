---
title: "Empathy Disabled on every Boot"
date: 2016-08-10
forum: General Help
---

### Post by Jason_Hunter on 2016-08-10
Every time I boot, I have to open Empathy and "enable" the jabber account. 

Isn't this supposed to be automatic?

Why is it "disabled"?

I'm using gnome-shell on 16.04

---

### Post by fonji on 2016-10-14
Hello!

I have the same problem, did you find a way to correct it?

---

### Post by Jason_Hunter on 2016-10-14
> **fonji said:**
> Hello!

I have the same problem, did you find a way to correct it?

Nope;stillthesame

---

### Post by deadflowr on 2017-05-24
If you want it to start at login, then set a startup applications entry for it.
Open Startup Applications and click Add.
Give it a name (any name will do).
and add the command: empathy
to the command entry line
comment is optional.
click Add to save.
Then it'll launch at startup

If you think the preference setting: Automatically connect on startup has anything to do with launching at login, that is incorrect.
It only has to do with how empathy will run when you do open it.
And nothing to do with starting at login.
It a common mistake that causes confusion.

Hope it helps

---

