---
title: "uninstall evolution correctly"
date: 2008-06-05
forum: General Help
---

### Post by sprightlyone on 2008-06-05
hi 
  my 1st attempt resulted in removing my desktop
 so now i want to try again but need to know which files to remove &which ones to leave 
 i want to use thunderbid only &clean-up the unwanted installs
thanks lyle

---

### Post by abhiroopb on 2008-06-05
in the terminal:

sudo apt-get remove evolution --purge

and then do 

rm /home/<user>/.evolution

---

### Post by Tom--d on 2008-06-05
> **abhiroopb said:**
> in the terminal:

sudo apt-get remove evolution --purge

and then do 

rm /home/<user>/.evolution

After run..

```
sudo apt-get autoremove --purge
```

All Evolution will be gone.

---

### Post by Xiong Chiamiov on 2008-06-05
> **Tom--d said:**
> After run..

```
sudo apt-get autoremove --purge
```

All Evolution will be gone.
or the simpler
```

sudo aptitude purge evolution

```
which is easier to remember and takes care of autoremoving as well.

---

### Post by abhiroopb on 2008-06-05
should you be using aptitude to remove if u use apt-get to install?

---

### Post by Tom--d on 2008-06-05
I've had no problem with apt-get with uninstalling.

I've don't use aptitude (due to I remember apt-get), and really I don't know what aptitude does.. (hint hint) ;)

---

### Post by abhiroopb on 2008-06-05
aptitude is (AFAIK) another package manager, which seems to do a better OVERALL job of package managing. For example it provides alternate solutions if there are conflicting dependencies, etc (like how sometimes if you try and remove say libgpod, it automatically removes amarok, if you use aptititude it provides other solutions). However, this seems to require more overhead such as space so people seem to prefer apt-get.

---

### Post by Quintin Riis on 2008-06-05
> **abhiroopb said:**
> should you be using aptitude to remove if u use apt-get to install?

Yes, doesn't matter too much what you are using, apt-get, aptitude, synaptic, adept, or whatever... they all use APT backend.

---

### Post by Tom--d on 2008-06-05
Thank you :)
I see now. 

So if I wanted to remove a package but removing causes another package, which I want to keep, I need to use aptitude. apt-get just removes all needed packages for that package? (Wait wait, one more package word in there ;))

---

### Post by sprightlyone on 2008-06-05
[QUOTE=
and then do 

rm /home/<user>/.evolution[/QUOTE]
 i get this     rm:cannot /home/lyle/.evolution : is a directory

what is wrong now 
  
lyle

---

### Post by Quintin Riis on 2008-06-05
Read the manual page for rm, "man rm".

You need to use rm -r (recursive) to remove a directory.

---

