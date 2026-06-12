---
title: "Removing packages..."
date: 2006-12-21
forum: General Help
---

### Post by M0nk3yM4n on 2006-12-21
I'm having problems with my z600cups package, every time I try a sudo apt-get update or install it says that the package is damaged or something and that it can't find the archive file for it to fix it. How do I just remove the whole thing? I've tried redownloading the red hat drivers off the Lexmark site for my Dell 720 and they for some reason after be converted by alien damaged or something. I think it has to do something with the script command...but anyway how do I just get rid of the whole thing? So I can at least update and function normally.

---

### Post by an.echte.trilingue on 2006-12-21
```
apt-get remove package_name
```

This doesn't work???

---

### Post by M0nk3yM4n on 2006-12-21
> **an.echte.trilingue said:**
> ```
apt-get remove package_name
```

This doesn't work???


Reading package lists... Done
Building dependency tree
Reading state information... Done
E: The package z600cups needs to be reinstalled, but I can't find an archive for it.

This is what is returned...](*,)

---

### Post by M0nk3yM4n on 2006-12-21
Opening up Synaptic Package Manager gives me this little treat....

A new window opens that says..

An error occured
E: The package z600cups needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

:confused:

---

### Post by an.echte.trilingue on 2006-12-21
what does 

```
dpkg --remove package_name
```

do?

---

### Post by M0nk3yM4n on 2006-12-21
Additionally when I click "reload" in the package manager, it attempts to download the indexes but then just stops...clicking reload again gives me a new window that says.

Could not download all repository indexes
The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

I'm using the same computer to do this as I write this post. I'm also using 6.10, which I think is a fatal mistake =(.

---

### Post by M0nk3yM4n on 2006-12-21
> **an.echte.trilingue said:**
> what does 

```
dpkg --remove package_name
```

do?

Well maybe a little more insight...

doing that returns....

dpkg: error processing z600cups (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 z600cups

---

### Post by an.echte.trilingue on 2006-12-21
try 

```
sudo dpkg --remove --force-remove-reinstreq package_name
```

If that does not work, you can edit  /var/lib/dpkg/status and remove all package_name entries, followed by```
sudo dpkg --purge package_name
``` however this might leave bits of the program installed, meaning that you will have to use the --force option when you try to install it again.

Good luck,
-mat

---

