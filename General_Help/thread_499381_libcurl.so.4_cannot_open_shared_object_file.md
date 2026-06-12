---
title: "libcurl.so.4: cannot open shared object file"
date: 2007-07-12
forum: General Help
---

### Post by JumpmanXXIII on 2007-07-12
How can i install libcurl.so.4 library 

I need it for the linux sendspace wizard

I check my /usr/lib/  for libcurl.so.4 and it's not there

I tried sudo apt-get install libcurl4  - doesn't work

Although sudo apt-get install libcurl3  - I have the latest version

Thanks in Advance

[-o<

---

### Post by salah_tr on 2007-07-20
hi,

Trie this 
**sudo apt-get install curl**

---

### Post by rebegin on 2007-08-20
hey i'm trying to run the same app and the installed curl package doesn't seem to solve the problem :( any other idea?

---

### Post by pablobm on 2008-02-06
if someone use Ubuntu 7.04  and got error about "libcurl.so.4' try typing in console:

```

sudo ln -s /usr/lib/libcurl.so.3 /usr/lib/libcurl.so.4
```

---

### Post by dcloutman on 2008-06-27
I realize this is an old thread, but I ran into the same problem and found that answers that had already been posted various places on the Web were wrong.

I my case, I compiled curl from source, but I suspect that the problem is the same if you use apt-get. In my case, I used the default --prefix option, which is /usr/local. This means the executable gets placed in /usr/local/bin, and the libraries (*.so*) go into /usr/local/lib.

To fix this, you have to look at the error and understand what it is really saying.
 
[INDENT] [FONT="Fixedsys"]libcurl.so.4: cannot open shared object file[/FONT][/INDENT]

The assumption has been that this the curl binary saying, "I cannot find libcurl.so.4". But looking at /usr/local/lib/ I could see that all the permissions were correct, which is probably why the initial poster was pulling out his/her hair.

What the error code is *really* saying is **libcurl.so.4 **cannot find *some other unnamed shared object*, which is a completely different issue. Now, I would have never figured this out had I not just successfully compiled the same version of curl on an identical version of Ubuntu on nearly identical hardware a few days previously, and found that version working perfectly. So I was able to ask myself what I had done on that first machine that I hadn't done on the second that would cause it to work.

The answer is non-obvious, and probably undocumented. Your need openssl to get curl to work. Period. libcurl.so.4 is looking for a .so associated with openssl.

Not wanting to compile openssl from source, as well, I did the following:
[INDENT][FONT="Fixedsys"]atp-get install openssl
apt-get install openssl-doc[/FONT][/INDENT]

I believe the latter is optional, but apt recommended installing it with openssl, and since openssl can be hard to work with, I figured, what the hell. 

Anyhow, I installed openssl. curl now works. The error is gone.

Happy curling, everyone!

:guitar:

---

