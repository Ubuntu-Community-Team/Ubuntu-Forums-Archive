---
title: "apt-get update problems"
date: 2005-08-12
forum: General Help
---

### Post by Digitallysick on 2005-08-12
Fetched 2011kB in 4s (417kB/s)
Extracting templates from packages: 100%
Preconfiguring packages ...
dpkg: parse error, in file `/var/lib/dpkg/status' near line 6006 package `python2.4-dbus':
 missing version
E: Sub-process /usr/bin/dpkg returned an error code (2)


any ideas?

---

### Post by DJ_Max on 2005-08-12
Haven't seen this error. What do you remember doing before you got this error? You need to provide a little more info, as right now I'm swinging in the dark.

---

### Post by Digitallysick on 2005-08-13
well i think i somehow uninstalled Libc6 , in kynaptic, it screwed up alot of stuff, i think alot of packages are missing, i was trying to "upgrade" the libc6 , i am not sure what all is missing, is there anyway to re install the ubuntu packages over again? i have the disk, i just dont want to risk screwing up GRUB  and loosing my files

---

### Post by heimo on 2005-08-13
[QUOTE=Digitallysick]well i think i somehow uninstalled Libc6[/QUOTE]

Ouch. Not recommended.

You can try to  ```
sudo dpkg -i /var/cache/apt/archives/libc6_*
``` 
And then the same thing for all the other packages that were removed.

These are your friends too:
 ```
sudo apt-get install -f
sudo dpkg --configure -a

``` 

One thing you could try before the stuff above, is: ```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status_mybackup
sudo mv /var/lib/dpkg/status-old /var/lib/dpkg/status

```

---

### Post by Digitallysick on 2005-08-16
sudo dpkg --configure -a
dpkg: parse error, in file `/var/lib/dpkg/status' near line 6006 package `python2.4-dbus':
 missing version

i think dpkg is messed up??

---

### Post by heimo on 2005-08-16
[QUOTE=Digitallysick]sudo dpkg --configure -a
dpkg: parse error, in file `/var/lib/dpkg/status' near line 6006 package `python2.4-dbus':
 missing version

i think dpkg is messed up??[/QUOTE]

Did you try to move the status-old over status file?

---

