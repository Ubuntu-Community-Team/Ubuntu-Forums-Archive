---
title: "Upate-manager via CLI"
date: 2007-05-24
forum: General Help
---

### Post by dcooper on 2007-05-24
Hello, 

  I was wondering (and I've searched a little) is there a way to run "update-manager" remotely via the command line? If not how on earth do you grab updates (security and otherwise) remotely (especially on a headless system).  

 Thanks,

 D.

---

### Post by loathsome on 2007-05-24
> **dcooper said:**
> Hello, 

  I was wondering (and I've searched a little) is there a way to run "update-manager" remotely via the command line? If not how on earth do you grab updates (security and otherwise) remotely (especially on a headless system).  

 Thanks,

 D.

Can't you just run something like ```
# apt-get upgrade -y
```

.. ?

---

### Post by ruy_lopez on 2007-05-24
```
sudo apt-get update
```
followed by:
```
sudo apt-get upgrade
```
first command updates package lists, the second does the upgrade, if any packages have updated

---

### Post by loathsome on 2007-05-24
Yeah, and the -y parameter updates the system without asking for a confirmation.

---

### Post by dcooper on 2007-05-24
So basically the apt-get update / apt-get upgrade command set is what's going on behind the scene with the GUI "Update-Manager"?

If thats the case; then In the situation where I may only want certain updates, say there's 5 updates but I only want 2 of them will the "apt-get upgrade" ask me in succession Y/N for each package? (if I don't use the -y argument)

I appreciate the help.

Take care,

D.

---

### Post by loathsome on 2007-05-24
Hm.

You could to something like this ```
sudo apt-get upgrade -d
``` (download only) and then install manually afterwards.

---

### Post by dcooper on 2007-05-25
Well it seems that does pretty much what I wanted. ```
apt-get upgrade 
```doesn't seem to have switches to support selecting or deselecting the "upgrades" like in update-manager. However, if you use the -d and then install from /var/cache/apt/archives by hand (where the files are downloaded) you can pick and choose individual packages. 

I know ```
aptitude
``` can perform the apt-get update functions etc and install new packages, but from what I've seen in aptitude (thus far) you would have to browse through the categories and pick each one. 

Either way, it's a very nice system for remote updates. Thanks for the help.

---

### Post by mcduck on 2007-05-25
> **ruy_lopez said:**
> ```
sudo apt-get update
```
followed by:
```
sudo apt-get upgrade
```
first command updates package lists, the second does the upgrade, if any packages have updated

In addition, if you want full update, allowing also installing of new packages, use 'sudo apt-get dist-upgrade'. Normal upgrade only upgrades packages you already have installed, but if a package has some new dependency the upgrade is held back.

---

