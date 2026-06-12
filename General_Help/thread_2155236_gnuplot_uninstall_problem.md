---
title: "gnuplot uninstall problem"
date: 2013-06-17
forum: General Help
---

### Post by pouya16 on 2013-06-17
Hi there ... 
I had installed gnuplot with synaptic package manager but now when I go there for uninstalling It will crash and don't work anymore ! 

I already use this solution : 

apt-get -f install gnuplot

but terminal says : 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
gnuplot is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 gfortran-4.4 : Depends: gcc-4.4-base (= 4.4.3-4ubuntu5.1) but 4.4.7-3 is to be installed
                Depends: gcc-4.4 (= 4.4.3-4ubuntu5.1) but it is not going to be installed
                Depends: libgmp3c2 but it is not going to be installed
 libmpfr1ldbl : Depends: libgmp3c2 (>= 4.2.dfsg-1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

could u guys help me please  ?

---

### Post by Cheesehead on 2013-06-18
> **pouya16 said:**
> ```
gfortran-4.4 : Depends: gcc-4.4-base (= [COLOR="#FF0000"]4.4.3-4ubuntu5.1[/COLOR]) but [COLOR="#FF0000"]4.4.7-3[/COLOR] is to be installed
```

One of those is from Lucid, the other is too new for Saucy. You seem to have mixed releases, or added an incompatible PPA, in your /etc/apt/sources.list

Edit your /etc/apt/sources.list to clean it up to a single release. Remove (or comment out) PPAs and other releases.
If you need help, post your /etc/apt/sources.list here.

Then, 
run "sudo apt-get clean" to purge your locally-stored package cache,
run "sudo apt-get update" to refresh your current-package lists,
and run "sudo apt-get upgrade" to test that the package manager is working properly by installing same-release updates.

---

