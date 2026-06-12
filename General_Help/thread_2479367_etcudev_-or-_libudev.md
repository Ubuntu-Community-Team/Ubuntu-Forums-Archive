---
title: "/etc/udev -or- /lib/udev"
date: 2022-09-22
forum: General Help
---

### Post by rebeltaz on 2022-09-22
So, I bought a Huion drawing tablet. It is supposed to be compatible with Linux, but when I go to install the drivers, I get an error: "cp: cannot create regular file '/usr/lib/udev/rules.d/20-huion.rules': No such file or directory". whereis shows that udev on my system is at /etc/udev and /lib/udev. I contacted Huion and they told me that Ubuntu 18.04 isn't supported and that I needed to upgrade to 20. I don't want to. Since this is just a install script, I can change the location of udev to see if it will work, but I'm not sure which one to use. Any ideas? 

I've included the install.sh as a text file in case it helps to see it. Any advice (other than upgrade) would be really great!

---

