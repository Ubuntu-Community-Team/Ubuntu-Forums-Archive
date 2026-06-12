---
title: "Dependency problems in Edgy"
date: 2006-11-03
forum: General Help
---

### Post by ubuntu-mike022465 on 2006-11-03
I just did a recent update to Edgy, and I'm getting these errors from synaptic

Cannot install all available updates

Some updates require the removal of further software. Use the function "Mark All Upgrades" of the package manager "Synaptic" or run "sudo apt-get dist-upgrade" in a terminal to update your system completely.

build-essential
dpkg-dev
g++
libc6-dev

and

g++:
  Depends: cpp (>=4:4.1.1-6ubuntu3) but 4:4.0.3-1 is to be installed
  Depends: gcc (>=4:4.1.1-6ubuntu3) but 4:4.0.3-1 is to be installed
 Depends: g++-4.1 but it is not going to be installed
 Depends: gcc-4.1 (>=4.1.1-2) but it is not installable

dpkg-dev:
  Depends: dpkg (>=1.13.20) but 1.13.11ubuntu6 is to be installed

Anyone have any idea how to rectify the situation?  I've done, sudo apt-get update and upgrade, but have had no success.

Any help would be greatly appreciated.

Thanks in advance.

M.

---

### Post by ~LoKe on 2006-11-03
```
sudo apt-get install build-essential gcc
```

---

### Post by ubuntu-mike022465 on 2006-11-03
michael@michael-desktop:~$ sudo apt-get install build-essential gcc
Reading package lists... Done
Building dependency tree... Done
gcc is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  build-essential: Depends: gcc (>= 4:4.1.1) but 4:4.0.3-1 is to be installed
                   Depends: g++ (>= 4:4.1.1) but 4:4.0.3-1 is to be installed
E: Broken packages


What next?

Thanks for responding so quickly.

---

### Post by ~LoKe on 2006-11-03
```
sudo apt-get clean
```
I *think* that'll remove all the packages downloaded from the repositories by apt-get, but I can't remember for sure.

---

### Post by ubuntu-mike022465 on 2006-11-05
Tried that too, but I'm still getting the dependency errors.  Not sure what to do next...


](*,)

---

### Post by LenzM on 2006-11-05
Are you sure you don't have old dapper repositories in your /etc/apt/sources.list

---

### Post by ubuntu-mike022465 on 2006-11-11
Sorry, my bad, it's Dapper that I'm having the trouble with.  Any suggestions?

M.

---

### Post by ubuntu-mike022465 on 2006-11-15
Bumpity bump bump.

:confused:

---

### Post by ubuntu-mike022465 on 2006-11-16
Someone from the forum staff might want to check out the adding a tag function, because I'm not able to add any tags to this thread.

M.

---

### Post by Nameless_one on 2006-11-16
Have you tried installing g++? 

Something like:

```
sudo aptitude install g++
```

([this](http://www.psychocats.net/ubuntu/aptitude) recommends aptitude instead of apt-get)

---

### Post by jimisdead on 2006-11-16
are you running a custom/non-dapper kernel?

---

### Post by ubuntu-mike022465 on 2006-11-16
Tried with apt-get and synaptic (I know, I know, one in the same :P), but no joy.  I still get dependency errors and cannot install g++. 

](*,)   ](*,)   ](*,)   :-k 

M.

---

### Post by ubuntu-mike022465 on 2006-11-16
No, just running stock kernel from the repositories, mind you it's a K7 kernel, but it's still stock.

M.

---

