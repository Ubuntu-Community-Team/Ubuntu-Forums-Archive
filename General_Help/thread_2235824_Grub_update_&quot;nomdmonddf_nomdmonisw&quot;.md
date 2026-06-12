---
title: "Grub update &quot;nomdmonddf nomdmonisw&quot;"
date: 2014-07-23
forum: General Help
---

### Post by Lappert on 2014-07-23
Running ubuntu 14.04 with kubuntu desktop on a machine with RAID 1.

Doing a periodic apt-get upgrade, I get a splash screen wanting to update /etc/default/grub - but it warns me that the existing grub file had been locally modified.

I seem to remember I did extend the timeout from 2 to 5 seconds, but that's not what a comparison shows.

The existing grub file:

GRUB CMDLINE LINUX DEFAULT="nomdmonddf nomdmonisw"  (as far as I know I did not add "nomdmonddf nomdmonisw")

the proposed line would be:

GRUB CMDLINE LINUX DEFAULT=""

So my question is a) what does "nomdmonddf nomdmonisw" do? Is it important?

Should I re-modify the grub file to put it back in?

Thank you.

---

### Post by ibjsb4 on 2014-07-23
Have you seen this?

[https://lists.ubuntu.com/archives/ubuntu-devel/2014-February/038095.html](https://lists.ubuntu.com/archives/ubuntu-devel/2014-February/038095.html)

---

### Post by Lappert on 2014-07-23
Thanks... but it's a bit above my head. Is it wise to leave those two items out, or should I put them back in?

---

### Post by ibjsb4 on 2014-07-23
It has to do with raid and I really don't know the affect this will have on your raid.

---

### Post by Lappert on 2014-07-23
Thanks

---

### Post by rocky-bernstein on 2015-05-14
> **Lappert said:**
> Thanks... but it's a bit above my head. Is it wise to leave those two items out, or should I put them back in?

To get this conversation going on a less vague way and in a way for *others* who might stumble across this, as best as I can tell from reading cited email, if you don't have drmraid or are not using it, but do have mdadm installed, then it doesn't matter. 

This is my particular situation. Actually, my particular situation is also that I have mdadm installed but I am not using it and mdadm entries don't appear in /etc/fstab.

 (Then in my particular situation, other than programming simplicity/laziness, I don't know the update tried to add these options.)

A best as I can tell, this option is used is used for compatibility in either migrating from drmraid to mdadm, or possibly from an older mdadm to a newer one. But in either case, if you don't have entries in /etc/fstab then these options do nothing.

Correct?

---

