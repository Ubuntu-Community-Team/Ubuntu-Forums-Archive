---
title: "[SOLVED] All my Ubuntu difficulties... *sigh*"
date: 2008-06-07
forum: General Help
---

### Post by janvdl on 2008-06-07
Hello everyone :)

I am using Ubuntu 7.10 and I have the following problems.

1. How do I install something I have downloaded? Let's say I have downloaded MediaPlayer_12345.tar.gz ; Must i run this in the console somehow? 

2. I recently bought an Acer X193W monitor, but the driver for it isnt listed in the Screens and Graphics menu. I am currently using my old Philips monitor driver, but being a perfectionist, is there some way to change this? :lolflag:

Thanks in advance.

---

### Post by ivze on 2008-06-07
There is a standart sequence of actions to install something from a .tar.gz, .tar.bz2 or another archive:
1)extract it
2)open terminal, cd into the extracted directory
3)run './configure' - see what script says and instal this; continue until script exits normally
4)rum 'make'
5)run 'sudo make install'
(This is a manual of installing some app from sources)
In some cases, the sequence of actions may me different. Look for INSTALL or README text files in the archive and read them first.

---

### Post by Pjotr123 on 2008-06-07
Installing manually is the hard way. This is the easy way:
[http://ubuntutip.googlepages.com/installingapplications](http://ubuntutip.googlepages.com/installingapplications)

---

### Post by janvdl on 2008-06-07
Thanks for the replies, both the easy and manual way. I'll go try it out. :KS

---

### Post by Bubba64 on 2008-06-07
If you end up having to download a targz instead of getting the package in Debian which gdebi can install generally, extract the targz and before you go through the process of trying to install via the terminal look for a install file. Many targz files have a auto install that can be run or run through the terminal via a gui that appears when you click open the install file. Before you download anything as the previous posted link suggests look first in synaptic or add remove it may be in a repository, or you may just have to install a 3rd party like medibuntu or launchpad which are both reputable download sources

---

### Post by _DD_ on 2008-06-07
You screen doesn't really need the correct driver. As long as its running on the right resolution/refresh rate then that's fine.

On the other hand, your graphics card drivers are important. What graphics card and driver are you using?

---

