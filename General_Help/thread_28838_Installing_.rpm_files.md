---
title: "Installing .rpm files?"
date: 2005-04-21
forum: General Help
---

### Post by Gunadic on 2005-04-21
I'm a bit... well a total newbie when it comes to linux, and I'm looking to install FirstClass, the program my school uses for Email. However its in a .rpm folder, and I have no idea where to put their contents when the extractor comes up... a little help for the newbie?

Thanks

---

### Post by heimo on 2005-04-21
You can convert rpm packages to deb packages with [alien]("http://packages.ubuntu.com/hoary/admin/alien")

First install alien on your system.
 ```
sudo apt-get install alien

``` 

Convert Firstclass.rpm to deb package (Debian package)
 ```
sudo alien firstclass.rpm
``` 

Install the deb package using dpkg:
 ```
sudo dpkg -i firstclass.deb
``` 

It's not perfect, but works most of the time. Good luck!

---

### Post by Gunadic on 2005-04-23
I've tried this, but I keep getting an error thats really ticking me off. Its the same error that I get when I attempt to run 

sudo apt-get update

which stalls at 99%

---

### Post by heimo on 2005-04-24
[QUOTE=Gunadic]I've tried this, but I keep getting an error thats really ticking me off. Its the same error that I get when I attempt to run 

sudo apt-get update

which stalls at 99%[/QUOTE]

Could you please quote that error?

Thanks!

---

