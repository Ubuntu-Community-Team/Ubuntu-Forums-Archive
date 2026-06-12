---
title: "Running emulator in android studio ubuntu crouton"
date: 2017-05-20
forum: General Help
---

### Post by faarn on 2017-05-20
Hi,

I keep getting the following error when trying to set up an emulator in android studio in ubuntu crouton:

```
/dev/kvm does not exist.
```

I have run $ sudo kvm-ok and get:

[HTML]INFO: /dev/kvm does not exist
HINT:   sudo modprobe kvm_intel
INFO: Your CPU supports KVM extensions
INFO: KVM (vmx) is disabled by your BIOS
HINT: Enter your BIOS setup and enable Virtualization Technology (VT),
      and then hard poweroff/poweron your system
KVM acceleration can NOT be used
[/HTML]
When I run sudo modprobe kvm_intel I  get:

[HTML]modprobe: FATAL: Module kvm_intel not found.[/HTML]

It is also impossible for me to enter BIOS as my Chromebook doesn't have it.

Any help appreciated.

---

