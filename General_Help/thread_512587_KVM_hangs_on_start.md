---
title: "KVM hangs on start"
date: 2007-07-29
forum: General Help
---

### Post by Dragonslicer on 2007-07-29
When I try start kvm with
```
kvm -m 256 -cdrom /path/to/kubuntu-7.04-dvd-i386.iso -boot d .kvm/server.img
```
I get a BIOS screen that says Loading... (among other typical BIOS information), then just does nothing while using 100% of one of the cores on my CPU. The server.img disk image is newly created. I've been following [https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM), and everything up to this point has worked fine. My CPU is an Athlon AM2. Anybody else seen this issue before and have any ideas on what the problem is?

---

### Post by psynusoid on 2007-07-31
I had to append -no-kvm for the install on Intel and then after restarting was able to use kvm.
Have a look at [http://kvm.qumranet.com/kvmwiki/Guest_Support_Status]("http://kvm.qumranet.com/kvmwiki/Guest_Support_Status") to see the flags and workarounds for various OS.

---

### Post by Dragonslicer on 2007-07-31
The comment on that page says "Installation requires -no-kvm on Intel". What installation is it referring to? Installing KVM itself (which I did from the repository package), the guest OS (the step I'm having trouble with now), or something else? I have an AMD processor, but I can give it a shot. What downsides are there to that switch?

---

### Post by Dragonslicer on 2007-07-31
Tried adding -no-kvm to the command to start the VM, and I get the same thing.

---

### Post by e1geo on 2007-08-24
Same problem here on this processor:

AMD Athlon(tm) 64 X2 Dual Core Processor 4000+

just hangs with Loading...

Anyone?

---

### Post by Dragonslicer on 2007-08-26
As I discovered, the version of kvm in the Ubuntu repositories is very old. You should get the latest version from [http://kvm.qumranet.com/kvmwiki/Downloads](http://kvm.qumranet.com/kvmwiki/Downloads). [FONT="Courier New"]apt-get build-dep kvm[/FONT] should get all of the libraries you need to compile kvm.

---

