---
title: "Self-compiled kernel on Feisty"
date: 2007-03-06
forum: General Help
---

### Post by ngolian on 2007-03-06
I've compiled my own kernel on Feisty like I've always done with earlier Ubuntus and Debian. It still works but there's a minor problem: update-grub keeps changing all the root= entries from /dev/hda7 to a UUID, including the one in the kopt line. This makes my kernel panic if I forget to change it back. AIUI I need to use an initrd or initramfs to be able to mount by UUID, but I don't know how to do this. I'd prefer to use initramfs if possible because of initrd being obsolescent. Are there any guides around for it?

---

### Post by Tyler_Durden on 2007-05-26
Hi,
I have exactly the same problem. Can somebody please explain why vanilla kernels won't boot with the root=UUID=... option. And why does update-grub always replace my root=/dev/sdb2 entry with root=UUID=...? Is there any way to disable this damned UUID stuff?

Many thanks in advance.

So long,
CU Tyler

---

### Post by Tyler_Durden on 2007-05-26
Hi.
well I finally found a solution that works. The one thing that really disturbed me is that update-grub just overrides my "kopt=..." setting. Why does it do that? This behaviour kinda reminded me of SuSe's Yast, which simply overwrites any configuration file regardless if being modified by the user or not.

So, the easiest solution to this "problem" is simply: Install the debian grub package, which does not override your "kopt=..." setting without asking you. I chose the grub package from debian-unstable, downloadable here: [http://packages.debian.org/unstable/admin/grub](http://packages.debian.org/unstable/admin/grub).

Cheers,
CU Tyler

---

