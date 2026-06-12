---
title: "I can't enable nvidia-gpu with nvidia-prime"
date: 2019-01-11
forum: General Help
---

### Post by redpheonix on 2019-01-11
I have a Inspiron 7559 laptop, with Nvidia 960M gpu. I installed Ubuntu  16.04 LTS, then installed nvidia drivers and bumblebee and it ran fine.  Recently, I upgraded to Ubuntu 18.04 ,installed nvidia 390  drivers,aaaand bumblebee doesn't work. After a bit of googling, I found  out that bumblebee doesn't play with nice with nvidia-390+ drivers.  Here's a link for reference- [https://bugs.launchpad.net/ubuntu/+source/bumblebee/+bug/1758243](https://bugs.launchpad.net/ubuntu/+source/bumblebee/+bug/1758243)

Anyway, I decided to follow the instructions listed here [https://float-middle.com/ubuntu-18-04-steam-and-nvidia-390/](https://float-middle.com/ubuntu-18-04-steam-and-nvidia-390/).  but I couldn't get bumblebee to work. I decided to ditch the whole  bumblebee thing and to go only with prime-select method of managing  graphics. However, when I do *prime-select nvidia* and reboot, then I  run *glxspheres* I see that it's still using intel drivers rather than the nvidia one.

I tried a number of things. I purged and reinstalled nvidia and  bumblebee several times. I switched back and forth between intel and  nvidia several times. I messed around with the grub file but to no  avail.   No matter what I do, I can't get the computer to use nvidia  graphics.

Currently, my computer doesn't have any bumblebee. It only has  nvidia-410 drivers. Also commands like *nvidia-smi* shows gpu  information, *lspci -vnn | grep '\''[030[02]\]* lists the GPU, *modinfo |  nvidia* lists a bunch of things, *prime-select query* lists nvidia; so I  don't have any issues here.

---

