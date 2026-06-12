---
title: "Remove programs completely ..."
date: 2005-10-07
forum: General Help
---

### Post by dbee on 2005-10-07
Hi,

I am trying to unistall apache - but when I go for a complete removal in synaptic I still end up with lots of files on my system ... /usr/share/apache/  - /usr/sbin/apache - /lib/var/apache etc ...

How do I do a complete uninstall of a program, so that I don't get the same broken settings appearing across reinstallations

thanks

---

### Post by duminas on 2005-10-07
About the only thing I can think of is run a **locate apache** and remove whatever you find that is not desired.

Maybe there is something more automatic for this?
I am not sure.

---

### Post by dbee on 2005-10-07
thanks duminas,

That's what I ended up doing in the end, I guess it's not the best solution though, or the safest. 

I know that gentoo has something like ' ebuild --deep-clean ' for this situation.

I guess it's kinda strange that the synaptic command 'remove completely' still leaves a large number of library, binaries and shared files on the system.

Maybe something will turn up on this yet though ... <fingers crossed>

cheers

---

