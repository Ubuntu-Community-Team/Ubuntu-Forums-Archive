---
title: "how do I start"
date: 2007-11-05
forum: General Help
---

### Post by irishy on 2007-11-05
Please can someone point me in the right direction
I have with help from the forum now installed feisty fawn and I have had a good look round put in some images and music and found my first problems an orange icon on the panel tells me that an error occured please run package manager error broken count >0 can any one en lighten me about this or show me where to find out,
and looking around i have found another fault  software index broken it is impossible to install or remove software please use the package manager"synaptic" or run sudo apt-get install -f
again can you point me in the right direction
thanks
 irish

---

### Post by trak87 on 2007-11-05
Sounds like a package didn't install correctly and the result is that something about it is broken. To fix it, open System, Administration, Synaptic Package Manager (you will be prompted for your password) and then select Edit, "Fix Broken Packages". That should fix it.

You can also accomplish the same thing via the command line, in a terminal window. Select Applications, Accessories, Terminal, and then type

```
sudo apt-get install -f
```

and press Enter.

---

