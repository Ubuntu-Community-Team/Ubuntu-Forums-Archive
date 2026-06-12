---
title: "Dynamic default gateway &amp; Stardict dictionaries"
date: 2007-02-01
forum: General Help
---

### Post by Dislimit on 2007-02-01
SCIM-bridge, Dynamic default gateway & Stardict dictionaries
Just installed 6.10. After a search, 3 questions left:

1. After I followed the direction in [http://wiki.ubuntu.org.cn/](http://wiki.ubuntu.org.cn/) to setup SCIM (use scim-bridge instead), 
I can't switch input method now. The modification is:
```

sudo apt-get install scim-bridge scim-qtimm
sudo gedit /etc/X11/xinit/xinput.d/scim

```
And change
```
GTK_IM_MODULE="scim"
```
to
```
GTK_IM_MODULE="scim-bridge"
```
Is the guide incorrect or what?

2. Stardict dictionaries.
I've installed Stardict as usual, but I can't found any dictionaries such as stardict-oxford-gb,
which should be there due to some online help, through Synaptic even if I added cn99 and enables Backports.
Any ideas?

3. How to select default gateway dynamically?
Back in 5.10 we have an option in the network admin dialog to select a default gateway,
but now it is no long there.
I have two network interface.
eth0 (wired)
eth1 (wireless)
Neither of them is in my auto list, but they both come up after I boot up and log in.
The route cmd shows that they are both working as gateways. But it seems that Ubuntu
likes to use eth1 while I like eth0 sometimes instead. I hope there is a better way to
select the default gateway online better than ifdown one of them.

---

