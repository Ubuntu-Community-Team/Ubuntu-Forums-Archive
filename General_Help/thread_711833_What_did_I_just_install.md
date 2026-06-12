---
title: "What did I just install?"
date: 2008-03-01
forum: General Help
---

### Post by baltho on 2008-03-01
Hello all,

I've just written this little one-liner - debian really, but I'm a die-hard ubuntu fan, so I've posted it here - to cope with a common problem I have. 

I quite often want to install something, say an imap server, so I fire up synaptic, search for imap, and have (gnu/linux being the wonderful beast it is) several packages to choose from. Naturally, I want to try them all!

You scroll down, do a bit of googling, pick a few packages, and install them. Wait. Synaptic says "all's well" and shows an empty list. Fair enough.

My problem is, I can never remember exactly which ones I've just installed - sometimes I'll jot them down in tomboy, but what a pain!

So if you run this command:
[FONT="Courier New"]grep "^Setting up" /var/log/apt/term.log | tail -20[/FONT]
you see the last 20 packages synaptic installed! Just what the doctor ordered: I can now type the command names into  a terminal, or do a
[FONT="Courier New"]dpkg -L <package_name>[/FONT]
by double-clicking on the package name and middle-clicking to paste it (I love that command line, I tell ya!) to see what files have been installed, and my life is now complete!

Hope someone finds this useful...

---

### Post by baltho on 2008-03-01
Sorry folks: just realised, you'll need to put a :sudo" in front of that, probably. :)

---

### Post by zvacet on 2008-03-01
**synaptic>file tab>history**

---

### Post by gfg on 2008-03-01
> **zvacet said:**
> **synaptic>file tab>history**

I did not know this. Thank you that is a nice feature!

---

