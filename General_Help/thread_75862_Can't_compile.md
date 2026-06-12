---
title: "Can't compile"
date: 2005-10-14
forum: General Help
---

### Post by fergus.b on 2005-10-14
I'm trying to compile apache and I get this error after I do a ./configure command:

checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

I've installed gcc and make. I've attached the config.log file. 

Not sure what to try next.

---

### Post by el toro on 2005-10-14
you might want to install build-essential if you haven't already.

---

### Post by fergus.b on 2005-10-14
Lovely, thank you! Thats it. :KS 

```
apt-get install build-essential
```

---

### Post by meastp on 2005-10-14
Hi!

I get the same error when trying to install cedega from cvs, but my build-essential is already the newest version.



Configuring ...




--------- Error log - file /home/meastp/.WineCVS/sources/cvscedega/ErrorLog : ---------
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking whether make sets $(MAKE)... yes
checking for gcc... gcc-3.4
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.


Error in Configure

Try fixing the error based on the output above, and
run the script again, without paramaters (Eg: WineCVS.sh)

---

### Post by nogladog on 2007-05-30
> **meastp said:**
> Hi!

I get the same error when trying to install cedega from cvs, but my build-essential is already the newest version.



I'm having the same problems, but I don't know where to find my config.log...  I'll post whenever it's fixed...

---

