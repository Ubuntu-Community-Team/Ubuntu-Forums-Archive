---
title: "Installed Packages List"
date: 2008-07-06
forum: General Help
---

### Post by petaloid on 2008-07-06
Hey all,
I'll be making a shift from my desktop (which has had ubuntu on it for a year, and has accumulated tonnes of packages) to my laptop (which currently lacks ubuntu, but I'll fix that shortly) and I was wondering if there was a way to install all the same packages I have on my desktop in my laptop with little manual labor.

Better still would be if I could get a piped list of all my installed packages and just download them all using aptitude install. 

Anyone have any ideas?

---

### Post by rraj.be on 2008-07-06
> **petaloid said:**
> Hey all,
I'll be making a shift from my desktop (which has had ubuntu on it for a year, and has accumulated tonnes of packages) to my laptop (which currently lacks ubuntu, but I'll fix that shortly) and I was wondering if there was a way to install all the same packages I have on my desktop in my laptop with little manual labor.

Better still would be if I could get a piped list of all my installed packages and just download them all using aptitude install. 

Anyone have any ideas?

Than just getting a list of installed packages you can just backup all your installed package's.

You can use AptonCD for this.

to install aptoncd type this in terminal
```

sudo apt-get install aptoncd
```

Using this you can create a local repositary of all your installed packages into a disk or DVD.

So you can just install ubuntu in your laptop and insert this created backup disk and start synaptic.

you can install all packages available in the disk.

---

### Post by brian_p on 2008-07-06
> **petaloid said:**
> Better still would be if I could get a piped list of all my installed packages and just download them all using aptitude install. 

Anyone have any ideas?

[http://wiki.debian.org/Packaging/Listing_Installed_Packages](http://wiki.debian.org/Packaging/Listing_Installed_Packages)

---

### Post by petaloid on 2008-07-06
@ brian_p: I notice that the list so generated has packages that came with ubuntu when I installed it. Is there a way I can remove those from the list?

@ rraj.be: some of my packages aren't in the cache, do I have to manually find those?

---

### Post by rraj.be on 2008-07-06
> **petaloid said:**
> @ brian_p: I notice that the list so generated has packages that came with ubuntu when I installed it. Is there a way I can remove those from the list?

No need for this.

Whaen you are using this command

```
apt-get install `cat installed-software.log` 

which was found here
[http://wiki.debian.org/Packaging/Listing_Installed_Packages]("http://wiki.debian.org/Packaging/Listing_Installed_Packages")
```

it will just install what are not installed and will omit the packages already installed.
> 
@ rraj.be: some of my packages aren't in the cache, do I have to manually find those?

No need.AptOnCD will automatically get teh packages which are all installed in your system.

You can even add your packages from some directories if you want to.

---

