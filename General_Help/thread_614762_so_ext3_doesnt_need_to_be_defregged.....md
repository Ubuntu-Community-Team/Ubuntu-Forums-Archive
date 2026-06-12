---
title: "so ext3 doesnt need to be defregged...."
date: 2007-11-16
forum: General Help
---

### Post by Choad on 2007-11-16
but just how good is it? i've noticed my laptop getting a bit slow lately. is this just gutsy getting a little bloated (:() or is it coz my home partition is choc full and potentially fragmented?

it's ext3, 70 gig, of which 64 gig is used. "2.9 gig available"

i wouldnt have thought it would impede the performance of my machine much, seeing as all programs are on the root partition which is only 32% full (and therefor shouldnt be fragmented at all)

any tests i can run to see how fragmented things are getting?

---

### Post by kellemes on 2007-11-16
You don't need to defragment.. and as far as I know there aren't any tools that can do this without serious risks.
Maybe you should indeed clean you /home.. Try to leave about 10% of disks unused.

---

### Post by por100pre1 on 2007-11-16
Try removing your downloaded deb packages, that should give you some good free space:

```
sudo apt-get clean
```

---

### Post by Choad on 2007-11-16
> **por100pre1 said:**
> Try removing your downloaded deb packages, that should give you some good free space:

```
sudo apt-get clean
```
why on earth would they be in my home dir tho?

---

### Post by minus198 on 2007-11-16
When you do "sudo apt-get install <program>" the .deb file is saved on your computer. If you don't do "sudo apt-get clean" those files will eventually take a lot of space...

---

### Post by por100pre1 on 2007-11-16
> **Choad said:**
> why on earth would they be in my home dir tho?

Oh, my bad! That won't add more space to a separate /home partition. **You should resize your partitions.**

---

### Post by minus198 on 2007-11-16
> **por100pre1 said:**
> Oh, my bad! That won't add more space to a separate /home partition. **You should resize your partitions.**


Didn't notice that he hade a separate /home dir either :p

---

