---
title: "Package managers can't access repositories"
date: 2007-02-04
forum: General Help
---

### Post by Rancidmaniac13 on 2007-02-04
None of the package managers can access the repositories. This has only started to happen in the last few days. My internet conection is working fine, I can browse the web with no problems. Any help would be greatly appreciated. Here are the errors:

[http://archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/edgy/main/i18n/Translation-en_IE.bz2:](http://archive.ubuntu.com/ubuntu/dists/edgy/main/i18n/Translation-en_IE.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/i18n/Translation-en_IE.bz2:](http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/i18n/Translation-en_IE.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/edgy/main/i18n/Translation-en_IE.bz2:](http://archive.ubuntu.com/ubuntu/dists/edgy/main/i18n/Translation-en_IE.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/i18n/Translation-en_IE.bz2:](http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/i18n/Translation-en_IE.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/edgy/universe/i18n/Translation-en_IE.bz2:](http://archive.ubuntu.com/ubuntu/dists/edgy/universe/i18n/Translation-en_IE.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/edgy-updates/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/Release.gpg:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/i18n/Translation-en_IE.bz2:](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/i18n/Translation-en_IE.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/i18n/Translation-en_IE.bz2:](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/i18n/Translation-en_IE.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/i18n/Translation-en_IE.bz2:](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/i18n/Translation-en_IE.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://security.ubuntu.com/ubuntu/dists/edgy-security/Release.gpg:](http://security.ubuntu.com/ubuntu/dists/edgy-security/Release.gpg:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://security.ubuntu.com/ubuntu/dists/edgy-security/main/i18n/Translation-en_IE.bz2:](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/i18n/Translation-en_IE.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/i18n/Translation-en_IE.bz2:](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/i18n/Translation-en_IE.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/i18n/Translation-en_IE.bz2:](http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/i18n/Translation-en_IE.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg:](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/i18n/Translation-en_IE.bz2:](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/i18n/Translation-en_IE.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

---

### Post by MoLE on 2007-02-11
It appears that your package managers are trying to access a proxy on your machine listening on port 4001.  localhost (127.0.0.1) is always your own machine.

A quick google search on the error message reveals similar problems involving anonymous proxying software.  See [here]("http://ubuntuforums.org/showthread.php?t=349222") and [here.]("http://forums.debian.net/viewtopic.php?t=310&")

Have you recently installed this sort of software?

---

### Post by Tayeb on 2007-02-11
I have the same problem, neither synaptic, nor update manager is working?
I have Samba that is sort of stuck, should I delete it?

---

### Post by MoLE on 2007-02-11
Can you be a bit more specific with the error message for synaptic?  What you do you mean when you say that Samba is sort of stuck?

---

### Post by Rancidmaniac13 on 2007-02-15
Yeah, I had installed some new software. I got around the problem anyway. Thanks for the help.

---

### Post by caspersghosts on 2007-08-15
I have this same issue, as well.

What is the solution?

---

### Post by Rancidmaniac13 on 2007-08-16
I had installed anonproxy or something like that and it was messing up my connection. I just un-installed it.

---

