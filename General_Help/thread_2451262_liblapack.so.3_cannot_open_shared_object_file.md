---
title: "liblapack.so.3 cannot open shared object file"
date: 2020-09-30
forum: General Help
---

### Post by ofc91 on 2020-09-30
hi everyone,

I started to learn dakota optimization tool in ubuntu. I am thinking &#305; &#305;nstalled dakota correctly, but when &#305; write "dakota -v", I get  "dakota: error while loading shared libraries: **liblapack.so.3:** cannot open shared object file: No such file or directory" message. 

Can anyone give me a solution please?

thank you

---

### Post by ActionParsnip on 2020-09-30
What is the output of:
```

sudo updatedb; locate liblapack.so*; lsb_release -a; uname -a

```
Thanks

---

### Post by ActionParsnip on 2020-09-30
[https://packages.ubuntu.com/search?searchon=contents&keywords=liblapack.so&mode=exactfilename&suite=focal&arch=any](https://packages.ubuntu.com/search?searchon=contents&keywords=liblapack.so&mode=exactfilename&suite=focal&arch=any)

---

