---
title: "Duel Core Xeon"
date: 2006-10-16
forum: General Help
---

### Post by Garf on 2006-10-16
Hi... 
The place I work for is getting a new server and we want to put Ubuntu 6.06 server on it...

The question is what kernal do we use?

I have been looking through these forums and found that people think the following kernel is the one to use:

**linux-amd64-xeon**

Basically I have 3 questions.
[LIST=1]
[*]Why can't I find it when I do apt-cache search linux-amd64-xeon. And I have done sudo apt-get update - Edit. I think because we don't yet have a 64-bit installation of Ubuntu it's not showing these options when we do the search? Also does this mean that for the xeon we have to install the AMD64 version of Ubuntu?
[*]Why would an AMD kernel be the right one for an intel chip?
[*]Is the smp version the right one to go with for this CPU?
[/LIST]

Thanks in advance.

-Gareth.

---

### Post by Garf on 2006-10-17
No one???

---

### Post by Bytor on 2006-10-20
> **Garf said:**
> 
2. Why would an AMD kernel be the right one for an intel chip?


Because Intel's EM64T extensions to the x86 core of Pentium 4s and Xeons is virtually exactly the same as AMDs 64 bit stuff. Write code for the one set of 64 bit operations and you've also written it for the other.

Other than marketing speak, there isn't that much difference between EM64T and AMD64.

---

