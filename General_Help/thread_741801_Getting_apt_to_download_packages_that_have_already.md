---
title: "Getting apt to download packages that have already been installed"
date: 2008-04-01
forum: General Help
---

### Post by tel93 on 2008-04-01
I am compiling an ISO file containing a modified Xubuntu. I would like to download new packages in order to use on this modified Xubuntu. However, when I want to just download the package files for software that I've installed (using apt-get -y -d install package), it won't let me, saying that I had already installed these packages. Is it possible for me to download the package files even if they've been installed?

---

### Post by erginemr on 2008-04-01
You can use the command from the terminal:
```
aptitude download *package_name*
```

This will install the packages to your */home/user_name* folder or wherever you are.

---

### Post by tel93 on 2008-04-02
Well that didn't help at all. All it does is download one package, not all that are needed. Is it possible to force apt-get?

---

### Post by erginemr on 2008-04-02
I see. You want to download a whole set of packages with dependency handling.
Hmm. Let me see... :-k

EDIT: Well, this is a difficult plight indeed. I believe you cannot force apt-get to download all dependent packages, because those have already been installed in your system and are not dependent anymore. There should be another way...

---

### Post by erginemr on 2008-04-02
I believe the best way is virtualization. You should download and install VirtualBox ([http://www.virtualbox.org/](http://www.virtualbox.org/)) either in Ubuntu or in Windows. And then, set up a virtual Xubuntu system from either Xubuntu Live CD or Alternate CD (both has its benefits, with the Alternate CD containing the actual *.deb packages to be installed). Install Xubuntu to your virtual hard drive this way.

Then beginning with this new, fresh system, you should customize it as you want, install extra programs and such. The Debian packages for the installed extra software (including their dependencies) will go into "/var/cache/apt/archives" directory of your virtual OS.

When you are done, you can use **remastersys** to rebuild the Xubuntu Live CD with your customizations. You may consider to exclude your /home/user_name directory for a generic Live CD, and flush "/var/cache/apt/archives" with "sudo aptitude clean" to save same space, though.

For more details on remastersys, please refer to:
[http://www.remastersys.klikit.org/](http://www.remastersys.klikit.org/)
[http://linuxmint.com/wiki/index.php/Remastersys](http://linuxmint.com/wiki/index.php/Remastersys)

---

