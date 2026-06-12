---
title: "Problem compiling XChat"
date: 2008-05-24
forum: General Help
---

### Post by Phobosz on 2008-05-24
[http://www.picvalley.net/v.php?p=u/221/55209_353.PNG](http://www.picvalley.net/v.php?p=u/221/55209_353.PNG)

This is the error, so i guess it's because i don't have the required lib but i can't find it in synaptic so can anyone help me ?

---

### Post by macaholic on 2008-05-24
Firs off a tip, when posting an error, either use the 'code' entry option (# sign) or use a site like pastebin.com. The library you are looking for is probably libglib2.0, when compiling source code, you generally need the -dev version of the file as well.

---

### Post by pointone on 2008-05-24
```
sudo apt-get build-dep xchat
```

---

