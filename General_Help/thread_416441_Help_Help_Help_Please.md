---
title: "Help Help Help Please"
date: 2007-04-21
forum: General Help
---

### Post by ali780 on 2007-04-21
I have the following error How can I fix it?
Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

Thanks

---

### Post by heimo on 2007-04-21
> **ali780 said:**
> I have the following error How can I fix it?
Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.


First thing I'd try is:
```
sudo apt-get update
sudo apt-get install -f

```Does it give warnings?

---

### Post by ali780 on 2007-04-21
I tried them
But both of the stops on 99% and don't finish.

---

### Post by ali780 on 2007-04-21
How much time they need for finish? I mean they finish fast or need some times? more than 5 minutes?

---

### Post by DougieFresh4U on 2007-04-21
Maybe try** sudo dpkg --configure -a**

---

### Post by vishnumrao on 2007-04-21
I suggest try it sometime later. The servers are all swamped right now. Even my download crawls when I do a sudo apt-get update. Maybe try sometime later. 

PS: I noticed another thread with a similar problem started by you. Is the same problem you are referring to? If yes, it would be good to remove the other.Just a suggestion.

VMR

---

### Post by ali780 on 2007-04-21
Yes but I don\t know How can I remove them. 
there is just one solution for my problem? I mean there is no alternative solution?
Thanks

---

### Post by heimo on 2007-04-21
If you're using se.archive.ubuntu.com
```
grep archive /etc/apt/sources.list
```
I doubt it's about servers being down, as those swedish mirrors are _really_ good.

---

### Post by ali780 on 2007-04-21
I dosen\t work. So it remains just first 2 sudo command. i hope they can solve my problem

---

