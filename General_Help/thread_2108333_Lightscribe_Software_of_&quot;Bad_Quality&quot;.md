---
title: "Lightscribe Software of &quot;Bad Quality&quot;"
date: 2013-01-24
forum: General Help
---

### Post by Petro Dawg on 2013-01-24
I'm trying to install software (lightscribe-1.18.26.7-linux-2.6-intel.deb) for my Lightscribe DVD burner directly from the [Lightscribe web site]("http://www.lightscribe.com/downloadsection/linux/index.aspx?id=1372").   The package is a .DEB and can be installed with the Ubuntu software center.  However, when trying to install the software I am met with a warning message stating "the package is of bad quality"  and the details state "The package doesn't provide a valid Installed-Size control field.  See Debian Policy 5.6.20."  *A screen shot of the warning is attached.*

So... how serious of a warning is this?  Is there another option to get Lightscribe working in Ubuntu 12.04.1? 

There are also command line instructions on the Lightscribe web site for installing the same package, mainly... 
```
sudo dpkg -i [I]«filename»
[/I]
```but I'm wary of trying it after the warning message received through the software center.

---

### Post by mlentink on 2013-01-24
It's a bug. Installing Google Earth from the deb on the Google-website will yield you the same message.
If you really trust the source, simply let it install anyway.

---

