---
title: "apt-dater"
date: 2015-03-27
forum: General Help
---

### Post by strtwtsn on 2015-03-27
Hi

I am looking at configuring a way of managing updates similiar to WSUS on Windows.  Im currently in the process of looking at apt-dater but it isnt immediately clear how I can choose older versions of packages, choose not to upgrade a particular package.  Is it possible to do these things?

If not, is there a way thats cheap (i.e not landscape)

I've configured it using chef / ansible and puippet, but I need to have a more graphical method.

Thanks

---

### Post by Frogs Hair on 2015-03-27
The synaptic package manager offers a setting to lock a package version and  displays all available versions of a package in the current repository relative to the release in use. I have not used these functions and allow packages to upgrade when prompted by the update manager.

---

### Post by v3.xx on 2015-03-27
> how I can choose older versions of packages, choose not to upgrade a particular package.
One way would be pinning the package and I pin with a GUI; Synaptic PM.

[https://help.ubuntu.com/community/PinningHowto](https://help.ubuntu.com/community/PinningHowto)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9)

---

### Post by ian-weisser on 2015-03-27
> **strtwtsn said:**
> it isnt immediately clear how I can choose older versions of packages, choose not to upgrade a particular package.
Why do you want to do that?

That's not intended to be a facetious question. Windows environment upgrades can be quite different from Ubuntu environment upgrades. Your question, and your preference for WSUS, implies that you may be unfamiliar with the differences. 

In Debian and Ubuntu, downgrading is possible, though not well supported by the package manager. 
Most upgrades within a release of Ubuntu are either security patches or Critical/High priority bugfixes. New features and other real changes await the next release of Ubuntu.
Most older versions of packages are generally not retained in the repositories...you will need to cache those yourself.

Most Debian and Ubuntu users are expected to run the latest package *for their release* in order to have fully patched and stable systems.
Enterprise users in your apparent position are recommended to use LTS releases, which offer 5-year stability (minimally changing software, very few upstream non-security/non-bugfix upgrades) precisely so you don't need to actively manage custom versions, and cache old packages, and miss security patches, to maintain workflow and functionality.

---

