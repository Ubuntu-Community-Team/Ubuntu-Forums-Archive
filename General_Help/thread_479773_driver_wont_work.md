---
title: "driver wont work"
date: 2007-06-20
forum: General Help
---

### Post by michaelbmcgee on 2007-06-20
for a while i have had ubuntu feisty x86 on my pc and i got my netgear wg311v3 card to work with ndiswrapper. i followed this wiki [http://www.jimbo7.com/wiki/index.php?title=WG311v3_LINUX_WIKI](http://www.jimbo7.com/wiki/index.php?title=WG311v3_LINUX_WIKI) 

so i decided to reformat my hard drive and install ubuntu feisty x64 to take advantage of my processor. my problem is that i cant get the driver to work with ndiswrapper. i tried to follow this wiki  [http://nothingoutoftheordinary.com/?p=44](http://nothingoutoftheordinary.com/?p=44) . the driver wraps fine and the device is detected in ndiswrapper with ndiswrapper -l. the problem occurs when i run modprobe ndiswrapper.

root@michael-laptop:/home/michael#
root@michael-laptop:/home/michael# modprobe ndiswrapper

the terminal just kinda freezes like... "root@michael-laptop:/home/michael#" doesnt show up after i push enter. just a curser thingamajig. i can type but cant execute commands.

it should look like this
root@michael-laptop:/home/michael#
root@michael-laptop:/home/michael# modprobe ndiswrapper
root@michael-laptop:/home/michael#


also i get this sometimes
root@michael-laptop:/home/michael#
root@michael-laptop:/home/michael# modprobe ndiswrapper
Killed
root@michael-laptop:/home/michael#

any ideas? please help i need to get this working!!
thnx -michael

---

