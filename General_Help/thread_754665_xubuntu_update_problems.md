---
title: "xubuntu update problems"
date: 2008-04-14
forum: General Help
---

### Post by Helios38 on 2008-04-14
Hello,


i am using Xubuntu 8.04 Hardy on a secondary hard drive (primary HD is running windows.) and things were working fine until today i saw a lot of updates. i open update manager and i learn that i cannot install all of the packages. i know my system does not need a partial upgrade, so i looked at the updates that were not installable.


they were some ubuntu updates, now what im curious about is why is xubuntu trying to install some ubuntu files?


should i let it be and install these updates? or should i uncheck all of the ubuntu updates?


one of the updates it wanted to install were ubuntu-core



why would it be doing this?

---

### Post by sekinto on 2008-04-14
Maybe both Ubuntu and Xubuntu use "ubuntu-core", seeing as Xubuntu is a derivative of Ubuntu.

If you are unsure you can look at your /etc/apt/sources.list file, if all the sources are Xubuntu you would not be getting a Ubuntu-only update.

What error do you get if you try this:
```
aptitude --upgrade
```

---

### Post by Helios38 on 2008-04-14
it does a bit of updating.


i will update using this then update what i can from update manager.

i'll post my results in the morning

---

