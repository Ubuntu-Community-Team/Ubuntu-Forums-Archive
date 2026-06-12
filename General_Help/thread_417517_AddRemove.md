---
title: "Add/Remove"
date: 2007-04-21
forum: General Help
---

### Post by allenuhelp1256 on 2007-04-21
I am new to really using this program but it looks great.

In Applications -> Add/Remove, on initial load I get:

" The List of Available Applications is out of date"

with options for reload or close.

On reload attempt, I get:

"Downloading package"

Then it says something like: Package is not available due to network issues (which is not on my side!) or file has moved.

Unfortunately, this window/app is now frozen so I can't give exact message. I will have to reboot.

It looks like it looking for something on the web at Ubuntu.

any ideas?

I will reboot again to see message.

---

### Post by allenuhelp1256 on 2007-04-21
This is the message:

"Could not download all repository indexes"

Here is more in dialogue box:


"http://archive.canonical.com/ubuntu/dists/dapper-commercial/main/binary-i386/Packages.bz2: Sub-process bzip2 returned an error code (2)"

---

### Post by zvacet on 2007-04-21
Programs>accessories>terminal
```
sudo aptitude update
```

---

