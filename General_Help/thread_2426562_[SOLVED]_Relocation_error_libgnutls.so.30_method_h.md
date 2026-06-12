---
title: "[SOLVED] Relocation error libgnutls.so.30 method http has died unexpectedly error 127"
date: 2019-09-10
forum: General Help
---

### Post by sudoranger on 2019-09-10
[IMG]https://i.ibb.co/sP09Jvk/95-B260-C5-7-FD1-4121-824-C-0-FF455026-CB1.jpg[/IMG]

Just updated my Ubuntu 18.04.3 a few minutes ago and my pc died. I reformatted and reinstalled a fresh one but still getting this problem. Sucks, lucky for me I have a separate partition for /home perhaps this is an upstream issue because I saw a workaround about dpkg some libraries from debian repo in askubuntu but I cant reply there it needs 50 reputation to comment!

Edit:

I think this has been fixed today. After tracking multiple bug reports, you can find more info from the following links.

[https://bugs.launchpad.net/ubuntu/+source/libidn2/+bug/1843507](https://bugs.launchpad.net/ubuntu/+source/libidn2/+bug/1843507)
[https://github.com/oerdnj/deb.sury.org/issues/1247](https://github.com/oerdnj/deb.sury.org/issues/1247)

---

### Post by detallado on 2019-09-10
This seems to be a temporary workaround, a problem with a bad library, I guess we'll have to wait until Ubuntu releases the official fixed upgrade.

Solution:
[https://bugs.launchpad.net/ubuntu/+source/libidn2/+bug/1843507/comments/4](https://bugs.launchpad.net/ubuntu/+source/libidn2/+bug/1843507/comments/4)

wget [http://mirrors.kernel.org/ubuntu/pool/main/libi/libidn2/libidn2-0_2.0.4-1.1build2_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/main/libi/libidn2/libidn2-0_2.0.4-1.1build2_amd64.deb)
sudo dpkg -i libidn2-0_2.0.4-1.1build2_amd64.deb
sudo apt-mark hold libidn2-0

---

### Post by sudoranger on 2019-09-11
> **detallado said:**
> This seems to be a temporary workaround, a problem with a bad library, I guess we'll have to wait until Ubuntu releases the official fixed upgrade.

Solution:
[https://bugs.launchpad.net/ubuntu/+source/libidn2/+bug/1843507/comments/4](https://bugs.launchpad.net/ubuntu/+source/libidn2/+bug/1843507/comments/4)

wget [http://mirrors.kernel.org/ubuntu/pool/main/libi/libidn2/libidn2-0_2.0.4-1.1build2_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/main/libi/libidn2/libidn2-0_2.0.4-1.1build2_amd64.deb)
sudo dpkg -i libidn2-0_2.0.4-1.1build2_amd64.deb
sudo apt-mark hold libidn2-0

Thanks for the info! It seems that it only affects those having PHP installed from the sury.org repository. I tried again with a new fresh install but this time without ondrej's PHP and I don't have this issue anymore.

---

### Post by peternormann on 2019-09-11
> **sudoranger said:**
> Thanks for the info! It seems that it only affects those having PHP installed from the sury.org repository. I tried again with a new fresh install but this time without ondrej's PHP and I don't have this issue anymore.

This thread saved my day. 

Using Linux Mint 19.2 Cinnamon I couldn't even launch a terminal or most other applications and I  was getting the exact same issues: Unable to boot properly having network manager, cups and other services fail. 

Booting from live usb to get the [COLOR=#000000]*libidn2-0_2.0.4-1.1build2_amd64.deb file and then rebooting the system and installing it as per *[/COLOR]https://bugs.launchpad.net/ubuntu/+source/libidn2/+bug/1843507/comments/4 [COLOR=#000000]*using a terminal (ctrl-alt-F5) fixed everything!*[/COLOR]

However, I did not have PHP installed from the sury.org repository, but I recently (as in this week) upgraded to 7.3 using ondrej's repository.

Thanks a bunch.

---

