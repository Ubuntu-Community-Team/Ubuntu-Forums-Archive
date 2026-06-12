---
title: "qpopper: subprocess post-removal script returned error exit status 1"
date: 2006-07-25
forum: General Help
---

### Post by evuraan on 2006-07-25
Hi Folks,

Greetings...!! 
[I]
(Posting after much stfw, and amply frustated ](*,) ) [/I]

I am trying to remove qpopper (ver: 4.0.5-4sarge1)  and **synaptic** says:

E: qpopper: subprocess post-removal script returned error exit status 1


**dpkg says:**

~# dpkg --purge --force-remove-reinstreq qpopper
(Reading database ... 186827 files and directories currently installed.)
Removing qpopper ...
dpkg: error processing qpopper (--purge):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 qpopper
[B]

apt-get remove qpopper says:[/B]

~# dpkg --purge --force-remove-reinstreq qpopper
(Reading database ... 186827 files and directories currently installed.)
Removing qpopper ...
dpkg: error processing qpopper (--purge):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 qpopper

Seems like the post-removal section of the uninstall is failing. Is there a way to skip the post-removal section? Any other inputs will be much appreciated. 

Many thanks in advance...!! 

--Ev

---

### Post by desperados on 2006-09-29
Hi,
i have the same problem with the latex209-bin package. Did you resolve the problem? Thank's a lot for a response.

Des

---

### Post by honeydew on 2007-08-22
I am having the same issues with a few ldap packages on amd64 dapper lts, I have tried the standard methods of fixing the system, but havnt come up with anything..

---

