---
title: "Cannot install Gnucash in 12.10"
date: 2012-12-17
forum: General Help
---

### Post by mirzahadi on 2012-12-17
I can't install Gnucash in a fresh, fully update install of Ubuntu 12.10. Terminal gives the following error:
> sudo apt-get install gnucash
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gnucash : Depends: guile-1.8 (>= 1.8.8+1-4~) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

---

### Post by ibjsb4 on 2012-12-17
You can try the fix broken package command.

```
sudo apt-get install -f
```

---

### Post by mirzahadi on 2012-12-17
I tried that but it still gives the same error

> sudo apt-get install -f gnucash
[sudo] password for adil: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gnucash : Depends: guile-1.8 (>= 1.8.8+1-4~) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


---

### Post by ibjsb4 on 2012-12-17
The package is there (guile 1.8.8+1-6), have you tried just installing it?

Are you familiar with synaptic package manager?  It is basically a GUI for apt-get and by using it to install a package it will tell you if your about to break anything or remove anything or conflicts with anything.  Its just handy when working with problem software packages.

I would suggest loading it and using it to install guile-1.8 just to make sure that you won't be creating problems.

```
sudo apt-get install synaptic
```

Use it to do a quick search on guile and install.  You will get a popup before the package is installed that will alert you of any problems. 

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=synaptic+package+manager&as_qdr=all&sa=Google+Search&lang=en]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=synaptic+package+manager&as_qdr=all&sa=Google+Search&lang=en")

---

### Post by mirzahadi on 2012-12-17
Thanks.  I just removed and then re-installed guile from synaptic and Gnucash is now installed! 

I really appreciate your time.

---

### Post by ibjsb4 on 2012-12-17
Welcome  :)

---

