---
title: "synaptic issues"
date: 2005-07-04
forum: General Help
---

### Post by hunteramor on 2005-07-04
I've been a linux user (though a very happy one!) for less than a week still, so the solution may be glaringly obvious, but I seem to be having trouble with synaptic.

Whenever I try to install a package, Synaptic insists that the following must be uninstalled first:

language-pack-en
language-pack-en-base
language-pack-zh
language-pack-zh-base
libc6-dev
libc6-i686
locales
lsb
ubuntu-base

I've spent a while this afternoon getting my language options exactly as I want them and a nice splashy grub set-up (for which i needed the libc6) so I'm aghast at the possibility of needing to uninstall what I just put together.  Why is it necessary to get rid of these to install anything new?

Also, synaptic is insisting that there are three broken packages, but "fixing" them doesn't seem to do anything since the next time I run synaptic, it still says they are broken.

This is my first time posting a question on this board, since I couldn't find anything helpful with a search (perhaps I overlooked a previous post).  Thanks for the help.

*UPDATE*
The "broken" packages are libc6-dev and libc6-i686 (which i wouldn't miss since I have a more recent version anyway, I think) and locales (not sure why that is broken)

---

### Post by arnieboy on 2005-07-04
follow [http://ubuntuguide.org](http://ubuntuguide.org) and add "backports" repositories to /etc/apt/sources.list
Open a terminal and type:
sudo apt-get update
followed by:
sudo apt-get upgrade

after all this is over open synaptic and check if u still have any broken packages.
All this assuming that u have an internet connection.

---

### Post by hunteramor on 2005-07-04
should have been more detailed - i'd tried that.  i'm going to go ahead and remove the packages synaptic suggests be removed with my fingers crossed and hope it doesn't undo everything i did this afternoon.

i'll keep you posted.

---

### Post by hunteramor on 2005-07-04
Okay, I think I've narrowed down the problem.

One package is requiring libc6_2.3.2.ds1-20, while another is requiring libc6_2.3.2.ds1-21.  When one library is installed, it insists that the packages depending on the other one are broken.  Seems like a catch-22 - any solution?

---

### Post by hunteramor on 2005-07-04
for any interested parties, the solution i found was to use the old library and version 0.1.3 of splashy, which seems to have done the trick.  multi-language support and splashy seem to be getting along fine now, although i'm sure i'm losing some functionality on the splashy end.

---

