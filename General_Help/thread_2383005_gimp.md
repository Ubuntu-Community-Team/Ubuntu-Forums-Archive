---
title: "gimp"
date: 2018-01-19
forum: General Help
---

### Post by wilson-don on 2018-01-19
I have just reinstalled ubuntu 16.04 there is  no gimp here... I have down loaded  it  but it tells me I have to build it... no good for me... cant find it in software center..

---

### Post by cruzer001 on 2018-01-19
Hello

You should not need to go outside our ubuntu sources for packages.  Gimp can be installed in terminal.
```

sudo apt install gimp
```

Thats the basic package, you may want to look at what else is offered.  One way is with Synaptic Package manager.

```
sudo apt install synaptic
```

Then just do a search on gimp.

[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

---

### Post by &amp;KyT$0P# on 2018-01-19
Before following cruzer001's advice, run this in Terminal -
```
sudo apt-get update
```

---

### Post by cruzer001 on 2018-01-19
An excellent suggestion halogen2 :)

---

### Post by steeldriver on 2018-01-19
You may also need to enable the universe repository in your sources

---

