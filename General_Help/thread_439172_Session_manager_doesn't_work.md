---
title: "Session manager doesn't work"
date: 2007-05-10
forum: General Help
---

### Post by Marcos.Rufino on 2007-05-10
Well, after some weeks with Feisty Fawn, I'm sad to see that many important things just don't work, at least in my box. Many of the problems I have are related to the Gnome configuration modules. 

For example, in the Session manager (>System>Preferences>Session) I can't add apps to be automatically started when I turn on the machine. Nor remove the applications already listed. [Actually, the Session app let me include or remove but when I restart the system everything comes back to the original state. And yes, I'd already tried to save the session.]

The Language support application, in turn, let me change the default language of the system, but when I restart the machine, guess what... everything is exactly as before.

Am I the only one who is having these annoying problems with Feisty Fawn? My Synaptic is with all the repositories activated and I'm waiting everyday for an update that could solve all these snags. 

Thanks

---

### Post by useResa on 2007-05-10
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/112735](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/112735) [br].[/br] ---------------------------- [br].[/br] [br].[/br] 				I noticed that it was indicated as a bug one time before.
Maybe you could attach your information to this bug as well.

---

### Post by Marcos.Rufino on 2007-05-10
Thanks useResa, I will do it right now.

---

### Post by HavocRise on 2007-05-13
same issue here.  anyone got an answer for this?  it works correctly for a different user...

---

### Post by HavocRise on 2007-05-17
I fixed it!  Check the permissions on your ~/.config/autostart/ folder.  Mine was set to root as the owner and my account only had read access.  That is why it wouldn't save any changes.  Hope this helps!

---

### Post by Marcos.Rufino on 2007-05-17
Congratulations, HavocRise!!

You've found the solution for this annoying problem.

---

### Post by useResa on 2007-05-18
> **HavocRise said:**
> I fixed it!  Check the permissions on your ~/.config/autostart/ folder.  Mine was set to root as the owner and my account only had read access.  That is why it wouldn't save any changes.  Hope this helps!Have you also posted your findings and solution in the bug report?
This could be helpful and useful when this report is being handled.

TIA

---

