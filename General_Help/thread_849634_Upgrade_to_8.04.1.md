---
title: "Upgrade? to 8.04.1"
date: 2008-07-04
forum: General Help
---

### Post by benign on 2008-07-04
How are you supposed to upgrade to 8.04.1 from 8.04? When I run the update manager it doesn't tell me anything about the updated version.

---

### Post by overdrank on 2008-07-04
> **benign said:**
> How are you supposed to upgrade to 8.04.1 from 8.04? When I run the update manager it doesn't tell me anything about the updated version.

HI and you can use the command ```
lsb_release -a

```
And the output should look
Distributor ID:	Ubuntu
Description:	Ubuntu 8.04.1
Release:	8.04
Codename:	hardy

---

### Post by lukjad on 2008-07-04
What is 8.04.1? Is it the preview of Intrepid Ibex?
*Edit:*
Will this command work on Ubuntu Studio?

---

### Post by benign on 2008-07-04
It's the maint release that came out today or yesterday. If you get the newest ISO it is dated for the 2nd of July. 

I'm not sure how these maintenance releases work... I get the same output when using the command that the poster above mentioned.

I've burned it to a CD so I'm just going to do a fresh install later since I screwed up some libs or something and now wine won't run anything even after reinstalling it.

[https://lists.ubuntu.com/archives/ubuntu-announce/2008-July/000112.html](https://lists.ubuntu.com/archives/ubuntu-announce/2008-July/000112.html)

[http://releases.ubuntu.com/8.04.1/](http://releases.ubuntu.com/8.04.1/)

---

### Post by grinias on 2008-07-05
I think that I already have 8.04.1, by normally updating packages as were come available. The output of 
```
lsb_release -a
```
> 
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 8.04.1
Release:        8.04
Codename:       hardy


In fact, I get the same output in a wubi 8.04 installed kubuntu system. So, no upgrade of wubi to 8.04.1 is either needed.

---

### Post by philinux on 2008-07-05
If you've been keeping your system up to date then you will have the .1 release.

[https://lists.ubuntu.com/archives/ubuntu-announce/2008-July/000112.html](https://lists.ubuntu.com/archives/ubuntu-announce/2008-July/000112.html)

---

