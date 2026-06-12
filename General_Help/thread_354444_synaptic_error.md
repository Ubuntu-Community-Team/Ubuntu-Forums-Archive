---
title: "synaptic error"
date: 2007-02-06
forum: General Help
---

### Post by STREETURCHINE on 2007-02-06
E: graphviz-cairo: subprocess post-removal script returned error exit status 127

i get this in synaptic when i am trying to uninstall graphviz-cairo,

it also shows up as an error when i update in terminal,

and it seems it is causing me to get apt-based errors in automatix.

any idea how to get rid of this program...

---

### Post by taurus on 2007-02-06
What happens if you run these from a terminal?

```
sudo aptitude remove graphviz-cairo
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by STREETURCHINE on 2007-02-06
thanks taurus, but i used ..

     ```
sudo rm -f /var/lib/dpkg/info/graphviz-cairo.postrm
sudo apt-get remove graphviz-cairo
```.

 and they did the trick, but thanks for your help:)

---

