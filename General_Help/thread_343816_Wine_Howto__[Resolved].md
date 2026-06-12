---
title: "Wine Howto ? [Resolved]"
date: 2007-01-22
forum: General Help
---

### Post by will61 on 2007-01-22
I'm a new user 
And I would like to install Wine however I can't seem to fine a Howto I've searched this forum  and the closest thing a can find is a Howto for Breezy or Dapper

I've tried the Guide on the winhq website but when I try to add the repositories in synaptic and hit reload I get errors and the packages won't download (the error states that there is no public key) and after searching on the winehq website I can't seem to find these public keys

does anybody know of a decent howto for edgy ? one where the packages actually download without any drama's ?

Thanks in advance Will

---

### Post by aysiu on 2007-01-22
[http://www.psychocats.net/ubuntu/wine](http://www.psychocats.net/ubuntu/wine) should help

---

### Post by will61 on 2007-01-22
Still no luck I keep getting this error

W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: You may want to run apt-get update to correct these problems

Then when I run "apt-get update" and rerun the install I continue to get the same error

I've also tried running "dpkg --configure -a" without any luck either 

Whats with the public key issue are there any alternative sources for the wine package the one I'm using seems not to want to work at all

---

### Post by will61 on 2007-01-22
Thanks for the help I've worked it all out wine is up and running now :D

---

### Post by mistypotato on 2007-01-24
That's great Will, you got "your" problem resolved.  How about posting what "you" discovered and taking the time to post it so that it might "help" someone else that comes along looking for help on this same topic?

Wouldn't that be great also?

---

### Post by penquin on 2007-01-24
does anyone know how to get wine to recognize a cd drive?  I am trying to use exact audio copy and it doesn't see the cd in my drive.  Also when I try to use my daughters programs the cds are not recognized after installation.

---

### Post by YokoZar on 2007-01-25
Here, follow the instructions here: [http://winehq.org/site/download-deb](http://winehq.org/site/download-deb)

The instructions were updated recently, due to the addition of the key to the database (hence the warning you're getting).  It's a single command to add it though (see the link)

---

