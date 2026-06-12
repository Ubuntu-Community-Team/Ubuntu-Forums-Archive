---
title: "unison - exclusion of cache paths"
date: 2007-11-24
forum: General Help
---

### Post by KhaaL on 2007-11-24
I'm trying to figure out a way to exclude cache folders from my backup list, but I have no idea how to do this without adding them to the default.prf file manually. I've tried with these entries:

ignore = Path {*Cache*}
ignore = Path {*cache*}

but they dosen't help. Any ideas on how I can do this?

---

### Post by penman242 on 2007-11-30
I'm assuming you have another .prf file that contains your roots.  I'm not sure if information in default.prf automatically gets called when you run your particular prf file.  My suggestion is to create a common.prf that contains your line:

ignore = Path {*cache*}

then add

include common

to the begining of your specific .prf file(s).

Hope that helps!

---

