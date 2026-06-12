---
title: "lubuntu 1gb ram requirement, but my laptop has 971 mb of ram. Anyway to bypass?"
date: 2018-08-31
forum: General Help
---

### Post by ashtongameryt on 2018-08-31
Read the title, please, Windows XP runs SO bad. I really hope someone knows a way to do this.

It should be able to run fine even with less then 1GB of RAM. If I can run it fine, why is it stoping me from installing it?

---

### Post by deadflowr on 2018-08-31
What does it say?
I for one have never seen any hard set limit to the amount of RAM needed on any version of Ubuntu, though less ram would be noticeable as it'll load the installer slow.
(and the less ram the slower the loading, the much slower the loading)
And things will hang, and such but it's never stopped the installation because of that.

Are you sure it's RAM and not the required storage space (hard drive space) needed?
If that does not meet the minimum requirements, the install will fail and/or be blocked from installing.

---

### Post by ashtongameryt on 2018-08-31
It has all the requirements, but I only have like 20MB ram less then 1GB. Trying to force install it right now.

---

### Post by geofftf on 2018-09-01
Having a little less space than 1 GB should not be a problem. Precisely what version are you attempting to install, and precisely what have you done to install it. Precisely how did the installation fail? Did you get an error message? You can still download Lubuntu 14.04, which has a minimum requirement of 128 MB of RAM.

---

### Post by SignedAdam on 2019-03-05
Open up terminal 

Type : cd /etc/calamares/modules

You should be now at that directory 

type : sudo chmod a+rwx welcome.conf

Now you should have permission to edit the ram block file, who ever  implemented this block should lose there job

Type : featherpad welcome.conf

Should open the file and now change the 1 to a 0 next to requiredram 

Then press files save and open the installer again, 

This is how I bypassed the ram limit, and I’m a windows user... sad times

---

