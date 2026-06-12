---
title: "Recovery Mode for Ubuntu installed by Wubi?"
date: 2007-08-08
forum: General Help
---

### Post by porcorosso on 2007-08-08
I did a search for "recovery mode" in this section, but the hits I got all seemed to be about recovery mode for Windows. I was just wondering if there's a way to boot into Ubuntu's recovery mode (since there seems to be no GRUB) when you've installed Ubuntu through Wubi.

If I've missed something obvious you are most welcome to dope-slap me. But please, also give me the information!

:D

---

### Post by ago on 2007-08-08
edit c:\wubi\boot\grub\menu.lst, increase the timeout and comment out the hidemenu option. After you select ubuntu you will see a second boot menu to specify the kernel/recovery

---

### Post by porcorosso on 2007-08-08
Thank you for that information. Your instructions worked, though I was sort of surprised to see TWO sets of recovery and generic boot options. Would you have any idea why that would be? My Wubi installation is on a separate physical hard drive from my Vista installation.

I am involved in some testing that may require me to use the recovery mode, and I wanted to be sure I could get into it. Thanks again for your help.

---

### Post by ago on 2007-08-08
> **porcorosso said:**
> Thank you for that information. Your instructions worked, though I was sort of surprised to see TWO sets of recovery and generic boot options. Would you have any idea why that would be? My Wubi installation is on a separate physical hard drive from my Vista installation.

I am involved in some testing that may require me to use the recovery mode, and I wanted to be sure I could get into it. Thanks again for your help.
You have 2 sets probably because you did a system upgrade and that installed a new kernel, each kernel has 2 boot options, to that you have to add the kernel that came with wubi.

---

### Post by porcorosso on 2007-08-08
Oh, okay. So that explains why one (pair) of them doesn't work? Heh. I guess I should edit the file to get rid of the extraneous pair. Nice to know.

Thanks again.

---

