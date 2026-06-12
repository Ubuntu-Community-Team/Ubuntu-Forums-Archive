---
title: "Move from archive.ubuntu.com to ubuntu.com in sources.list"
date: 2016-10-09
forum: General Help
---

### Post by Jason_Hunter on 2016-10-09
I had to upgrade a system from 14.10 to 16.04. 

I had to change all the files in sources.list to archive.ubuntu.com.

When I went through all the systems 15.04 and 15.10 and then 16.04, I still see archive.ubuntu.com in the sources.list file. 

Is there no automated way to clean up all this?

Do I have to manually edit the file again?

---

### Post by deadflowr on 2016-10-09
The archives for all supported repos are always at archive.ubuntu.com.
What makes you think that would need to be changed?
What you change is not the address, but the codename (trusty, xenial, whatever that name is in whatever release you are running.)

---

### Post by Jason_Hunter on 2016-10-09
ok, my bad; I thought it was the word archive it added, but it was old-releases: 

sudo sed -i -re 's/([a-z]{2}\.)?archive.ubuntu.com|security.ubuntu.com/old-releases.ubuntu.com/g' /etc/apt/sources.list

All good; thank you

---

