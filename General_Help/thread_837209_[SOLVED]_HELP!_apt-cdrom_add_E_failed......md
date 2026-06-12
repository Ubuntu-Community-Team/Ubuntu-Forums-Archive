---
title: "[SOLVED] HELP! apt-cdrom add E: failed....."
date: 2008-06-22
forum: General Help
---

### Post by beN..87 on 2008-06-22
fresh install of ubuntu 8.04 alternate cd

apt-cdrom add
E: Failed to mount cdrom

tried apt-cdrom add -a
tried apt-cdrom add -m

i also ticked the CD as a software source, still no luck

the strange thing is i have reinstalled and has worked sometimes, and not others

i am trying to add the cd i installed with, and it fails to fetch it - the cd integrity is fine

i have searched around for answers, and i'm stuck

can anyone help?

i need to install build-essential from cd as i have no internet connection until i can use make and build-essential

thanks in advance,

---

### Post by beN..87 on 2008-06-22
> **beN..87 said:**
> fresh install of ubuntu 8.04 alternate cd

apt-cdrom add
E: Failed to mount cdrom

tried apt-cdrom add -a
tried apt-cdrom add -m

i also ticked the CD as a software source, still no luck

the strange thing is i have reinstalled and has worked sometimes, and not others

i am trying to add the cd i installed with, and it fails to fetch it - the cd integrity is fine

i have searched around for answers, and i'm stuck

can anyone help?

i need to install build-essential from cd as i have no internet connection until i can use make and build-essential

thanks in advance,

well i've solved it on my own - for others who install a fresh ubuntu, and then can't add packages from the same cd you installed with-

sudo gedit /etc/fstab

change the device from /cdrom to /cdrom/

for some stupid reason the live CD sets it up wrong.... smart

bug report is here

[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/115536](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/115536)

---

