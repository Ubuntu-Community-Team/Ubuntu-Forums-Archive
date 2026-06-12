---
title: "How are CFLAGs appended to configure?"
date: 2013-06-08
forum: General Help
---

### Post by sselt on 2013-06-08
In a typical configure make source, how can CFLAGS be added or appended to the configure line
**without** overriding any built in to the source scripts?

Will an export do this?

```
export CFLAGS="-custom flags"
./configure
```

---

### Post by sum1nil on 2013-06-08
CFLAGS are set as environmental values for the compiler. They are set when you login and your .bashrc is read. 
So add something like this to your ~/.bashrc after the initial comments:

**#GCC Flags**
[I]CFLAGS="-O2 -pipe"
export CFLAGS
CXXFLAGS="${CFLAGS}"
export CXXFLAGS[/I]

You can change them to whatever works or helps you.
Hope this helps.

---

