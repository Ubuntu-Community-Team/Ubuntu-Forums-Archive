---
title: "Help Graphics Problem, no xserver after update"
date: 2013-01-23
forum: General Help
---

### Post by DrScum on 2013-01-23
I updated the nvidia graphics driver from the nvidia repos, now after rebooting i get a tty login screen. How do I go back to the good driver from the ubuntu restricted driver section? I need terminal commands, of course.

Thanks for your help.

---

### Post by dino99 on 2013-01-23
sudo apt-get purge nvidia-current nvidia-settings

note: deactivate the nvidia ppa via synaptic (if it exist)

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get update
sudo apt-get install nvidia-current nvidia-settings

---

### Post by DrScum on 2013-01-23
Thanks for your help. How do I deactivate the ppa, remember, I have only the command line available as of yet. The ultimate goal is to get my desktop back!

---

### Post by DrScum on 2013-01-24
After a several hour session I was able to solve the problem. Here the solution for the sake of people who might run into the same problem.

The problem originated from a NVIDIA driver update which caused the situation that the driver and the kernel module did not have the same version. This became ovious in the output from the "startx" command. 

With "dpkg -l | grep -i nvidia" you get a list with all NVIDIA drivers available. 

with " sudo apt-get remove --purge <drivername>" I purged every nvidia driver EXCEPT the NVIDIA-COMMON. After rebooting the system is back to normal. 

The most time I lost with following post saying that you can delete the drivers with this command: "sudo apt-get remove --purge nvidia* " or something like that. It didn't work, the drivers were not deleted as I found out with the "dpkg -l | grep -i nvidia" command after several hours of going back and forth.

In conclusion: this is the second serious problem I have after upgrading related to the NVIDIA drivers (see thread #2107905). Thus I am going to stick with the open source driver and dump the restricted ones.

---

