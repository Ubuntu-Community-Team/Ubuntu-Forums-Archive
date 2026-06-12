---
title: "samba users...."
date: 2008-05-23
forum: General Help
---

### Post by fouadk on 2008-05-23
hi everyone....

how many samba users can be created on a single machine ???

---

### Post by kidders on 2008-05-24
Hi there,

Afaik, the maximum number of unique users is something in the region of four billion (a limitation of the Linux platform). In theory, I suppose, you could create multiples of that number of Samba users, by mapping more than one to any given Linux UID.

I don't know about Windows systems though ... Perhaps if you involve MS-based domain controllers in administering your network, you might hit a lower ceiling. What ballpark is your anticipated number of accounts in?

---

### Post by fouadk on 2008-05-24
thank you for your reply....

what i am tryin to do is that i have a windows active directory with around 3000 users....i want to put the files of those users on a linux server to avoid viruses killing my files server(we always face that problem with windows 2003 file server even with anti-virus software)and i will be using folder redirection on active directory to point to those files on the linux server  and then using a virus scanner clean those files....i dunno if this is the right way to do it but i will be creating samba users and give each samba user pemission to its folder...

what do you think ??? doable ??? right way to do it ???? any better more professional way ???

please help...

thanks in advance :D

---

