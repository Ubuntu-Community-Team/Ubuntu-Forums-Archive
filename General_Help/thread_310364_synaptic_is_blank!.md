---
title: "synaptic is blank!?"
date: 2006-12-01
forum: General Help
---

### Post by hazze on 2006-12-01
Hello!

A week ago i downloaded a .rpm file and i found out i needed some packages do install it. So for some reason i installed these packages:

rpm (4.4.1-9.1ubuntu0.1)

python-rpm (4.4.1-9.1ubuntu0.1)
smartpm (0.42-0ubuntu2)
smartpm-core (0.42-0ubuntu2)

libbeecrypt6 (4.1.2-5)
librpm4 (4.4.1-9.1ubuntu0.1)

And now my synaptic dosen't show a thing, and removing the packages by apt-get reove doesen't seem to work.

So how to delete these packages? Because i think this is the problem?

---

### Post by slimdog360 on 2006-12-01
try replacing your sources list with the one from the psychocats page. [http://www.psychocats.net/ubuntu/sources]("http://www.psychocats.net/ubuntu/sources")

If you didnt already know, you can install something called alien ```
sudo apt-get install alien
``` and it can convert rpm's into deb's via  ```
alien packagename 
```

---

### Post by hazze on 2006-12-01
> **slimdog360 said:**
> try replacing your sources list with the one from the psychocats page. [http://www.psychocats.net/ubuntu/sources]("http://www.psychocats.net/ubuntu/sources")

If you didnt already know, you can install something called alien ```
sudo apt-get install alien
``` and it can convert rpm's into deb's via  ```
alien packagename 
```

Yes I read about the alien after I installed the other packages.... 

It dosen't work to update the sources.list.


I think maybe the problem is that I checked in a box for using .rpm packages as default and for what I know synaptig uses deb så where can I correct this?

---

### Post by slimdog360 on 2006-12-01
did you change your sources list? it says how to do it on that link I gave you.

---

