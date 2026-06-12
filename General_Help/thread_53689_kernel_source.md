---
title: "kernel source"
date: 2005-08-01
forum: General Help
---

### Post by Dr. Z2A on 2005-08-01
I am setting up a wifi card that needs to know where the kernel source is to set up.  Unfortunately, I do not know where the kernel source is stored.  Can anyone tell me where the kernel source is stored and if it needs to be uncompressed or not?  And if it needs to be uncompressed, what the file name is?  I was told that it should be in /usr/src, but I checked there and all there was was a folder called rpm.

---

### Post by art on 2005-08-01
Download, using synaptic, linux-tree
It should put the correct files in /usr/src. First check which kernel you are running with
uname -r in cmd, and download the corresponding one.

---

### Post by az on 2005-08-01
If you need to compile a kernel module, just install the linux-headers package for your kernel.  The default kernel is 2.6.10-5-386, so install linux-headers-2.6.10-5-386

It makes a symlink in /lib/modules/2.6.10-5-386/build so that any config script finds the linux-headers and uses that.  linux-headers-2.6.10-5-386 is on your cd, if you have no other internet access.  The linux-tree-2.6 package is only available on the online repositories.


Usually, just the headers are enough to build a module.

---

### Post by Dr. Z2A on 2005-08-01
[QUOTE=art]Download, using synaptic, linux-tree
It should put the correct files in /usr/src. First check which kernel you are running with
uname -r in cmd, and download the corresponding one.[/QUOTE]
where can i get that?

---

### Post by Xian on 2005-08-01
[QUOTE=Dr. Z2A]where can i get that?[/QUOTE]
Where the member said...using Synaptic.
Just do a keyword seach for linux-tree.

[Synaptic How-To](https://wiki.ubuntu.com/SynapticHowto)

---

