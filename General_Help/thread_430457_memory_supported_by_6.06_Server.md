---
title: "memory supported by 6.06 Server"
date: 2007-05-02
forum: General Help
---

### Post by halfmanhalfpint on 2007-05-02
How much memory is supported by 6.06 server?

Michael

---

### Post by halfmanhalfpint on 2007-05-02
What is the maximum amount of memory supported by 6.06 Server?

Michael

---

### Post by madmetal on 2007-05-02
> **halfmanhalfpint said:**
> What is the maximum amount of memory supported by 6.06 Server?

Michael

if i remember correct the 6.06 32bit has a 1gb ram limitation due to kernel ram limitation..
newer 32bit versions have some problems working with 4gb of ram also..
but 64bit versions dont have ram limitations and at 32bit editions you can compile your own kernel to manage more RAM.. 

so for 6.06 you either have to install 64bit version or compile kernel to make use of more than 1gb ram..

---

### Post by madmetal on 2007-05-02
more infos about 32bit linux kernel ram limitations and management..
[http://kerneltrap.org/node/2450](http://kerneltrap.org/node/2450)

---

### Post by mcduck on 2007-05-02
> **madmetal said:**
> if i remember correct the 6.06 32bit has a 1gb ram limitation due to kernel ram limitation..
newer 32bit versions have some problems working with 4gb of ram also..
but 64bit versions dont have ram limitations and at 32bit editions you can compile your own kernel to manage more RAM.. 

so for 6.06 you either have to install 64bit version or compile kernel to make use of more than 1gb ram..

The 386-kernel (default on desktop) in 6.06 and older Ubuntu versions does have the 1GB maximum of RAM, but installing 686 or k7 kernel from repositories fixed that.

6.10 and 7.04 use 'generic' kernel by default, and that one has 4GB maximum. 64-bit version of course has way higher limits.

I'm not absolutely sure about the server kernel in different versions. But anyway, there is no need to compile your own kernel to get more than 1GB of RAM working :)

---

### Post by bapoumba on 2007-05-02
@ halfmanhalfpint: merged your duplicate thread in here.

---

