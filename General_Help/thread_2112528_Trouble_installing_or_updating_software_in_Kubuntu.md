---
title: "Trouble installing or updating software in Kubuntu 12.04"
date: 2013-02-05
forum: General Help
---

### Post by jhilp on 2013-02-05
I just installed Kubuntu 12.04, and I've been trying to install updates (with Muon Software Updater) or add software (with Muon Software Center). However, most of the time both programs fail to ask for a user password before installing and then an error comes up saying the operation failed because I didn't provide authentication, even though it didn't ask for a password. Any help is appreciated.

---

### Post by carl4926 on 2013-02-05
try

```
sudo apt-get update
```
then
```
sudo apt-get upgrade
```

---

### Post by L a r r y on 2013-02-05
> **carl4926 said:**
> try

```
sudo apt-get update
```
This command will call for your password and then update the system. That should get around the update issue with the gui tools.
> 

then
```
sudo apt-get upgrade
```
And I believe this will bring your OS up to the most recent release.

I like to see an explanation to go along with the instructions for the new reader who happens across a set of instructions like this.  

I count myself among those who need a reminder.:lolflag:

And carl4926 and others on the system with the knowledge, I appreciate your being there.  Thank you.

---

### Post by carl4926 on 2013-02-05
>  upgrade
           upgrade is used to install the newest versions of all packages
           currently installed on the system from the sources enumerated in
           /etc/apt/sources.list. Packages currently installed with new
           versions available are retrieved and upgraded; under no
           circumstances are currently installed packages removed, or packages
           not already installed retrieved and installed. New versions of
           currently installed packages that cannot be upgraded without
           changing the install status of another package will be left at
           their current version. An update must be performed first so that
           apt-get knows that new versions of packages are available.


The most recent release would need:
dist-upgrade

Along with changed sources....

---

