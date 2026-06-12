---
title: "Do I need to run apt clean, apt autoclean, apt autoremove after an automatic upgrade?"
date: 2020-04-09
forum: General Help
---

### Post by Butthead on 2020-04-09
Hi,

Just wondering about something out loud here.  I got a factory built computer (Zareason) that does automatic upgrades on boot up.  Is it necessary to run "apt clean," "apt autoclean," & "apt autoremove" like I did in the old days when I upgraded through the Terminal?:confused:

Thanks for any info! :guitar:

---

### Post by TheFu on 2020-04-09
Depends on how much free storage there is in /var/.  if /var/ only has 1G free, yes.  if /var has 200G free, probably not.
i don't run clean, just autoclean and only about once a month.

The problem comes up when we use apt-get in our scripts, because we have been warned against using apt. The apt options aren't stable, they say.  The manpages are pretty clear about the differences between apt, apt-get, and aptitude for the different options. Best to read those.

---

### Post by DuckHook on 2020-04-09
> **TheFu said:**
> …The apt options aren't stable, they say…
:shock:
I've been using plain apt for years now. On dozens of machines if I include the virtual sort. Never a problem. Have I just been lucky?

---

### Post by TheFu on 2020-04-09
> **DuckHook said:**
> :shock:
I've been using plain apt for years now. On dozens of machines if I include the virtual sort. Never a problem. Have I just been lucky?

in scripts?   The warning around using apt is for scripting.

---

### Post by DuckHook on 2020-04-09
> **TheFu said:**
> in scripts?   The warning around using apt is for scripting.
Got it. I don't use apt in scripts, so I wouldn't know. I don't like running really important stuff automatically. Not that I could really do anything if an update blew up in my face in real time either, but just the thought of automating something like that&#8230;

---

### Post by Tadaen_Sylvermane on 2020-04-10
Ive thus far had no problems with it in a script. However I also watch it like a hawk and don't run it automatically. Script just does it for me. One command instead of 4.

---

### Post by DuckHook on 2020-04-10
> **Tadaen_Sylvermane said:**
> …One command instead of 4.
I just string it together in one line and run it after finding its previous invocation with <Ctrl> + <r> "clean":```
sudo apt update && sudo apt full-upgrade && sudo apt autoremove --purge && sudo apt clean
```…thus avoiding both scripts and retyping.

---

### Post by Butthead on 2020-04-10
> **TheFu said:**
> Depends on how much free storage there is in /var/.  if /var/ only has 1G free, yes.  if /var has 200G free, probably not.
i don't run clean, just autoclean and only about once a month.

Okay, thanks!  That makes sense. :guitar:

---

