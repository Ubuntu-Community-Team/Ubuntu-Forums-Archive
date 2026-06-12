---
title: "Upgrade to Edgy"
date: 2007-02-20
forum: General Help
---

### Post by luken8r on 2007-02-20
If this has been covered elsewhere, please point me to it, but Ive already looked

Im looking to upgrade from my 6.06 distro to 6.10, but I dont want to reformat. During the installation, can I forgo the partition/format option and keep my existing files?  I have a lot to back up and would  just like to reinstall the OS

---

### Post by Maestro23 on 2007-02-20
> **luken8r said:**
> If this has been covered elsewhere, please point me to it, but Ive already looked

Im looking to upgrade from my 6.06 distro to 6.10, but I dont want to reformat. During the installation, can I forgo the partition/format option and keep my existing files?  I have a lot to back up and would  just like to reinstall the OS

[https://help.ubuntu.com/community/EdgyUpgrades?highlight=%28upgrade%29](https://help.ubuntu.com/community/EdgyUpgrades?highlight=%28upgrade%29)

---

### Post by luken8r on 2007-02-20
Gracias. 
I already read through that page and it didnt mention the format/partitioner one way or another, so I thought Id ask.  
Lets say I do the package upgrade in this manner and my network fails to consecutively download the packages (Ive been having networking issues); what would happen?  Could I just  retry and it would pick up where it left off?
Would this package upgrade detect any new hardware that has previously been installed but not detected properly? Similar to a fresh install from a CD?

Im looking to upgrade from 6.06 to .10 mainly because of the above networking issues. I tried a new NIC and that wasnt detected as I would have liked. I wanted to go to 6.10 first to see if that would resolve any of my issues and if not, then see about getting some new  hardware in here.

---

### Post by david_2001 on 2007-02-20
> **luken8r said:**
> Gracias. 
I already read through that page and it didnt mention the format/partitioner one way or another, so I thought Id ask.  
Lets say I do the package upgrade in this manner and my network fails to consecutively download the packages (Ive been having networking issues); what would happen?  Could I just  retry and it would pick up where it left off?
Yes.
> Would this package upgrade detect any new hardware that has previously been installed but not detected properly? Similar to a fresh install from a CD?
Yes, potentially.  Depends on the hardware, of course.
> Im looking to upgrade from 6.06 to .10 mainly because of the above networking issues. I tried a new NIC and that wasnt detected as I would have liked. I wanted to go to 6.10 first to see if that would resolve any of my issues and if not, then see about getting some new  hardware in here.
I would actually suggest biting the bullet and not just reformatting but repartitioning as well, in order to put /home in it's own partition (I guess the issue is / and /home in the same partition).  Putting /home in a separate partition will make future upgrading less of a problem.

---

