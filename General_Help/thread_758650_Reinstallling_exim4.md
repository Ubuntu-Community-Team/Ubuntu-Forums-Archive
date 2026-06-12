---
title: "Reinstallling exim4"
date: 2008-04-18
forum: General Help
---

### Post by jmvidalvia on 2008-04-18
I tried to reinstall exim-4.
I made: sudo apt-get remove -purge exim4
As /etc/exim4 folder was still there, with all the config sub-directories, I removed all of them, hopping that a new instalation would create them again.
I reinstalled exim4.
When trying to "sudo dpkg-reconfigure exim4-config", /etc/exim4 folder is not created and I can nor reconfigure It.
My question is: ¿how to make a new installation form zero?
I also tried "sudo  apt-get --reinstall install exim4" without success: I mean, exim4 is isntalled but config folder on etc is not there?
Any ideas?
Thanks a lot!

---

### Post by Tews on 2008-04-18
Go to the synaptic manager, enter eixim4 and mark it for removal.. when its complete, remark it for installation .... problem solved! :lolflag:

---

### Post by jmvidalvia on 2008-04-18
I am afraid my server has no graphical front end, so Synaptic won't be available :(

---

