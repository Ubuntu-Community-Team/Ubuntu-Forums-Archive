---
title: "how to get package list from another system?"
date: 2007-12-23
forum: General Help
---

### Post by davidpbrown on 2007-12-23
Not a critical problem and more out of curiousity..

My 64bit system lost it's motherboard and working from a 32bit laptop, I'm wondering if it's possible to grab the package list from the old drive.

If the system was live I'd do something like
sudo dpkg --get-selections > ./backup/package_list

but I'm expecting I can't boot a 64bit system directly on a 32bit laptop without complications.

Is there a way to hack the package list from the old system files?

---

### Post by p_quarles on 2007-12-24
I don't think it's possible to interact with the data on a hard drive at all unless it's connected to a working processor. Am I misunderstanding the question?

Anyway, if you can access the hard drive, you can certainly get this data. The fact that the broken machine was using 64 bits doesn't really matter, since the package names themselves don't indicate architecture (APT takes care of that for you). To create a slightly more useful file, though, you might want to use something like this:
```
sudo dpkg --get-selections | grep '[[:space:]]install$' | awk '{print $1}' > package_lis
```
That way, you'll only list packages that the system had installed, rather than all packages except those marked as "purged."

---

### Post by glantucan on 2007-12-29
And how would you get synaptic to read that list and install them?

Could I get this list from a feisty system and use it on a gutsy one?

Cheers

---

### Post by p_quarles on 2007-12-29
> **glantucan said:**
> And how would you get synaptic to read that list and install them?

Could I get this list from a feisty system and use it on a gutsy one?

Cheers
I don't know of a way to use Synaptic for that purpose, but here's what I do:
```
sudo apt-get update
cat package_list | xargs sudo apt-get install -y
```
That will attempt to use the terms from package_list (the file you created with the other command) to install the same packages. 

And yes, you can use a list from 7.04 on a 7.10 installation -- the only catch is that you'll get a few errors at first. You'll need to go into the text file and manually delete the packages which apt says are missing or deprecated. I've done this several times, and it's not as a bad as it sounds. You generally have to delete like six or seven items before the full installation starts running.

---

### Post by dagnabit dang doohickey on 2007-12-29
Rather than using:
```
cat package_list | xargs sudo apt-get install -y
```
which doesn't give the opportunity to inspect the install thats about to take place. You can use:
```
xargs -a package_list sudo apt-get install
```
which will behave as normal, asking for confirmation before proceeding with the install.

---

### Post by glantucan on 2007-12-29
Good enough :D

Thanks a lot both

---

