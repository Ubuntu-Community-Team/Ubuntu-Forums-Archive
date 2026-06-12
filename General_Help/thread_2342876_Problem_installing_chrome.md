---
title: "Problem installing chrome"
date: 2016-11-10
forum: General Help
---

### Post by davehenson on 2016-11-10
> **kevdog said:**
> Try these commands since you need to install google-chrome using a ppa repository

```

sudo sh -c 'echo "deb http://dl.google.com/linux/chrome/deb/ stable main" > /etc/apt/sources.list.d/google.list'
wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add -
sudo apt update
sudo apt install google-chrome-stable

```

These instructions were taken from this site:[http://www.ubuntumaniac.com/2016/04/install-google-chrome-50-on-ubuntu-1604.html](http://www.ubuntumaniac.com/2016/04/install-google-chrome-50-on-ubuntu-1604.html)


Kevdog, thanks for posting this!!!  although it did work for me, it appears to return some errors. I'm not sure what to make of them. after the wget, it returned this:

```
dave@daveubuntu:~$ wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add -
N: Ignoring file '20auto-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
N: Ignoring file '20auto-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
N: Ignoring file '20auto-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
N: Ignoring file '20auto-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
N: Ignoring file '20auto-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
N: Ignoring file '20auto-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
N: Ignoring file '20auto-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
N: Ignoring file '20auto-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
N: Ignoring file '20auto-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
N: Ignoring file '20auto-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
N: Ignoring file '20auto-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
OK



```


I proceeded on and in updating my packages it returned this:
```
Fetched 200 kB in 1s (165 kB/s)                    Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
N: Ignoring file '20auto-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
N: Skipping acquire of configured file 'main/binary-i386/Packages' as repository 'http://dl.google.com/linux/chrome/deb stable InRelease' doesn't support architecture 'i386'



```


Is this something with the repository or with my configuration?  

Also btw in the end, Chrome DID actually install and Netflix works well with it.  I also have Chromium installed but it does not work with Netflix. It instead redirects me to an error page for HTML5 and Silverlight. [https://help.netflix.com/en/node/23742](https://help.netflix.com/en/node/23742) 

do you happen to know if Chromium works (for anyone) with Netflix?  Ideally I would like to use as much open source as possible. Hence me preferring chromium if at all possible.

---

### Post by QIII on 2016-11-10
Moved to its own post from [https://ubuntuforums.org/showthread.php?t=2342299](https://ubuntuforums.org/showthread.php?t=2342299).

Posting a question in a thread marked "solved" is not likely to draw people looking to help.

Cheers!

---

### Post by ian-weisser on 2016-11-10
It's a warning, not an error.
Your settings for the unattended-upgrades application changed during your release-upgrade to 16.04.
Your old settings are saved in the ucf-dist file.

If you like the new settings, delete the old file.
If you like the old settings, restore from the old file.
If you have no idea, then live with the warnings for a few weeks until you have a preference.

---

### Post by davehenson on 2016-11-11
> **ian-weisser said:**
> It's a warning, not an error.
Your settings for the unattended-upgrades application changed during your release-upgrade to 16.04.
Your old settings are saved in the ucf-dist file.

If you like the new settings, delete the old file.
If you like the old settings, restore from the old file.
If you have no idea, then live with the warnings for a few weeks until you have a preference.

thanks for the clarification Ian!

---

