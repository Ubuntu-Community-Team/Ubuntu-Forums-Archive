---
title: "Over 3G RAM on 32bit?  Apparently... YES! You Can.  Or Not?"
date: 2007-09-21
forum: General Help
---

### Post by jsgarvin on 2007-09-21
I've seen many threads here and on other linux forums wherein one or more people adamantly declare that 32bit operating systems can *not* and never will be able to access more that 3GB of RAM.  I've even seen some that carefully try to explain the math behind the WHY of it all.

Then, today... [this article](http://www.linux.com/feature/119287) shows up on Linux.com, and I start having my doubts.  According to the article, a properly compiled 32bit kernel can support up to 64GB of RAM!?!?

The article also claims that 32bit Ubuntu has supported up to 4GB of RAM out of the box since 6.10... but I know I've seen threads here with plenty of people saying they have 7.04 and 4GB of RAM but Ubuntu only sees 3GB of it.

So... WTF?  I'm clearly confused and missing something fundamental in all this.  The author of the Linux.com article doesn't say anything about it only applying to people running 32bit linux on 64bit processors, and I find it hard to believe that he would overlook that kind of "minor" detail.   Will someone please enlighten me.

---

### Post by PmDematagoda on 2007-09-21
> **jsgarvin said:**
> I've seen many threads here and on other linux forums wherein one or more people adamantly declare that 32bit operating systems can *not* and never will be able to access more that 3GB of RAM.  I've even seen some that carefully try to explain the math behind the WHY of it all.

Then, today... [this article](http://www.linux.com/feature/119287) shows up on Linux.com, and I start having my doubts.  According to the article, a properly compiled 32bit kernel can support up to 64GB of RAM!?!?

The article also claims that 32bit Ubuntu has supported up to 4GB of RAM out of the box since 6.10... but I know I've seen threads here with plenty of people saying they have 7.04 and 4GB of RAM but Ubuntu only sees 3GB of it.

So... WTF?  I'm clearly confused and missing something fundamental in all this.  The author of the Linux.com article doesn't say anything about it only applying to people running 32bit linux on 64bit processors, and I find it hard to believe that he would overlook that kind of "minor" detail.   Will someone please enlighten me.

Yes, it is true you can compile the 32 bit Linux kernel in such a way that it acts like a 64 bit kernel and can support a lot more RAM than is usually possible, but very usually not more than a 64 bit kernel.

But out-of-the-box support by a 32 bit kernel for 4Gb RAM is unheard of. I have seen people complaining that their 32 bit Feisty kernel will not recognise more than 3.2 GB of RAM, so I think that may be a false statement.



P.S. Not wanting to offend you, but you should ask a question like this in the Community Cafe, not in the General Help section.

---

### Post by jsgarvin on 2007-09-21
> **PmDematagoda said:**
> P.S. Not wanting to offend you, but you should ask a question like this in the Community Cafe, not in the General Help section.

Duly noted.  Thanks.

---

### Post by PmDematagoda on 2007-09-21
> **jsgarvin said:**
> Duly noted.  Thanks.

Glad to help, I hope you found my answer sufficient enough to solve any problems you may have concerning this issue.:)

---

### Post by psusi on 2007-09-21
The kernel can be compiled with support for Paging Address Extensions, which allows for support of up to 64 GB of physical ram, however, any one process may still only access 3 gb of ram at a time.

---

### Post by bodhi.zazen on 2007-09-21
It is my understanding the the server kernel has been optimized to support such high ram.

Now if someone would be so kind as to send me a box with 64 Gb ram I would be more then happy to test ...

---

### Post by dcstar on 2007-09-21
> **psusi said:**
> The kernel can be compiled with support for Paging Address Extensions, which allows for support of up to 64 GB of physical ram, however, any one process may still only access 3 gb of ram at a time.

And this applies to other 32 bit O/S, like Windows 2003 Server which can use 4GB with the /PAE boot parameter (even though it will only use up to 3GB without it).

Beware of blanket statements that can serve to confuse rather than simplify......   :(

---

