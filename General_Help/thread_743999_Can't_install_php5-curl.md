---
title: "Can't install php5-curl"
date: 2008-04-03
forum: General Help
---

### Post by fluid_motion on 2008-04-03
I can't seem to install php5-curl. I already have libcurl3-gnutls installed and even tried removing and reinstall it, I did the install -f too and yet it still gave me the same message.

```
~$ sudo apt-get install php5-curl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  php5-curl: Depends: libcurl3 (>= 7.16.2-1) but it is not installable
E: Broken packages

```

How do I fix this broken package?

---

### Post by jrib on 2008-04-03
1. paste the contents of your /etc/apt/sources.list and all files in /etc/apt/sources.list.d .  
2. paste the output of ```
apt-cache policy php5-curl libcurl3 libc6
```
3. Have you installed any .deb files manually or used repositories not currently in your sources.list?

---

### Post by fluid_motion on 2008-04-03
Just checked, repositories are messed up. Silly me, must have changed when I used the update manager detect best repository thing. Thanks for that suggestion, it can finally install. :)

---

