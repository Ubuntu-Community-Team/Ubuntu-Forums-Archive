---
title: "Which module is Xubuntu seeking in error message upon boot?"
date: 2024-03-10
forum: General Help
---

### Post by johsal on 2024-03-10
First thing that happens after Xubuntu bootloader selection (GRUB2): 

```
error: no such module.

Press any key to continue...
```

Key press or if I wait a few seconds, it continues to boot successfully. I am booting by ISO (not extracted). It's the same error in two different Xubuntu versions. 

Is there a typical non-critical module sought at the beginning of the boot process?

---

### Post by VMC on 2024-03-10
Something in your grub is giving erroneous info.
When grub menu comes up, push 'e' key. You might be able to see the offending module.
If not then grub.cfg is pointing to something that doesn't exist.

---

### Post by ajgreeny on 2024-03-10
Which Xubuntu version are you asking about? Is this Xubuntu Noble Daily, current or pending?

I have been using the daily ISOs of Xubuntu for a few weeks now; some of them have errors when booted as a VM in KVM/QEMU but I have never seen anything about a missing module.

---

### Post by #&amp;thj^% on 2024-03-10
> **ajgreeny said:**
> I have never seen anything about a missing module.
+1 i think VMC is on to the problem>>>"grub.cfg is pointing to something that doesn't exist. "

---

### Post by johsal on 2024-03-11
This is my GRUB2 Fossa entry:

```
menuentry 'Fossa64 XUBUNTU (xubuntu-20.04.6-desktop-amd64.iso)' {
   set isofile="/Linux64-ISO/xubuntu-20.04.6-desktop-amd64.iso"
   rmmod tpm
   loopback loop (hd1,3)$isofile
   linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject
   initrd (loop)/casper/initrd
}
```

Is the offending module obvious?

---

### Post by ajgreeny on 2024-03-11
Are you using an installed version of Xubuntu or just a live version running from either a USB or maybe even a virtual Live OS in virtualbox? 

The grub stanza you show suggests this is a live system not a full install but we need to know as much as you can tell us.

Note also that Xubuntu 20.04 which you are using is no longer fully supported. Some of the packages may still have support and upgrades available but all the specifically xubuntu repos are no longer available for 20.04.
For safety you should really move to a fully supported version, cuttently mantic, 23.10, or probably better, 22.04 which has longer support period left.

---

### Post by johsal on 2024-03-11
> **ajgreeny said:**
> Are you using an installed version of Xubuntu or just a live version running from either a USB or maybe even a virtual Live OS in virtualbox? 

The grub stanza you show suggests this is a live system not a full install but we need to know as much as you can tell us.



That is a LIVE boot on an internal HDD.

---

### Post by MAFoElffen on 2024-03-11
He is booting a LiveCD ISO image from file or similar to /etc/grub.d/40_custom...

Try commenting out this line like this:
```

# rmmod tpm

```

Save and then update
```

sudo update-grub

```

Note... GNU Grub has a TPM module (It does exist), but it is not loaded by default. So it would be there at the time that entry is executed.

---

### Post by VMC on 2024-03-11
> **MAFoElffen said:**
> He is booting a LiveCD ISO image from file or similar to /etc/grub.d/40_custom...

Try commenting out this line like this:
```

# rmmod tpm

```

....

Yes, I've seen that **tpm** error in the past also. I'm sure that's the error your seeing.

---

### Post by johsal on 2024-03-12
> **MAFoElffen said:**
> He is booting a LiveCD ISO image from file or similar to /etc/grub.d/40_custom...

Try commenting out this line like this:
```

# rmmod tpm

```


The Trusted Platform Module entry was standing out, but social confirmation was the ticket. Thanks for having a look. 

I wonder why it was assumed to be needed: 

[https://github.com/sebanc/brunch/issues/919](https://github.com/sebanc/brunch/issues/919)

---

