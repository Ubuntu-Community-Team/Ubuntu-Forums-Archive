---
title: "Building Kernel and removing ALL old drivers"
date: 2008-01-11
forum: General Help
---

### Post by chrini on 2008-01-11
First of all, bare with me because I have a lot of questions:

I mainly need some clarification on what it means to "build the kernel" {also how to}; as well as how to locate and remove old drivers (read further for more details). **Computer specs below.**

To begin, I am trying to get my wireless working and, thus far, this involves removing the old ieee80211 driver and old ipw2200 driver and installing new ones (hopefully fixing the problem). But I think I have made a mess of things and would like to restart by removing the new files that I have just tried installing and going through the process again. Now the makefile for the ieee80211 driver has a function ". remove-old" that is suppose to remove ALL of the old files, however, I still find them in some of the /lib/modules/{3 different folders} area. And there is no such function for the ipw2200 driver. So how to I go about removing the old ipw2200 driver/files and the ieee80211 driver/files (if the function doesn't seem to be removing them).

Most importantly, how do I know if my kernel is capable:

"If that directory does not exist, or is empty, you likely need to 
install the kernel source packages for your distribution."


Also, this little blurb is from the installation instructions for the ieee80211 driver, could someone interpret it to me (i.e. what does it mean {esp. the \'uname -r\' part because it comes up a lot in the install instructions} and what happens if it isn't there {i.e. how/where do I get the 'kernel source packages'):

"The installation requires the compiled kernel sources or headers 
against the matching kernel.  These are typically found in:

        /lib/modules/\`uname -r\`/build

If that directory does not exist, or is empty, you likely need to 
install the kernel source packages for your distribution."

Dell Latitude D610
PRO/Wireless 2200BG Network Connection
Ubuntu 7.10

Thanks for the help and let me know if you need more info.:)

---

### Post by Washer on 2008-01-11
Ok first of all you really want to create a new kernel instead of messing with your current one. More on that in the tutorials below.

how do you know if your kernel is capable.. what version does the manual say? Compiling isn't a problem

uname -r gives you  your kernel version. Try running the command in a terminal.

Get the sources from synaptic, not from kernel.org. I think the package is linux-source or something like that

I've been using these 4 resources, mostly in that order.
[http://linuxhelp.150m.com/installs/compile-kernel.htm](http://linuxhelp.150m.com/installs/compile-kernel.htm)
[http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)
[http://ubuntuforums.org/archive/index.php/t-27673.html](http://ubuntuforums.org/archive/index.php/t-27673.html)
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

I recommend running through the tutorial once. It's very easy to uninstall the new kernel from synaptic. I suppose you'd be adding/removing modules in the menuconfig step after patching them in.

---

### Post by Washer on 2008-01-11
Yeah also you probably want the [networking]("http://ubuntuforums.org/forumdisplay.php?f=136") subforum

---

### Post by chrini on 2008-01-11
Thanks for the help. I'll take a look at these when I get a chance. Please give me more information if you come up with anything else. All the help I can get will be great. I'll let you know how it goes when I get a chance to try it out.

---

