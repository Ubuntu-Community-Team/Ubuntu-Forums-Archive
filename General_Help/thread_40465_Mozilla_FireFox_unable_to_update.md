---
title: "Mozilla FireFox unable to update?"
date: 2005-06-09
forum: General Help
---

### Post by XDevHald on 2005-06-09
I'm running the new kernel 2.6.10-5 which might be the issue as to why the update for mozilla firefox is not working. If you are having the same problem post it here so someone can relate to this issue and give me some input on why it's not updating it's self.

---

### Post by desdinova on 2005-06-09
[QUOTE=BB]I'm running the new kernel 2.6.10-5 which might be the issue as to why the update for mozilla firefox is not working. If you are having the same problem post it here so someone can relate to this issue and give me some input on why it's not updating it's self.[/QUOTE]
 Im using 2.6.10-5-k7 and I've just put the backported 1.0.4 on - so far it is much better - and the problem with FF crashing when loading the RealPlayer plugin has gone. Are you on about its own internal extension updates?

---

### Post by XDevHald on 2005-06-09
[QUOTE=desdinova]Im using 2.6.10-5-k7 and I've just put the backported 1.0.4 on - so far it is much better - and the problem with FF crashing when loading the RealPlayer plugin has gone. Are you on about its own internal extension updates?[/QUOTE]
 I am running 1.0.4 at the moment but I assume there is a new security update for it. I'm not entirely sure why it's being blocked but I am thinking it has to do with the kernel.

I'm going to remove the kernel and replace it with the recent version.

---

### Post by XDevHald on 2005-06-09
The following packages have unmet dependencies:
  mozilla-firefox-gnome-support: Depends: firefox-gnome-support but it is not installed

If anyone else gets an error like this, just type **apt-get install -f** and it'll apply the upgrade for you :)

(Issue Resolved)

---

### Post by NeoChaosX on 2005-06-09
Actually, you're supposed to do **sudo apt-get dist-upgrade**. But it works either way.

---

