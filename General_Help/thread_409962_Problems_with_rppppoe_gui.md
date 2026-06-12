---
title: "Problems with rppppoe gui"
date: 2007-04-15
forum: General Help
---

### Post by syd2o2 on 2007-04-15
I just installed Ubuntu 7.04 beta, and I have  a problem with rppppoe.
When I type tkpppoe in terminal I get:
syd@syd:~/Desktop/rp-pppoe-3.8$ tkpppoe
exec: 24: wish: not found
syd@syd:~/Desktop/rp-pppoe-3.8$ 

After the initial installation of Feisty I installed build-essential package with 
sudo apt-get install build-essential
Tnen downloaded rppppoe 3.8 and typed from terminal
sudo ./go-gui
It compiles and installs, but when it's supposed to start gui it fails with that error.
This same process worked and still works on another computer with Ubuntu 6.10.
I need to use rpppoe with gui instead of the default pppoeconf because I often need to switch between two different providers, and it's a lot quicker and easier with a gui.
What am I mising? Can anyone help?

---

### Post by zvacet on 2007-04-15
Is your network manager working?Maybe that can be reason,I don´t know just an idea.

---

### Post by syd2o2 on 2007-04-15
How can I check if it's working?
BTW,I have only wired connections, and use static address.

---

### Post by syd2o2 on 2007-05-01
Now I've installed 7.04 final, and this same problem still persist. This is a really big problem for me, as I switch between isp's many times a day. Nobody else using rspppoe has this problem?
Or why isn't there a gui for making pppoe connections with ubuntu's default software?

---

### Post by syd2o2 on 2007-05-03
New situation. I have two computers with feisty, first has the final version installed, and second was beta, with all updates installed now.
I uninstalled, through add/remove programs network manager on the first computer, and gui for rppppoe was starting. But I had to reinstall the rppppoe for it make connections properly. OK, so it works now, great.
Problem is I did the same thing on the second computer, but I still get the same exec: 24: wish: not found. Installined-uninstallied network manager and rppppoe a few times, but no go. There's one more difference between computers, the second one has kde installed.
Anyone?

---

### Post by thelinuxguy on 2007-05-28
> **syd2o2 said:**
> but I still get the same exec: 24: wish: not found.

You need the tk8.* package.
System >> administration >> Synaptic Package Manager
Install the package tk8.4

Does rp-pppoe work now?

---

