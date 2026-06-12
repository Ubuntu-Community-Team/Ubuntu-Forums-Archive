---
title: "How do I make apt-get to ignore unfound packages?"
date: 2014-04-13
forum: General Help
---

### Post by woohoomoo2u on 2014-04-13
I messed up my ubuntu install and took the default manifest to try to install everything I uninstalled again. I got the manifest and combined all the lines, then I made it into a script. The only problem is that i still have the version numbers in the lias of packages and they obvilously can't be found. (ex: 12.244.54~ubuntu656). How do I get apt-get to ignore the packages that can't be found?

---

### Post by ian-weisser on 2014-04-14
By removing package versions and missing packages from your 'default manifest', whatever that is.

Neither apt-get nor dpkg will "ignore" input from you, the admin. The system is set up to assume that your input is Truth, and that you know what you want. If your input specifies a version, the system assumes you really want that specific version.

I would instead use apt the way it's intended to be used - to resolve dependencies for you. For example, if you want to install the Inkscape application, just tell apt you want Inkscape and let it figure out what needs to be installed and where to get it from. You shouldn't need to give apt a long script or list.

---

### Post by woohoomoo2u on 2014-04-14
ubuntu-14.04-desktop-amd64.manifest
I should have been more clear, here is an example of my script:
 ```
#!/bin/sh
echo test
sudo apt-get install account-plugin-aim    3.8.6-0ubuntu7 account-plugin-facebook    0.11+14.04.20131126.2-0ubuntu2 account-plugin-flickr    0.11+14.04.20131126.2-0ubuntu2 account-plugin-google    0.11+14.04.20131126.2-0ubuntu2 account-plugin-jabber    3.8.6-0ubuntu7 account-plugin-salut    3.8.6-0ubuntu7 account-plugin-twitter    0.11+14.04.20131126.2-0ubuntu2 account-plugin-windows-live    0.11+14.04.20131126.2-0ubuntu2 account-plugin-yahoo    3.8.6-0ubuntu7 accountsservice    0.6.35-0ubuntu7 acl    2.2.52-1 acpi
```

now how do i get apt-get to ignore #.#.#ubuntu#(or in other words, 0.6.35-0ubuntu7). Becuase othe wise:
```
E: Unable to locate package 0.6.35-0ubuntu7
E: Couldn't find any package by regex '0.6.35-0ubuntu7'
```

---

### Post by ian-weisser on 2014-04-14
That file isn't meant to be plugged into apt-get. And apt-get isn't meant to be used that way.

Do you really want all those plugins?

If you want to restore your desktop to a group of packages similar to your original install state, then merely re-install the 'ubuntu-desktop' metapackage (or kubuntu-desktop, or xubuntu-desktop, etc). It will pull in all relevant dependencies for you.

---

