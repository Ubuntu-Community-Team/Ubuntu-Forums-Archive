---
title: "Translation"
date: 2017-03-18
forum: General Help
---

### Post by gammayt on 2017-03-18
"C:\Program Files (x86)\Steam\bin\SteamService.exe" /repair 

Can  anyone translate this to Ubuntu/Linux?
Like I need to find out how to get to my Ubuntu's "Program Files" and my steam folder.  Thanks

---

### Post by grahammechanical on 2017-03-18
Please edit your post so that the text is black text and not a difficult to read pale grey or a dirty white.

---

### Post by gammayt on 2017-03-18
Done, sorry.

---

### Post by howefield on 2017-03-19
> **gammayt said:**
> "C:\Program Files (x86)\Steam\bin\SteamService.exe" /repair 

Can  anyone translate this to Ubuntu/Linux?
Like I need to find out how to get to my Ubuntu's "Program Files" and my steam folder.  Thanks

Generally, applications aren't installed into a single location, multiple locations might be used depending on the purpose of the file. Executables would usually be installed to /usr/bin/ but probably not a good idea to mess around in there unless you have an idea of what you want to do.

You could use something like ..

```
dpkg -L packagename
```

to find the installed paths to a particular package.

---

