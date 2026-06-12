---
title: "VMWare installation help"
date: 2007-03-05
forum: General Help
---

### Post by ntbutler on 2007-03-05
i am sorry if this is such a noob waste of a post, but its kinda important to me... I need to get vmware installed for uni...

I used synaptic to try to install vmware (the version in synaptic was 1.0.3 i think). That kept crashing in the final stages of the installation.
I then went onto the vmware site and downloaded the latest version (the tar file), extracted that and tried to run vmware-install.pl. i then ran into problems saying that there were still old versions of vmware, (even after 'removing' them), so i used synaptic to completely remove vmware.
Now the installation runs, but i have arrived at a stage where the installer is trying to create a vmmon module, for which it is trying to use the gcc compiler. My problem now is i need this:
> 
What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The default directory doesn't exist. I thought i may have found the suitable header files in /usr/lib/gcc/i486-linux-gnu/4.0.3/include/ , but when i try thin i get the message 
> The path "/usr/lib/gcc/i486-linux-gnu/4.0.3/include/" is an existing directory, but it does not
contain a "linux" subdirectory as expected.


any1 got any ideas? am i not giving it the right c header folder path? i seem to always, no matter what i put in (as long as it is a vaild directory) i seem to get the " but it does not
contain a "linux" subdirectory as expected." crap, even when i created the default directory and placed the c header files i had found in there...

thanx

---

### Post by ffxr on 2007-03-05
its looking fot the linux header source directory so that it can build a kernel module..
try poniting the script @ your linux headers src directory..

e.g /usr/src/linux-headers-2.6.17-11

---

### Post by AndyCooll on 2007-03-05
To install VMware, certain additional stuff needs installing first (build-essential, linux-headers etc etc)

This post [ HowTo: Windows (XP) on Ubuntu with VMWare Server]("http://www.ubuntuforums.org/showthread.php?t=183209") got me up and running with VMware Server (a souped up version of Vmware).

:cool:

---

