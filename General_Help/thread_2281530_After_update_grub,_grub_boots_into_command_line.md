---
title: "After update grub, grub boots into command line"
date: 2015-06-07
forum: General Help
---

### Post by Dri3s on 2015-06-07
Hello,

I have a Asus N550JK laptop, dual boot ubuntu 14.04 and windows 8.1.

Everything was working fine, until a few days ago, when I ran the software updater. While updating grub the pc rebooted into the grub command line. No more GUI to select my operating system.

2015-06-06 18:55:33 configure grub-efi-amd64:amd64 2.02~beta2-9ubuntu1.2 <none>
2015-06-06 18:55:33 status half-configured grub-efi-amd64:amd64 2.02~beta2-9ubuntu1.2

So I booted the live cd and ran boot-repair, which kind of fixed it(with errors: [http://paste.ubuntu.com/11606415/](http://paste.ubuntu.com/11606415/)), I'm able to select my OS's. 

But when I run the software-updater, it automatically restores grub and it boots again into the command line. 

And when I try to run synaptic package manager, it says: "E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem." But this doesn't correct the problem, it again makes the pc boot into the grub command line.

Boot-repair each time restores grub, so I can boot both OS's, but I can't update or install packages in Ubuntu.

Is this easy to solve, without reinstalling everything? More information needed?

Tia

---

### Post by oldfred on 2015-06-07
Grub and a few other tools like parted, need to scan all partition. But you left Windows hibernated, so it cannot be scanned and I think then grub is just failing to complete. It still should work, but maybe not add the Windows boot entry to grub.

Script shows no files in efi partition. Is grub erasing them, and then Boot-Repair restoring them?
 Or did script hiccup and not show files you have in /EFI/ubuntu and other /EFI/* folders?

---

### Post by Dri3s on 2015-06-08
Ok thx Oldfred,

I left windows hibernated...

---

