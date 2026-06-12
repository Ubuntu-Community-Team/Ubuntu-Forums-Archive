---
title: "Problem while booting"
date: 2015-04-02
forum: General Help
---

### Post by Sebastian_Ulloa on 2015-04-02
Hello,
I've got a problem when I try to start ubuntu, a screen appears showing this:

GRUB4DOS 0.4.5c 2012-06-19, Mem: 630K/2765M/254M, End: 35B421
[Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions.
Anywhere else TAB lists the possible completions of a device/filename]

GRUB>

I tried with the *ls *command and it seems that it tries to look for the grub in the Windows root folder because it displays folders like
[I]
Program Files (x86)

[/I]I've tried some commands like kernel and cat, but with both the result is:

*Error 15: File not found*

---

### Post by oldfred on 2015-04-02
We do not support EasyBCD, you may do better on there forums.
Grub4dos is an old version of grub legacy used by EasyBCD as Windows will not boot Linux.
Ubuntu uses grub2 as it boot manager or menu and boot loader.

       [http://neosmart.net/blog/](http://neosmart.net/blog/)
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

If you want to use grub2 then download this into the Ubuntu installer and post the link to the Summary report.
      
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Boot-Repair can only fix minor Windows issues like reinstall a Windows type boot loader. You otherwise need a Windows repair CD or flash drive to repair Windows issues.

---

