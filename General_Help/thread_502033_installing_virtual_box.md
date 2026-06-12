---
title: "installing virtual box"
date: 2007-07-16
forum: General Help
---

### Post by ali780 on 2007-07-16
Hi
I want to install virtualbox on my Ubuntu 7.04.
If you can please give me some hint . Please if you can write the code for this job.

---

### Post by dreadlord_chris on 2007-07-16
> **ali780 said:**
> Hi
I want to install virtualbox on my Ubuntu 7.04.
If you can please give me some hint . Please if you can write the code for this job.

open up a terminal:
```

wget http://www.virtualbox.org/debian/innotek.asc
sudo apt-key add innotek.asc

```
now open up Synaptic Package Manager - click Settings > Repositories
then click New.
URI: [http://www.virtualbox.org/debian/](http://www.virtualbox.org/debian/)
Distrubution: feisty
Section(s): non-free 
click OK then click Reload
Virtualbox packages will now be available in Synaptic.

---

