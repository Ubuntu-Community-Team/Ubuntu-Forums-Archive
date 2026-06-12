---
title: "What does 2&gt;&amp;- do in bash?"
date: 2014-01-26
forum: General Help
---

### Post by elundmark on 2014-01-26
I'm using this command to get the contents of the clipboard:
```
$ xclip -silent -selection c -o 2>&-
```
I've added **2>&-** (which I picked up from somewhere) to surpress an [error]("https://groups.google.com/forum/#!topic/vim_dev/xB54U0EapfE") that shown up sometimes, but I've forgotten precisely what it does, besides redirecting the output.
Does it lauch the process asynchronously? What else does it do?

---

### Post by mcduck on 2014-01-26
It doesn't do anything else than suppress the STDERR output from whatever program you run.

---

### Post by elundmark on 2014-01-26
> **mcduck said:**
> It doesn't do anything else than suppress the STDERR output from whatever program you run.

Ahh... thanks!
So, what then is the difference bewteen **2>&-** and **2>&**   ?

---

### Post by steeldriver on 2014-01-26
```
2>&-
```
*closes* the output stream whose file descriptor is 2

I don't think 2>& (without the final dash) is syntactically legal, it doesn't mean anything afaik

---

### Post by elundmark on 2014-01-26
Many thanks, glad I got that sorted out :)

---

