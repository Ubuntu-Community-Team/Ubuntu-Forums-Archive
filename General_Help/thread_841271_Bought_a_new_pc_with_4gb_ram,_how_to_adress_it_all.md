---
title: "Bought a new pc with 4gb ram, how to adress it all"
date: 2008-06-26
forum: General Help
---

### Post by Roderik on 2008-06-26
Tonight my new pc arrives, a quad core intel with 4gb ram, and i'm trying to find if i can adress the full 4gb with the default -generic kernel from hardy. I would prefer not to run a -server kernel, not compile my own, and not run an ~amd64 system.

I tried to create a package on launchpad with the latest generic kernel and changing the highmem option to the 64G but it doesn't compile on the build servers.

Is there a simple way to run a 4gb system with more then 3xxxmb memory available?

---

### Post by chrisccoulson on 2008-06-26
Why do you not want to run a 64-bit system? I've been running the 64-bit version since Breezy, so I have seen the availability of applications improve and the number of problems decrease quite significantly over the last 2 years, and I would definately recommend running the 64-bit version. There isn't anything that I use which doesn't work on the 64-bit version now, and I can't think of a good reason to not use it

If you run the 64-bit version, there should be no problem AFAIK.

---

### Post by Roderik on 2008-06-26
I'm aware of the fact that 64bit is improving daily, but there are just a few vital applications that i need for work that have (possibly "had") a bad reputation on 64bit. I have to admit that Feisty was the last 64 bit version i tried.

Eclipse
Java
Flash with everything working (sound etc)
Skype

Secondly, out hosting and developments setups are identical (excluding the X server ofcourse), a 64bit pc just isn't exactly the same and will possibly prevent me from debugging low level performance issues.

And while there are enough guides to make it all work, most of the time, it just has some disadvantages for me personally.

Let it be said, that if there is no other way, i will run 64bit, but i don't think i'm the only ubuntu'er with this wish :)

---

### Post by chrisccoulson on 2008-06-26
64-bit has improved since Feisty.

Eclipse - I can't help you with this as I don't run it, but I see no reason why it wouldn't work. A 64-bit version is packaged in the repositories.

Java - The icedtea-gcjwebplugin package is in the Hardy repositories, which provides a working 64-bit browser plugin for Firefox. I run it, but I don't know how well it works as I don't visit a lot of websites that require it.

Flash - The flashplugin-nonfree package in the Hardy repositories takes care of nspluginwrapper for you, to allow you to run 32-bit Flash in the 64-bit browser. I run it with no issues at all (you need the libflashsupport package too), and it was only an apt-get away (just like the 32-bit version).

Skype - Is available in the Medibuntu repositories. I don't use it, but I see no reason why it wouldn't work. If you install using Medibuntu, it will take care of all the 32-bit compatibility dependencies for you. Any issues you have are likely to be sound related and common to 32-bit and 64-bit platforms.

And there is the 64-bit support section on these forums, where you will find some very knowledgable members who can help you with any problems.

---

### Post by Roderik on 2008-06-27
Ok, based on your recommendations i went with the 64bit version. The only problem is the network adaptor driver, sigh! 

ref: [http://ubuntuforums.org/showthread.php?t=842113](http://ubuntuforums.org/showthread.php?t=842113)

---

