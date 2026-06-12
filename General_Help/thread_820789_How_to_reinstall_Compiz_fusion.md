---
title: "How to reinstall Compiz fusion?"
date: 2008-06-06
forum: General Help
---

### Post by iOli on 2008-06-06
Hello
I had compiz fusion and than i uninstalled it because of some reasons.
Now i wanna install it again
When i type the code in the terminal, it says that its already installed, but i can not find it anywhere..

Can somebody help me?
Thx

---

### Post by rogerdpenguin on 2008-06-06
Go to synaptic package manager, search compiz-fusion, and select the complete removal option.

---

### Post by iOli on 2008-06-09
> **rogerdpenguin said:**
> Go to synaptic package manager, search compiz-fusion, and select the complete removal option.

But then when i reinstall it, and click on it under system, preferences and then compiz config settings manager, nothing happens..
Y?
Thxx

---

### Post by Forlong on 2008-06-10
What's the output when running ```
ccsm
``` in the terminal?

---

### Post by iOli on 2008-06-10
ok now I can start compiz manager, but when I enable an effect, nothing happens and the programm looks weird xD

And also my simple compiz config manager doesn't work..

PS: I have a picture of my weird ccsm

---

### Post by Happy_Man on 2008-06-10
Hm.. try resetting your settings for CCSM by going to ~/.config/compiz and deleting everything inside of it.

---

### Post by magnus0 on 2008-06-10
maybe
```

sudo apt-get remove --purge compiz-fusion && sudo apt-get install compiz-fusion

```

---

### Post by iOli on 2008-06-11
nothing happened..

---

### Post by magnus0 on 2008-06-11
> **iOli said:**
> nothing happened..

sorry, the package name was wrong. should be just compiz instead of compiz-fusion

this should do it:
```

sudo apt-get remove --purge compiz && sudo apt-get install compiz

```

---

### Post by iOli on 2008-06-12
> **magnus0 said:**
> sorry, the package name was wrong. should be just compiz instead of compiz-fusion

this should do it:
```

sudo apt-get remove --purge compiz && sudo apt-get install compiz

```

It redownloaded it but my ccsm is still weird and my simple ccsm is still not workin':confused:

---

### Post by Forlong on 2008-06-12
What's the output when running ```
simple-ccsm
``` in the terminal?

---

### Post by iOli on 2008-06-13
ok it said i have to install some things so i did it. Now I can see it when i click system then preferences and then simple ccsm..but when I click on it nothing happens! :confused:

---

### Post by Forlong on 2008-06-14
And what output do you get now when running
```
simple-ccsm
```
in the terminal?

---

