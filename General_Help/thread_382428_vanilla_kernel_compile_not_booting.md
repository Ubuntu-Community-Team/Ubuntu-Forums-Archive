---
title: "vanilla kernel compile not booting"
date: 2007-03-12
forum: General Help
---

### Post by gaillard on 2007-03-12
Hey everyone.

I have a little problem here.
I am trying to compile a kernel for some new hardware and I followed the howto in the howto section thats called master kernel thread.

kernel compiles fine, but on boot up it says
[21.746399] PCI: Cannot allocate resource region 0 at device 0000:00:00.0




Kernel alive
kernel direct mapping tables  up to 100000000 @ 8000-d000


any idea guys?

I used the same configuration from my working 2.6.17 kernel... Also this is the latest stable kernel 2.6.20.2 from kernel.org

Thanks everyone!

---

### Post by igknighted on 2007-03-12
Many times, even when using the old config, stuff isn't included that should be.  The most common is ext3 drivers being included as a module and not as part of the kernel, although it could be any number of things missing.  Try going through the config menus one by one to find the right settings.  Also, what guide are you using?  This one has worked for me and others, you might try it: [http://www.ubuntuforums.org/showthread.php?t=311158](http://www.ubuntuforums.org/showthread.php?t=311158)

---

### Post by gaillard on 2007-03-12
well how do i know which settings to try? 

I mean the reason I am compiling this kernel is for support for my new sound card which was having issues under 2.6.17

and the error was a pci one perhaps its related?

Would it take forever if I just enabled everything for the kernel to compile, just to see if it works?

---

### Post by gaillard on 2007-03-12
Ok it was some sata stuff not compiled in is why it wouldn't boot.

BUT that PCI message is still there.  Does anyone know what that is?

I have a feeling it is related to the soundcard as I am having trouble getting it working but I am positive the sound card works fine in windows.

Thanks for the help!

---

### Post by gaillard on 2007-03-12
Also when I run the xconfig I get this 
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0

is this related to the PCI error I am getting on boot?

Help me!
:confused: 
Thanks everyone

---

