---
title: "IP address in bash prompt"
date: 2006-12-10
forum: General Help
---

### Post by bleearg on 2006-12-10
Hi all,
I'm wondering if anyone knows of a way to get the machine's IP address to show up in the bash prompt?  I've been looking through the [Bash Prompt HOWTO]("http://tldp.org/HOWTO/Bash-Prompt-HOWTO/"), but there doesn't seem to be a built-in escape sequence for the IP.  I know it's possible to use the hostname by using \h, but I'd really like the IP, too.

Any ideas?

TIA,
evt

---

### Post by psycho78 on 2006-12-10
try ifconfig ... and if you only want the ip of one interface:
ifconfig devicename
Regards,
psycho78

---

### Post by psycho78 on 2006-12-10
sorry misunderstood... you ment the prompt... I remember there is a way,.... hmm have to look it up... :)

---

