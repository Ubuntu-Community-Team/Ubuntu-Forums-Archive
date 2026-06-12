---
title: "vmware 6.0 &amp;&amp; vmi paravirtualization help!"
date: 2007-05-09
forum: General Help
---

### Post by &#1088;&#1086;&#1079;&#1086;&#1074;&#1099;&#1081; &#1082;&#1086;&#1090; on 2007-05-09
I'm install vmware 6.0 but can't enable "kernel paravirtualization" (VMI) checkbox in Virtual Machine settings.

Please help:

How to check for enabled vmi?
How to enabled vmi in vmware?

I'm use ubuntu 7.04 Feisty

---

### Post by erikb5 on 2007-05-11
First you need to know that the VMI Paravirt-ops are enable only in the i386 kernels and not in the x86-64.

To check if you're kernel has VMI support enabled
```

# grep VMI /boot/config-2.6.20-15-server

CONFIG_VMI=y

```

If you want to check that you have VMI running in you're kernel check the /proc/interrupts.

```

# grep VMI /proc/interrupts

0   74    IO-APIC-Edge            VMI-alarm

```

---

### Post by erikb5 on 2007-05-11
As for activating the VMware paravirtual kernel support in the Options\Advanced tab, I activated it prior to installing Ubuntu 7.04 Server (i386).

In addition, if I add the vga=0x317 framebuffer setting to the grub menu kernel settings on an VMI enable virtual machine, I have a problem with the console refreshing. It's unusable.

---

### Post by darwin_te on 2007-06-27
The paravirtual kernel support is available only when running Linux guest.  If you're running Windows guest, it is disabled.  Also your Linux guest kernel should have support for VMI.

---

### Post by tribaal on 2008-04-25
> First you need to know that the VMI Paravirt-ops are enable only in the i386 kernels and not in the x86-64.

Any idea why?

Cheers

- Trib'

---

