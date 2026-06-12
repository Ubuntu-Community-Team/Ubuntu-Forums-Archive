---
title: "Apache Virtual Hosts on Ubuntu 20.04"
date: 2021-03-01
forum: General Help
---

### Post by mnduck on 2021-03-01
I'm trying to set up two virtual hosts on apache2.

I have been successful with one of them but even though the second (imaginatively named first.co.uk and second.co.uk) appears to be the same as the first with exception of the name all I get is file not found.

There is another issue, I can connect to first.co.uk via localhost or it's lan IP address not by name which is is not right. I can not even use localhost/first.co.uk without getting an address not found error.

Both have files in sites available and sites enabled and apparently simlinks to the appropriate files.


Even after plodding through a number of tutorials I can see nothing wrong, other than it not working, I must be missing something and I would appreciate your help.

Many Thanks        MND

---

### Post by dragonfly41 on 2021-03-01
From memory since last setting up virtual hosts

/etc/hosts file configured to allow 
localhost
first.co.uk 
second.co.uk  ??

---

### Post by mnduck on 2021-03-01
Sorted I had to edit the hosts file and clear my browser data.

---

