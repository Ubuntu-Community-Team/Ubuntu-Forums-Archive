---
title: "help getting rpm dev tools"
date: 2013-06-08
forum: General Help
---

### Post by PxDuck on 2013-06-08
How can i get these, my googlefu is not helping me and working on trying to set up a socks5 server on 12.04.

yum install rpm-build.x86_64 openldap-devel.x86_64 pam-devel.x86_64 openssl-devel.x86_64 libgssapi-devel.x86_64 -y (for 64 bit Linux)

Please help.

PxDuck

---

### Post by deadflowr on 2013-06-08
yum and rpm are red hat packaging tools.
You'll need to find debian equivalent tools.
Debian and Ubuntu use apt instead of yum.

Best bet is to look through here
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

And see if the packages you need are in there.
Then to install run
```
sudo apt-get install <packagename>
```
replace packagename with the actual package name.

You can install mutilple packages at once by spacing between the packages like
```
sudo apt-get install package1 package2 package3
```

More on apt
```
man apt
```

---

### Post by PxDuck on 2013-06-08
thanks, will play around to see if i can find.

---

