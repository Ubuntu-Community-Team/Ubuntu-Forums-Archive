---
title: "Uninstalling Postfix to Reinstall It"
date: 2005-09-07
forum: General Help
---

### Post by megamartianca on 2005-09-07
I'm trying to migrate a Slackware machine over to Ubuntu for easier update and system management, but one big hangup is Postfix.  I use the box in question as a mail gateway (to weed out spam, viruses, various mail attacks, etc) and then hand on what remains to my mail server.  To do this I use the experiment version of Postfix which supports Anvil.

Looking at the installed Postfix, it does not, and I was wondering how one uninstalled Postfix so one could compile and install the more experimental strain.

---

### Post by KingBahamut on 2005-09-07
sudo apt-get remove postfix

---

### Post by megamartianca on 2005-09-07
[QUOTE=KingBahamut]sudo apt-get remove postfix[/QUOTE]

Well, what I'm really looking for, I suppose, is a way of downloading the Debian experimental version of Postfix.  Is that something I can do via apt-get and the Debian experimental repository?

And just what is the Debian experimental repository?

---

