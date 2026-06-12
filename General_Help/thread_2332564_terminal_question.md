---
title: "terminal question"
date: 2016-08-01
forum: General Help
---

### Post by jgw on 2016-08-01
when I open a terminal my prompt says: "greg@greg-System-Product-Name:~$".  There was a time when greg was good enough, then something else and, now, this.  At the same time, when I am in files, there is no problem in that my home directory is /home/greg/   I don't understand why everything isn't as presented with files or where that other stuff is coming from.

Thank you.................

---

### Post by Rocket2DMn on 2016-08-01
I'm not sure I understand what your question is.  This is a typical terminal prompt: *username*@*hostname*:*directory* where the starting directory is your home dir, represented as the ~ symbol.  You can always change your hostname.  You can also change what the terminal prompt looks like by editing your .bashrc file.

---

### Post by buzzingrobot on 2016-08-01
On the common one-machine scenario, displaying the hostname in the prompt may not look terribly useful.  Someone else, though, might open terminals on multiple hosts, and having the name in the prompt is very useful. (E.g., someone with a VPS account who's logged on to do some maintenance.)

Plenty of docs and howtos out there to explain how the prompt works and how to change it.

---

### Post by jgw on 2016-08-01
Thank your for the replies.

I edited both the hostname and hosts file and changed the name.  I think I have to restart so I won't know if it worked until tomorrow as it didn't work without a reboot.   The hosts file had the offending line <g>

Thanks again!!!!!!!!!!!!!!

It worked!

---

