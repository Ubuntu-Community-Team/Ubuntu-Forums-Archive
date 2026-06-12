---
title: "Blocked or Broken"
date: 2021-08-21
forum: General Help
---

### Post by wyattwhiteeagle on 2021-08-21
What can be done to repair or purge, or delete packages and dependencies which are blocked or broken?

---

### Post by T6&amp;sfpER35% on 2021-08-21
[https://itsfoss.com/synaptic-package-manager/](https://itsfoss.com/synaptic-package-manager/)

---

### Post by wyattwhiteeagle on 2021-08-21
Synaptic Package Manager, if it won't allow me to completely get rid of any snap package, especially when I no longer or neveruse it, I believe I would rather use a different package manager which allows me the ability to choose.

What about using the terminal for working with packages?

Maybe a command line to show the names of packages, what package's each one depends upon as well their dependencies.

And maybe some command lines for repairing, removing or uninstalling packages.

---

### Post by mikewhatever on 2021-08-21
It depens what kind of packages need repairing/removing. Snaps are not the same as debs, and both are not the same as appimage or flatpack.
Do you want a manual for all existing packages?
In case there are hundreds of such packaged, an they are impossible to list, backup and reinstall, but otherwise, provide details.

---

### Post by dragonfly41 on 2021-08-21
I find [Stacer GUI]("https://oguzhaninan.github.io/Stacer-Web/#:~:text=Stacer%20is%20an%20open%20source,all%20in%20one%20system%20utility.") to be useful.

You can manage both packages and snaps through a neat GUI.

---

### Post by T6&amp;sfpER35% on 2021-08-21
Remove packages that didn’t install completely.
```
sudo apt-get autoclean
``` 


Remove your apt-cache.
```
sudo apt-get clean
```


Remove software dependencies that you don’t need.
```
sudo apt-get autoremove
```


clear thumbnails
```
rm -rfv ~/.cache/thumbnails
```


clear cache
```
sudo du -sh /var/cache/apt
```




update 
```
sudo apt-get update -y
```


upgrade
```
sudo apt upgrade
```




Kernel and other Cleanups after Deletions
```
sudo apt autoremove --purge
``` 

to delete package
```
sudo apt remove (package name)
```

to delete snap package
```
sudo snap remove (package name)
```


stacer a nice GUI  tool too,as stated
```
sudo apt install stacer
```

---

### Post by dragonfly41 on 2021-08-21
Adding another tool to the list .. for managing PPA's

[https://launchpad.net/~webupd8team/+archive/ubuntu/y-ppa-manager](https://launchpad.net/~webupd8team/+archive/ubuntu/y-ppa-manager)

---

### Post by wyattwhiteeagle on 2021-08-21
thank you a whole bunch...

Are there commands for the terminal to create a list of broken, blocked or unmet items?


> **3nd said:**
> Remove packages that didn&#8217;t install completely.
```
sudo apt-get autoclean
``` 


Remove your apt-cache.
```
sudo apt-get clean
```


Remove software dependencies that you don&#8217;t need.
```
sudo apt-get autoremove
```


clear thumbnails
```
rm -rfv ~/.cache/thumbnails
```


clear cache
```
sudo du -sh /var/cache/apt
```




update 
```
sudo apt-get update -y
```


upgrade
```
sudo apt upgrade
```




Kernel and other Cleanups after Deletions
```
sudo apt autoremove --purge
``` 

to delete package
```
sudo apt remove (package name)
```

to delete snap package
```
sudo snap remove (package name)
```


stacer a nice GUI  tool too,as stated
```
sudo apt install stacer
```

---

### Post by dragonfly41 on 2021-08-21
Synaptic Package Manager which you have already tried has Edit > Fix Broken Packages.
As explained Synaptic does not manage snaps.

---

### Post by monkeybrain20122 on 2021-08-21
> **dragonfly41 said:**
> I find [Stacer GUI]("https://oguzhaninan.github.io/Stacer-Web/#:~:text=Stacer%20is%20an%20open%20source,all%20in%20one%20system%20utility.") to be useful.

You can manage both packages and snaps through a neat GUI.

Can't you do that with the software store?

---

### Post by monkeybrain20122 on 2021-08-21
> **wyattwhiteeagle said:**
> thank you a whole bunch...
...
Are there commands for the terminal to create a list of broken, blocked or unmet items?

apt doesn't manage snap.

---

### Post by ajgreeny on 2021-08-21
You can also run any apt or apt-get command using the -s option (simulate) which will go through the process and echo any action, ie, install, remove, etc, that the command would normally do but the -s option means nothing will actually happen and there will be nothing installed or removed.

So if you want to see what the ***sudo apt autoremove*** command will uninstall just add the -s option, ie ***sudo apt -s autoremove***, though even without the option you will still see the list, though not in a line by line layout, so not as easy to read as with the -s option, and you can still chose not to run the command simply by hitting the n key.

---

### Post by TheFu on 2021-08-21
[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) has lots of information, presented in the correct order, to limit confusion.
Snaps are a Canonical thing.  They have a website just to explain them.  Google finds it easily.

For all command line tools (also called CLI or shell), there are manpages which are references, not beginner guides.  The manpages for apt, apt-get, aptitude, are fairly clear once you know the terminology.  But there's only one way to learn the correct meaning of terms.  Time and looking each up as you come across it.

For GUI stuff, things are harder.  Look for the "Ubuntu Desktop Guide" and documentation for each GUI program.

But really beginning with a book - at least skim it - will help to get an overview.

---

### Post by wyattwhiteeagle on 2021-08-22
After removing a package or snap package, how can I prevent it from reinstalling through CLI or GUI?

---

### Post by wyattwhiteeagle on 2021-08-22
> **ajgreeny said:**
> You can also run any apt or apt-get command using the -s option (simulate) which will go through the process and echo any action, ie, install, remove, etc, that the command would normally do but the -s option means nothing will actually happen and there will be nothing installed or removed.

So if you want to see what the sudo apt autoremove command will uninstall just add the -s option, ie sudo apt -s autoremove, though even without the option you will still see the list, though not in a line by line layout, so not as easy to read as with the -s option, and you can still chose not to run the command simply by hitting the n key.

So, using the -y option...would it be like the -s option wasn't used?

```
sudo apt -s autoremove -y

```

---

### Post by monkeybrain20122 on 2021-08-22
> **wyattwhiteeagle said:**
> After removing a package or snap package, how can I prevent it from reinstalling through CLI or GUI?

If you install with synaptic or apt cli then it won't install snap, the only exception is chromium (not to be confused with google-chrome), where sudo apt install chromium-browser would execute a script that installs the snap (there is no deb package for chromium).

With the software store you can view the details before you install, if the provider is snapcraft then it is a snap, otherwise it is a deb.

---

### Post by monkeybrain20122 on 2021-08-22
> **wyattwhiteeagle said:**
> So, using the -y option...would it be like the -s option wasn't used?

```
sudo apt -s autoremove -y

```

Never use the -y option. That means yes to everything so you don't have a chance to back track even if the command removes half of your system. I know many tutorials and instructions use it, it is terrible.

---

### Post by wyattwhiteeagle on 2021-08-22
> **monkeybrain20122 said:**
> Never use the -y option. That means yes to everything so you don't have a chance to back track even if the command removes half of your system. I know many tutorials and instructions use it, it is terrible.

Ok, so the -y option overrides the -s option.

"Note To Self: Never use the -y options unless you are positively, absolutely certain of what you are gaining/losing."

---

### Post by deadflowr on 2021-08-22
> **wyattwhiteeagle said:**
> Ok, so the -y option overrides the -s option.

"Note To Self: Never use the -y options unless you are positively, absolutely certain of what you are gaining/losing."

The -y option overrides the ability of a user to review and confirm what will happen.
But if running with the simulation option -s it's moot as simulations run without a need to confirm.
So it (the -y option) actually has no affect when using the -s option.

Also, simulations can be run without sudo as it's not making any changes to the system. fwiw.

---

