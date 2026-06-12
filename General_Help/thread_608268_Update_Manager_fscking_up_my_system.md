---
title: "Update Manager fscking up my system"
date: 2007-11-09
forum: General Help
---

### Post by Locutus_of_Borg on 2007-11-09
I ran Update Manager last night, it stopped responding while still building the dependency tree, so I terminated the process after a while of grayed out nothing.  After that my CPU was running at 100% and causing a lot of lag, so I restarted.  This solved nothing so I shut down and restarted that way only to find my files system had errors in it and would not boot, giving me an 'exception Emask' error.  Eventually I got it working by using a live disk and running fsck on the offending partition.  Now I just tried to run Update Manager again, it  stopped working, then my computer froze up, and I had to ctrl-alt-backspace.  I once again got that exception Emask error, but was still able to login.

What the fsck?  Any ideas as to what might be the problem or how I can in the future check for updates?

I am using ubuntu 7.0.4 and kernel is 2.6.20-16-generic

Thanks.



Edit: Synaptic package manager just grays out, then closes after maxing out my CPU for a while as well.

Both utilities used to work fine.

---

### Post by Locutus_of_Borg on 2007-11-09
dpkg --configure -a 

let me at least start the update manager, but then I get this:
E: /var/cache/apt/archives/libcupsys2_1.2.8-0ubuntu8.1_i386.deb: failed in buffer_read(fd)
```
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/libcupsys2_1.2.8-0ubuntu8.1_i386.deb (--unpack):
 failed in buffer_read(fd): files list for package `openoffice.org-common': Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/libcupsys2_1.2.8-0ubuntu8.1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

```

...?

---

### Post by Maestro23 on 2007-11-09
> **Locutus_of_Borg said:**
> dpkg --configure -a 

let me at least start the update manager, but then I get this:
E: /var/cache/apt/archives/libcupsys2_1.2.8-0ubuntu8.1_i386.deb: failed in buffer_read(fd)
```
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/libcupsys2_1.2.8-0ubuntu8.1_i386.deb (--unpack):
 failed in buffer_read(fd): files list for package `openoffice.org-common': Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/libcupsys2_1.2.8-0ubuntu8.1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

```

...?

Go into /var/cache/archives and see if you can delete the libcupsys.deb

> sudo dpkg -P libcupsys2_1.2.8-0ubuntu8.1_i386.deb

Then try: 
> sudo apt-get update && sudo apt-get upgrade

---

### Post by Locutus_of_Borg on 2007-11-09
> none@blank:/var/cache/apt/archives$ sudo dpkg -P libcupsys2_1.2.8-0ubuntu8.1_i386.deb
dpkg: you must specify packages by their own names, not by quoting the names of the files they come in


Should I just rm the .deb file?

---

### Post by Maestro23 on 2007-11-09
> **Locutus_of_Borg said:**
> Should I just rm the .deb file?

Try just** libcupsys** as the package name.

---

### Post by Locutus_of_Borg on 2007-11-09
> none@blank:/var/cache/apt/archives$ sudo dpkg -P libcupsys
dpkg - warning: ignoring request to remove libcupsys which isn't installed.


:confused:

---

### Post by Maestro23 on 2007-11-09
> **Locutus_of_Borg said:**
> :confused:

Hmm. Can you delete all the .deb(s) from the directory.

> sudo dpkg -P *.deb

---

### Post by Locutus_of_Borg on 2007-11-09
I get the same thing about specifying packages by their own names.

---

### Post by Locutus_of_Borg on 2007-11-10
anything

---

