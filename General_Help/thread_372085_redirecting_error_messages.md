---
title: "redirecting error messages"
date: 2007-02-27
forum: General Help
---

### Post by nickoli_02 on 2007-02-27
I'm compiling a project for one of my university courses and I'd like to redirect the error message output to a file. Thing is, it's not working :P

```
g++ file.cpp > errors.txt
g++ file.cpp >> errors.txt
```

What's wrong with these lines? :confused:

---

### Post by jpeddicord on 2007-02-27
That definitely should be working. Is it creating the output files at all?

---

### Post by highneko on 2007-02-27
This may be helpful:
[http://wooledge.org/mywiki/BashFaq#faq55](http://wooledge.org/mywiki/BashFaq#faq55)

---

### Post by nickoli_02 on 2007-02-27
ohhhh I see, lol. &> redirects standard error. Thanks :)

---

