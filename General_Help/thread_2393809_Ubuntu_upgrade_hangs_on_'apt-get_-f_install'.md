---
title: "Ubuntu upgrade hangs on 'apt-get -f install'"
date: 2018-06-08
forum: General Help
---

### Post by Mathurin1968 on 2018-06-08
I have done something to my Ubuntu box and I'm not sure what... TBH I'm not even sure how I got here I've been looking at it for so long...

```
$ uname -r
4.4.0-127-generic
```
I have the following image header

```
flare@Flare:~$ sudo dpkg --list | grep linux-image
ii  linux-image-4.4.0-112-generic       4.4.0-112.135                             
ii  linux-image-extra-4.4.0-112-generic 4.4.0-112.135                             
flare@Flare:~$ sudo dpkg --list | grep linux-headers
ri  linux-headers-4.4.0-112             4.4.0-112.135                             
rH  linux-headers-4.4.0-112-generic     4.4.0-112.135 
```
When I try to run

```
$ sudo apt-get update; sudo apt-get dist-upgrade -y

```

everything looks OK and then it finishes with...

```
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-generic : Depends: linux-image-generic (= 4.4.0.127.133) but it is not installed
                 Depends: linux-headers-generic (= 4.4.0.127.133) but it is not installed
E: Unmet dependencies. Try using -f.
```

When I run

```
$ sudo apt-get -f install

```

it hangs on

```
Fetched 58.6 MB in 9s (6,401 kB/s)
(Reading database ... 62742 files and directories currently installed.)
Removing linux-headers-4.4.0-112-generic (4.4.0-112.135) ...
```

Is there anything I can do? Thanks!

*I seem to have plenty of free space

---

### Post by Bashing-om on 2018-06-08
Mathurin1968; Hello -

Give the package manager what it wants; and maybe it will go away :)
What results:
```

sudo apt install linux-image-generic-4.4.0.127
sudo apt install linux-headers-generic-4.4.0.127

```

reboot to see the effect .. and then show us:
```

dpkg -l | grep linux-

```
to see what else needs attention.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by Mathurin1968 on 2018-06-10
Thanks Bashing-om!  For the response,  this is what I get --


flare@Flare:~$ sudo apt install linux-image-generic--4.4.0.127
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package linux-image-generic--4.4.0.127
E: Couldn't find any package by glob 'linux-image-generic--4.4.0.127'
E: Couldn't find any package by regex 'linux-image-generic--4.4.0.127'

---

### Post by Bashing-om on 2018-06-10
Mathurin1968; ooopps -

Typo on my part :
should have only one dash:
```

sudo apt install linux-image-generic-4.4.0.127
sudo apt install linux-headers-generic-4.4.0.127

```


[INDENT][INDENT]silly lil dash
[/INDENT][/INDENT]

---

### Post by deadflowr on 2018-06-11
*Thread moved to **General Help***

---

