---
title: "VMware vmplayer can't run"
date: 2015-01-02
forum: General Help
---

### Post by dallase1 on 2015-01-02
When I try to run Vmware Player I get a error message that modules need to be compiled before I can run Vmplayer it lists the name of a file or modules and has a option to browse for the files and when I click browse I can see a folder with the name of the module exactly as the program is asking for it and when I select that folder and then click load it says "C file headers matching your running  kernel were not found".

I attached a screen snap shot of the error message.

How do I fix this problem?

Thanks

---

### Post by TheFu on 2015-01-03
I don't use VMware. However, all hypervisors need a driver that extends the kernel and it is kernel  version specific.  In my experience, the installation instructions always say what the prerequisites are to the installation. Did you follow those from the VMware download website?  I googled and found this: [https://help.ubuntu.com/community/VMware/Player](https://help.ubuntu.com/community/VMware/Player)

Also, that error message is pretty clear - "C file headers matching your running kernel were not found".
There is a meta-package for those - have you installed it?

Most people seem to run VirtualBox instead of VMware Player for desktop-on-desktop virtualization. You'll find more help with that tool, I'd guess.

BTW, every time a new kernel is installed on your system, you'll need to rebuild the VMware Player drivers, so take careful notes and you may want to script this stuff to make it faster.

---

### Post by sammiev on 2015-01-03
This is the way I did mine and only ever had to do it once as it will auto build on each new kernel. Hope [this]("https://www.howtoforge.com/how-to-install-vmware-player-on-ubuntu-11.04-linux-mint-11") helps.

---

### Post by TheFu on 2015-01-03
Falco does a good job with instructions.

It is best to install the header metapackage, not any specific version - 
Run **uname -r** to determine which kernel type is installed. Headers for your running kernel are needed.

  [LIST]
[*]  {something}-generic-pae = sudo apt-get install linux-headers-generic-pae
[*]    {something}-generic = sudo apt-get install linux-headers-generic
[*]    {something}-server = sudo apt-get install linux-headers-server
[/LIST]

Only 1 of needs to be installed, but it needs to be the correct version.

---

### Post by sammiev on 2015-01-03
> **TheFu said:**
> Falco does a good job with instructions.

It is best to install the header metapackage, not any specific version - 
Run **uname -r** to determine which kernel type is installed. Headers for your running kernel are needed.

  [LIST]
[*]  {something}-generic-pae = sudo apt-get install linux-headers-generic-pae
[*]    {something}-generic = sudo apt-get install linux-headers-generic
[*]    {something}-server = sudo apt-get install linux-headers-server
[/LIST]

Only 1 of needs to be installed, but it needs to be the correct version.

I only ever had to install VMplayer once as it been solid. Forgot how I did it back then but was able to find it after a few searches.

---

### Post by dallase1 on 2015-01-04
I figured it out I found a video on Youtube that showed how to install Vmplayer by dragging the install Bundle File into a Terminal an typing SUDO SH in front of what was displayed in the terminal window and it Uninstalled the corrupted install of Vmware and then reinstalled it properly and now I have XP Running in Vmplayer.

---

### Post by sammiev on 2015-01-05
Glad it all worked out for you. :)

---

### Post by cetun on 2015-01-08
Here you have instructions on how to install VMware Player in Ubuntu 14.04: [http://vmware-player.com/install-vmware-tools-in-linux/](http://vmware-player.com/install-vmware-tools-in-linux/)

---

