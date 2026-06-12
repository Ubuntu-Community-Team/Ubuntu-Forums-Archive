---
title: "Possible to trace &quot;redundant&quot; dependencies of packages marked as manual?"
date: 2015-02-05
forum: General Help
---

### Post by garycheng12 on 2015-02-05
Correct me if I'm mistaken--I learned on this forum that packages marked as manual have dependencies marked as automatic such that commands lik apt-get purge and apt-get autoremove will essentially delete all relevant files (except data files residing in Home) when the main package is installed from a (whether third-party or default) repository as long as it's added to the system. 
However, it appears that default applications/packages** and their dependencies** that come with Ubuntu (or in my case, Kubuntu) are marked manual. For example, not only is Ktorrent marked as manual, but its dependencies are marked manual as well (I know this because on Synaptic, it shows there are several other packages with the name Ktorrent, at least one of which is a dependency specifically for Ktorrent and nothing else--it says that you most likely won't need the package if you remove Ktorrent). However, the other packages with the Ktorrent in its name didn't say this--how can I be sure these dependencies are for Ktorrent only (so that deleting these dependencies won't create problems for other package/applications I may use on Kubuntu)?

Is a there a method to removing redundant dependencies after removing Kubuntu applications (an "apt-get autoremove" function for dependencies marked as manual)? The method above where I searched for packages with the name Ktorrent after removing Ktorrent is not ideal (I might miss finding some dependencies of Ktorrent if they don't have Ktorrent in their name and even if a package has Ktorrent in its name, it might be a dependency needed for other applications that I use, however unlikely).

I know that technically a list of dependencies can be generated for a package, but I would have to go through each dependency and find out if they are itself a dependency for others. Some dependencies might be a dependency for a dependency of the Kubuntu package I want deleted, and as you can see, this can become messy very quickly.

Also, correct me if I'm mistaken--how I got Intellij IDEA ID was download the tar.gz file from the website and extract it, then run idea.sh. There's no installation process, was there? This seems like a "portable application" to me. If it is, are all tar.gz files portable like this? I am thinking about storing these portable applications in the Home directory and if I want to "uninstall" them then I just simply delete the application directory.

---

### Post by ian-weisser on 2015-02-05
> **garycheng12 said:**
> However, it appears that default applications/packages** and their dependencies** that come with Ubuntu (or in my case, Kubuntu) are marked manual.

Yes, that's right.

Let's see what happens when you install Kubuntu from CD will all of the dependencies marked 'auto' (except for the top-level kubuntu-desktop metapackage). 
Everything installs fine.
But say you use evolution instead of kmail, so let's make a small change and uninstall kmail.
And there's the GOTCHA - uninstalling kmail requires uninstalling kubuntu-desktop...which means your ENTIRE SYSTEM is suddenly eligible for autoremoval...including apt itself.

It's foolish to let a normal, everyday user decision imperil your entire system.
So the Ubuntu developers workaround the issue by having the installer mark ALL first-install packages as 'manual'. 
Subsequent apt installs use marking properly.

In fact, we see this occur occasonally from users who install using the mini.iso instead of the normal install .iso. They build a great system from a tiny base by apt-get installing. They install a desktop using a metapackage. Then, a week or so later, they delete one dependency application from that desktop, they ignore the warning message ('hey, you're about to remove 250MB of system packages'), and then they show up here wondering what happened.

It's theoretically possible to do an intermediate step - to make the installer mark only high-level applications (kmail, dolphin, etc) as 'manual' instead of everything...but that requires a human to spend time each release cycle manually going through and checking those application markings. Nobody has joined the Installer Team and volunteered to do that.

> **garycheng12 said:**
> how can I be sure these dependencies are for Ktorrent only (so that deleting these dependencies won't create problems for other package/applications I may use on Kubuntu)?

Two ways: 
1) The **apt-cache rdepends <packagename>** command will list all packages, both installed and uninstalled, that depends upon <packagename>.

2) Try a *simulation* of removing the package and see what happens:  **sudo apt-****get remove --simulate <packagename>**


> **garycheng12 said:**
> Is a there a method to removing redundant dependencies after removing Kubuntu applications[QUOTE]
No. That's what apt-marking is meant for...but deliberately misused by the Ubuntu installer.


[QUOTE=garycheng12;13222423]Also, correct me if I'm mistaken--how I got Intellij IDEA ID was download the tar.gz file from the website and extract it, then run idea.sh. There's no installation process, was there? This seems like a "portable application" to me. If it is, are all tar.gz files portable like this?
That's called 'manually installing', and it's the way we installed software 25 years ago. It's portable in the sense you mean, but it also has a lot of shortcomings (namespace conflicts, invalid developer assumptions, hardcoded paths, etc). Packages and package managers were created to address many of those shortcomings. 
Debian packages are 'portable' in the same way - apt stores deb packages in /var/cache/apt/archives/

---

### Post by garycheng12 on 2015-02-05
> **ian-weisser said:**
> 
Let's see what happens when you install Kubuntu from CD will all of the dependencies marked 'auto' (except for the top-level kubuntu-desktop metapackage). 
Everything installs fine.
But say you use evolution instead of kmail, so let's make a small change and uninstall kmail.
And there's the GOTCHA - uninstalling kmail requires uninstalling kubuntu-desktop...which means your ENTIRE SYSTEM is suddenly eligible for autoremoval...including apt itself.



So uninstalling any dependency marked as auto will uninstall the package depending it? And uninstalling any dependency marked as manual will simply leave the package either partially functional or dysfunctional with broken dependencies (as opposed to uninstalling the packages that depend on it)? I'm guessing there's a command to solve the issue of a broken package in this scenario by installing back any missing dependencies? 

Either way, it seems that tracking/deleting all the dependencies of default applications is too tedious/dangerous--I will just read the descriptions of the dependencies and delete the obvious ones that are dependent only for that application. Unused dependencies have zero impact on the performance of the system and take up a trivial amount of space anyway (zero overhead), right? My guess is that even among the most experienced Linux users, tracking down all manually redundant dependencies in the system is impractical and unneeded.

---

### Post by ian-weisser on 2015-02-05
> **garycheng12 said:**
> So uninstalling any dependency marked as auto will uninstall the package depending it?

Yes.
If 'foo' depends on 'libfoo', and you uninstall libfoo, 
then apt will promptly remove everything that depends on libfoo, including foo.
That's not autoremoval, and that's unrelated to marking. That's just basic dependency management.

> **garycheng12 said:**
> And uninstalling any dependency marked as manual will simply leave the package either partially functional or dysfunctional with broken dependencies (as opposed to uninstalling the packages that depend on it)?

No.
Uninstalling any dependency, regardless of marking, will cause all packages that depend upon it to be promptly uninstalled. (see example above)
Again, not related to autoremoval, nor marking. Basic dependency management.


> **garycheng12 said:**
> I'm guessing there's a command to solve the issue of a broken package in this scenario by installing back any missing dependencies? 

Apt handles dependencies *automatically* so you don't run into this scenario.
You will never see a functioning system with foo installed but libfoo missing...unless the admin has really screwed it up.


> **garycheng12 said:**
> [I]t seems that tracking/deleting all the dependencies of default applications is too tedious/dangerous--I will just read the descriptions of the dependencies and delete the obvious ones that are dependent only for that application. Unused dependencies have zero impact on the performance of the system and take up a trivial amount of space anyway (zero overhead), right? My guess is that even among the most experienced Linux users, tracking down all manually redundant dependencies in the system is impractical and unneeded.

That's how I view it. Well said.

Some users really want a 'lean' system. Rather that tear down their install, I encourage them to try the [minimal .iso]("https://help.ubuntu.com/community/Installation/MinimalCD") and build up from there. Takes a bit of skill and patience to do so.
I've built up from minimal. It's a good way to learn dependencies and metapackages...and the perils of autoremove without a net.

---

### Post by sandyd on 2015-02-05
*Moved to general help*

---

### Post by garycheng12 on 2015-02-05
Thanks, ian-weisser. Very easy to digest the information from one source.

---

### Post by garycheng12 on 2015-02-11
> **ian-weisser said:**
> 
No.
Uninstalling any dependency, regardless of marking, will cause all packages that depend upon it to be promptly uninstalled. (see example above)
Again, not related to autoremoval, nor marking. Basic dependency management.


Actually, the reason why I thought of that is because ultimately, ktorrent is a dependency of kubuntu-desktop. Why does removing ktorrent not remove kubuntu-desktop then?

---

### Post by ian-weisser on 2015-02-11
```
$ apt-cache show kubuntu-desktop | grep ktorrent
Recommends: [...] ktorrent, [...]
```

ktorrent is merely 'recommended' by kubuntu-desktop. Not required ('depends').
'Recommend' means that the packages enhances the usefulness,  but is not required.

An apt setting determines if 'recommends' (and 'suggests') packages are included in your package actions.

---

### Post by garycheng12 on 2015-02-11
You are right, but why does* apt-cache rdepends ktorrent *show kubuntu-desktop if it's not a dependency?

---

### Post by ian-weisser on 2015-02-11
The apt-cache manpage explains:
>        --no-pre-depends, --no-depends, --no-recommends, --no-suggests,
       --no-conflicts, --no-breaks, --no-replaces, --no-enhances
           **Per default the depends and rdepends print all dependencies**. This
           can be tweaked with these flags which will omit the specified
           dependency type. Configuration Item: APT::Cache::ShowDependencyType
           e.g.  APT::Cache::ShowRecommends.


Compare the output of the following two commands.
It should make things clearer.

```
apt-cache rdepends ktorrent
apt-cache rdepends ktorrent --no-recommends
```

---

### Post by garycheng12 on 2015-02-11
Thank you, I should get in the habit of going through manuals available through the console--not sure why I tend to think it's only available online and I have to dig hard for it.

---

