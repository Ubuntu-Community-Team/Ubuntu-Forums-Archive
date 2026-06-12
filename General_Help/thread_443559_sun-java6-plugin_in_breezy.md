---
title: "sun-java6-plugin in breezy?"
date: 2007-05-14
forum: General Help
---

### Post by howlin_walleye on 2007-05-14
I'm interested in installing jun java6 on breezy. 

The archives have sun-java6-jdk, but apt-get cannot find sun-java6-plugin. 

I've run sudo apt-get update, and I have 'breezy-backports' enabled in sources.lst. 

I can locate the package at packages.ubuntu.com:

[http://packages.ubuntu.com/dapper-backports/web/sun-java6-plugin](http://packages.ubuntu.com/dapper-backports/web/sun-java6-plugin)

yet I still cannot make apt-get or synaptic see it:




dan@badger:~/dev/render/librender$ sudo apt-get -s install sun-java6-plugin
Reading package lists... Done
Building dependency tree... Done
Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-plugin has no installation candidate





Can anyone help explain the discrepancy between packages.ubuntu.com and apt-get?


Dan

---

### Post by mojoman on 2007-05-14
Could it be that the package is there but under another name? Try:
```
apt-cache search java6
```
or
```
apt-cache search sun-java
```
and see if you get a hit on a likely candidate.

My bet is that the package has a slightly different name. If one - under feisty - tries to install for example xine with
```
sudo apt-get install xine
```
one get the exact same error message that you got and the correct thing to do is to
```
sudo apt-get install xine-ui
```.

My guess is that it's the same thing here.

/mojoman

---

### Post by howlin_walleye on 2007-05-14
Correction - I'm using dapper, not breezy. 

Regardless, I think that the plugin doesn't exist for my arch - amd64. This is a long-standing problem -- java plugin on amd64. 

dan

---

### Post by mojoman on 2007-05-15
> **howlin_walleye said:**
> Correction - I'm using dapper, not breezy. 

Regardless, I think that the plugin doesn't exist for my arch - amd64. This is a long-standing problem -- java plugin on amd64. 

dan

Yes it is. I too use 64-bit (Fiesty Xubuntu) and it got java, save for the browser plugins. However, I use 32-bit browser instead, as described in[ this thread]("http://ubuntuforums.org/showthread.php?p=1174435") It works like a charm, java, flash, the full monty.

/mojoman

---

