---
title: "Can't sudo?"
date: 2006-07-09
forum: General Help
---

### Post by Cloudy on 2006-07-09
[I've been having some problems]("http://www.ubuntuforums.org/showthread.php?t=209219") but a clean install fixed them, for the most part; however, I can't sudo.

I open a terminal and type "sudo nano /etc/hosts" and it says "sudo: unable to lookup ubuntu via gethostbyname()". I'm not sure what to do.. :confused:

---

### Post by Cloudy on 2006-07-09
Found a solution. I really ought to search the forums before I make topics. >.<

---

### Post by RJARRRPCGP on 2006-07-10
This is a bug. If you leave the host name at "ubuntu", this occurs. 
I can't recall having this problem with Hoary. 

It looks like a new bug that was introduced in Breezy Badger. :(

When this problem occurs, you're forced to reinstall. :mad:

---

### Post by Cloudy on 2006-07-11
> **RJARRRPCGP said:**
> This is a bug. If you leave the host name at "ubuntu", this occurs. 
I can't recall having this problem with Hoary. 

It looks like a new bug that was introduced in Breezy Badger. :(

When this problem occurs, you're forced to reinstall. :mad:

[Not necessarily so, good sir.]("http://www.ubuntuforums.org/showthread.php?t=210451&highlight=sudo%3A+unable+lookup+ubuntu+gethostbyname%28%29")

:D 
2nd post. Worked for me; that's what I was talking about when I said I found a solution. ;)

---

