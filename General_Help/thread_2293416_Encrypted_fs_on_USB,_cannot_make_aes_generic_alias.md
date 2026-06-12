---
title: "Encrypted fs on USB, cannot make aes_generic alias"
date: 2015-09-04
forum: General Help
---

### Post by timothylegg on 2015-09-04
I am following the document:


[https://help.ubuntu.com/community/EncryptedFilesystemsOnRemovableStorage](https://help.ubuntu.com/community/EncryptedFilesystemsOnRemovableStorage)


to create an encrypted filesystem on a removable device.  All goes fine until the step of:


# sudo modprobe aes
modprobe: ERROR: could not insert 'padlock_aes': No such device


Hardly a surprise, the document warned me of bug #206129.  It instructs us to perform a workaround to enter in /etc/modprobe.d/aliases and add the line


alias aes aes_generic


But I had a sense of impending doom when I noticed that the file the I am to append to did not exist.  Particularly exasperating is that there is no comments section at the bottom of that page where users can warn people like us about pages being obsolete or suggest corrections, so lacking that, I come here.


It turns out that adding that line did not change anything.  I still got that error.  Hoping that it wouldn't matter, I proceeded anyway and the filesystem is an unmountable dud.


So how do I add this alias on 14.04?


If anybody of you out there can edit that help.ubuntu.com wiki, hopefully you can update it and make it correct again.

---

### Post by Ray_Walker on 2015-10-22
Same problem here, on Vivid.  

Utterly incredible that such a critical bug exists for eight years ...

cat /proc/cpuinfo ...

flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm ida arat epb pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase smep erms xsaveopt

What am I missing?

---

