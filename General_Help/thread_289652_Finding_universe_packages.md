---
title: "Finding universe packages"
date: 2006-10-31
forum: General Help
---

### Post by nocturn on 2006-10-31
Hi all

Is there an easy way to find out which of my installed packages came from universe?

I don't mind doing it in the CLI.

I want to find this out on my server before I migrate to Dapper.

---

### Post by nikhilk on 2006-10-31
This is what I have done a few times now. Not sure (read convinced) this is the easiest way though.

apt-get --print-uris -install <package_name>

Then just check the URI to determine the source of the package. Of course you have to know the name of the package for this (this is the hardest part).

---

### Post by nocturn on 2006-10-31
Thanks, it's a good start.

---

### Post by Rui Pais on 2006-10-31
Don't know if there is a single automated command for that...
You can try to run a simple script like:
```
#!/bin/bash
for pkg in `apt-cache pkgnames`
do   
    if apt-cache show $pkg | grep "Section: universe" >>/dev/null; then 
	if aptitude show $pkg | grep "State: installed" >>/dev/null; then
		echo $pkg
		#echo $pkg >> packages_on_universe.list
	fi
    fi
done
```

it take some time but makes the list

---

