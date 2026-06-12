---
title: "just did a fresh install on my home partition... missing system clock"
date: 2013-10-30
forum: General Help
---

### Post by Primefalcon on 2013-10-30
as you can see from the image below (click for bigger version) after I did a fresh install of my root partition I have no system clock.... help please
[[IMG]https://dl.dropboxusercontent.com/u/1212637/2013/Screenshot%20from%202013-10-30%2014%3A13%3A39%7Ethumbnail.jpg[/IMG]]("https://dl.dropboxusercontent.com/u/1212637/2013/Screenshot%20from%202013-10-30%2014%3A13%3A39.png")

---

### Post by Shadius on 2013-10-30
Maybe the clock isn't installed. Have you gone into the settings to check the date/time settings? If it's not there, maybe you need to install it.

Try:
```
sudo apt-get install indicator datetime
```

---

### Post by Primefalcon on 2013-10-30
```
[brad@lady:~ ] $ sudo apt-get install indicator datetime
[sudo] password for brad: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package indicator
E: Unable to locate package datetime
[brad@lady:~ ] $ sudo apt-get install indicator-datetime
Reading package lists... Done
Building dependency tree       
Reading state information... Done
indicator-datetime is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-generic linux-image-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
[brad@lady:~ ] $ 

```

---

### Post by Primefalcon on 2013-10-30
I ran ```
 sudo apt-get --reinstall install indicator-datetime
```, tis working now thanks for putting me onto the proper package :D odd though that after a fresh install of the root partition that this was broken.....

---

