---
title: "ftp using the terminal"
date: 2008-06-10
forum: General Help
---

### Post by enchance on 2008-06-10
I recently used the terminal to ftp and it was great. I have some questions tho:
      1. Can I put/get files without pressing 'y' for yes everytime?
      2. Can I put in a whole folder overwriting the existing folder on my server?

Thanks y'all.

---

### Post by andrew.46 on 2008-06-10
Hi,

I admire your fortitude in using such a minimalist client :-). Have a look at ncftp which still runs from CLI but is a little more user-friendly. I note from the man pages that your second point is met:

> The put command lets you send entire directory trees,  too.   It
should  work  on  all  remote systems, so you can try ``put -R''
with a directory to upload the directory and its contents.

I believe point 1 is met with ncftp as well.

         Andrew

---

### Post by mixmaster on 2008-06-10
> **enchance said:**
> I recently used the terminal to ftp and it was great. I have some questions tho:
      1. Can I put/get files without pressing 'y' for yes everytime?
      2. Can I put in a whole folder overwriting the existing folder on my server?

Thanks y'all.
1. Typing prompt while ftp is active toggles interactive mode (ie turns the "Y" on and off).  Starting ftp with the -i option starts it with prompts turned off.
2. The basic client will not put (or get) a directory.  However, if you switch to the directory and do mput/mget * it has much the same effect.  What you can't easily do is a recursive mput/mget (ie put/get a whole directory tree in one operation).

It is worth getting to know these basic utilities as they are the ones which will generally be on any flavour of linux no matter how old.

---

### Post by Kinnza on 2008-06-10
1) yes you can. 
use the command:
```
prompt
```
and then run your mput command

2) to the second question, you can use mput with * to move all your files from your local machine to the remote one

---

### Post by Kinnza on 2008-06-10
damn mixmaster you got here before i did :P

---

### Post by mixmaster on 2008-06-10
> **Kinnza said:**
> damn mixmaster you got here before i did :P
Rofl

---

