---
title: "Unable to locate package from repository"
date: 2016-10-24
forum: General Help
---

### Post by andrea-c on 2016-10-24
Hi all
I'm trying to install megacli for my megaRAIDsas card installed on a supermicro running ubuntu 14.04

I've added the repository

```
# Added repository for RAID controllers
deb-src http://hwraid.le-vert.net/distrib trusty main
```

with ```
 nano /etc/apt/sources.list
```

and saved everything.

Then I type
```
apt-get update
``` and it works fine but when I run
```
sudo apt-get install megacli megactl megaraid-status
```

My terminal output
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package megacli
E: Unable to locate package megactl
E: Unable to locate package megaraid-status
```

I'm following the steps [here]("http://hwraid.le-vert.net/wiki/LSIMegaRAIDSAS") and [here]("http://www.linuxcat.org/showthread.php?tid=68")

Am I doing something wrong?

[URL="http://www.linuxcat.org/showthread.php?tid=68"]
[/URL]

---

### Post by Bucky Ball on 2016-10-24
*Thread moved to **General Help**.*

Welcome. Check 

```
nano /etc/apt/sources.list
```

... and make sure the repo is still there as you should have added the repository by opening the file as admin with:

```
**sudo** nano /etc/apt/sources.list
```

... and closing and saving the file correctly. You should also be running:

```
**sudo** apt-get update
```

---

### Post by deadflowr on 2016-10-24
You only have the source repository added.
The package won't exist there as a deb file, only source.
Change the entry from deb-src to just deb and then the packages should show.

deb-src, for the record, means source files for debian packages.

---

### Post by andrea-c on 2016-10-25
Hi all thanks for the answers

Yes my bad, I forget to type the exact commands that I did, here

This is the extract from the sources.list

> ## Added repository for RAID controllers
deb-src [http://hwraid.le-vert.net/distrib](http://hwraid.le-vert.net/distrib) trusty main

all with sudo and properly saved.

When I run > **sudo** apt-get update

it actaully says:

>   404  Not Found [IP: 195.154.194.248 80]
W: Failed to fetch [http://hwraid.le-vert.net/distrib/dists/trusty/main/source/Sources](http://hwraid.le-vert.net/distrib/dists/trusty/main/source/Sources)  404  Not Found [IP: 195.154.194.248 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.


Does that mean that the repo is down?

---

### Post by howefield on 2016-10-25
Shouldn't *distrib* be replaced with ubuntu in the sources line ?

[http://hwraid.le-vert.net/wiki/DebianPackages](http://hwraid.le-vert.net/wiki/DebianPackages)

---

### Post by Bucky Ball on 2016-10-25
You didn't read this?

> **deadflowr said:**
> You only have the source repository added.
The package won't exist there as a deb file, only source.
_*Change the entry from deb-src to just deb*_ and then the packages should show.

---

### Post by howefield on 2016-10-25
> **Bucky Ball said:**
> You didn't read this?

Why, what don't you understand ?

---

### Post by Bucky Ball on 2016-10-25
OP was advised:

> Change the entry from deb-src to just deb and then the packages should show.

Unless my eyes are playing tricks or I'm missing something you could point out, the line used shows deb-src, not just deb.

---

### Post by andrea-c on 2016-10-26
> **Bucky Ball said:**
> You didn't read this?

I see sorry my bad.
That actually improved things a bit but I'm still getting 

> W:  Failed to fetch  [http://hwraid.le-vert.net/distrib/dists/trusty/main/binary-amd64/Packages](http://hwraid.le-vert.net/distrib/dists/trusty/main/binary-amd64/Packages)   404  Not Found [IP: 195.154.194.248 80]

W: Failed to fetch  [http://hwraid.le-vert.net/distrib/dists/trusty/main/binary-i386/Packages](http://hwraid.le-vert.net/distrib/dists/trusty/main/binary-i386/Packages)   404  Not Found [IP: 195.154.194.248 80]



and those I think are the 32bit and 6bit repository upstream links, am I correct?

---

### Post by howefield on 2016-10-26
> **Bucky Ball said:**
> OP was advised:
Ok, just that it was unclear whom your retort was aimed at.

---

### Post by Bucky Ball on 2016-10-26
> **howefield said:**
> Ok, just that it was unclear whom your retort was aimed at.

All good. I should have chucked an appropriate quote in from OP to make it clear. The 'changing deb-src to deb' idea unfortunately didn't get us far anyhoops. :|

---

### Post by steeldriver on 2016-10-26
It looks to me like **both steps are necessary**:

1. change the word **distrib **in the URL to the name of the actual distribution, i.e. [hwraid.le-vert.net/**ubuntu**/dists/trusty/main/binary-amd64/Packages]("http://hwraid.le-vert.net/ubuntu/dists/trusty/main/binary-amd64/Packages")

2. add it as a **deb** (rather than deb-src) if you want to install the binary package i.e.
```

**[COLOR=#0000ff]deb[/COLOR]** http://hwraid.le-vert.net/**[COLOR=#0000ff]ubuntu [/COLOR]**trusty main

```

---

### Post by andrea-c on 2016-10-27
Thanks Steeldriver that worked like a charm

---

### Post by Bucky Ball on 2016-10-27
Great news. Please mark the thread as solved from Thread Tools at the top of the page. This won't close the thread but will help others. Thanks. :)

---

