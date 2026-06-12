---
title: "how do I start"
date: 2007-11-05
forum: General Help
---

### Post by irishy on 2007-11-05
Please can someone point me in the right direction
I have with help from the forum now installed feisty fawn and I have had a good look round put in some images and music and found my first problems an orange icon on the panel tells me that an error occurred please run package manager error broken count >0 can any one en lighten me about this or show me where to find out,
and looking around i have found another fault  software index broken it is impossible to install or remove software please use the package manager"synaptic" or run sudo apt-get install -f
again can you point me in the right direction
thanks
 irish

---

### Post by fjgaude on 2007-11-05
Okay, open a terminal from the menu, Applications/Accessories/Terminal:

```
sudo apt-get install -f
```

Key in your password and hit Enter. That should fix things that have gone wrong.

---

