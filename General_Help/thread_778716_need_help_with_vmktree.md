---
title: "need help with vmktree"
date: 2008-05-02
forum: General Help
---

### Post by bschick on 2008-05-02
I am new to Linux, but have managed to setup an Ubuntu server with VMware Server running 3 servers. I have the MUI running fine and the system is great. I needed a way to monitor the process over time and it was suggested to use vmktree. 

The question, can someone help me with a step by step install for this app or point me in the right direction, the web site is very general and the app fails because it needs rrdtools - that site is not too helpfull and I follow that one and it fails with another missing item. After 3 or 4 layers of installing I get lost. 

Any help would be appreciated.

---

### Post by larstr on 2008-06-12
The install procedure should be fairly straight forward if you install the prerequisites from synaptics or apt-get.

rrdtool is available in synaptics and I'm not sure where it's failing for you.

You can also install rrdtool and bzip2 from the command line with the command:
```
sudo apt-get install rrdtool bzip2
```

If you already have the MUI working you shouldn't need any other non-standard libs. 

Now unpack the archive file you just downloaded from the site and run

```
tar xjvf tar xjvf vmktree- <- press tab, then enter
cd vmktree- <- press tab, then enter
sudo ./install.sh
```

That should be it.

Lars

---

