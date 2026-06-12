---
title: "[VMWARE] Location error"
date: 2005-04-09
forum: General Help
---

### Post by Lamber on 2005-04-09
The path "/usr/src/linux" is not an existing directory.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]


This error I get when i'm installing VMWARE. Does anyone know what the right location is?

Many thanks,

Lamber

---

### Post by joshmachine on 2005-04-09
You need to install the headers for the release of the kernel you have installed.  To find this out you can type

>> uname -r

to get the header you can apt-get install them,

>> sudo apt-get install linux-headers-`uname -r`

or select the appropriate package in synaptic.

Note: you'll also need gcc etc which if you don't have already you can get with

>> sudo apt-get install build-essential

After installation the vmware installer should just pick up the right place and not require anything but the defaults.

If it's still being stupid, the path to include can be found in /lib/modules/<<module release number>>/build/include

Cheers.

---

### Post by Lamber on 2005-04-09
[QUOTE=joshmachine]You need to install the headers for the release of the kernel you have installed.  To find this out you can type

>> uname -r

to get the header you can apt-get install them,

>> sudo apt-get install linux-headers-`uname -r`

or select the appropriate package in synaptic.

Note: you'll also need gcc etc which if you don't have already you can get with

>> sudo apt-get install build-essential

After installation the vmware installer should just pick up the right place and not require anything but the defaults.

If it's still being stupid, the path to include can be found in /lib/modules/<<module release number>>/build/include

Cheers.[/QUOTE]

Thanks, that did it  \\:D/ 

Now i can install XP on Ubuntu  :-P

---

