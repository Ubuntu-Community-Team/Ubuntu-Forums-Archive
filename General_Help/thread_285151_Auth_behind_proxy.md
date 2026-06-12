---
title: "Auth behind proxy"
date: 2006-10-26
forum: General Help
---

### Post by qalimas on 2006-10-26
Hello, I work part-time as a tech for a School Board (K-12).  My personal workstation is running Ubuntu (I can't stand Windows, I fix enough of those comptuers as it is...).

However, the school board has a proxy, which requires a username and password. (username: [email]blah@domain.org[/email]).  I can't connect to the reps with Synaptic, because Synatpic doesn't have an option to put in a username and password.  I tried using apt through CLI, but in configuration, I think just the first part of the username is put in, because the name itself has @domain.org.

I'm unsure how I'd go about connecting through Synaptic, I know all file types ARE allwoed through, as I can get what I need (or the smaller things, anyway) from packages.ubuntu.com.

Any help is appreciated, thanks! :D

---

### Post by PriceChild on 2006-10-26
Have you tried entering it into System>preferences>network proxy

---

### Post by qalimas on 2006-10-26
Yes, I have, and it has no effect :(

---

### Post by xavierh on 2006-10-26
> **qalimas said:**
> Hello, I work part-time as a tech for a School Board (K-12).  My personal workstation is running Ubuntu (I can't stand Windows, I fix enough of those comptuers as it is...).

However, the school board has a proxy, which requires a username and password. (username: [email]blah@domain.org[/email]).  I can't connect to the reps with Synaptic, because Synatpic doesn't have an option to put in a username and password.  I tried using apt through CLI, but in configuration, I think just the first part of the username is put in, because the name itself has @domain.org.

I'm unsure how I'd go about connecting through Synaptic, I know all file types ARE allwoed through, as I can get what I need (or the smaller things, anyway) from packages.ubuntu.com.

Any help is appreciated, thanks! :D

Check ON THE GETAUTOMATIX.COM. they explain how to get to the repositories if you are behing a firewall.. You net to make some changes to some files but I do not remember which ones.

---

### Post by qalimas on 2006-10-26
While before, that fix did work, since they put in the authentication through MS ISA Server, it won't anymore.

Username is [email]user@cpsb.org[/email]
Password is password

Not real, but user and password are replaced, the @cpsb.org is part of the username, and I think when typign the full proxy, it gets confused on what the username is (username@cpsb.org:password@cpsb.org).

(Edited: disabling smilies)

---

