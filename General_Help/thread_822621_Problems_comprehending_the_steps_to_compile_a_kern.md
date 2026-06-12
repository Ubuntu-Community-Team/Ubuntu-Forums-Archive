---
title: "Problems comprehending the steps to compile a kernel"
date: 2008-06-08
forum: General Help
---

### Post by jreinis on 2008-06-08
> **lauris said:**
> Hi,

 Is there a place I could download deb file of  2.6.22-14-generic kernel compiled with High Memory Support 64GB ? 

I`m running into issues while trying to do it myself (my compiled kernel gets 2.6.22.9 version, while I expect it to be 2.6.22-14, nvidia drivers failes to load with the new kernel and so on).

Thanks for help.

The Task - to change somewhere somewhat to get generic kernel supporting till 64GB (desktop). Server version do not offer.

I understand I need to edit existing .config and (modules or do not? )
with ALL existing settings nothing changing except to support memory till 64GB 
(now my system sees 3.5GB only) because new motherboard goes with 4/8GB memory chips and more import for me 
I use virtualbox and vmware OS images(to develop and to use some applications for windows and apple platforms)

So, I did these steps-by-steps guide

1. sudo apt-get install linux-kernel-devel fakeroot build-essential
2. sudo apt-get build-dep linux-image-$(uname -r)
3. apt-get source linux-image-$(uname -r)
4. sudo apt-get build-dep linux-ubuntu-modules-$(uname -r)
5. apt-get source linux-ubuntu-modules-$(uname -r)

Now I confuse:
What command I run to edit file ".config" ?
Is that place /usr/src/linux-headers-2.6.24-18-generic right?

CONFIG_HIGHMEM64GB is it enough?

Next command I did not get at all :
AUTOBUILD=1 fakeroot debian/rules binary-debs
What does it mean practically and I did not find directory "debian"?
 
Any help from guys who really compiled EXISTING kernel settings (not new one )?

My system is Ubuntu Hardy Heron 8.04 with generic kernel.

---

### Post by Nepherte on 2008-06-08
An exhaustive tutorial on how to compile your own kernel:[http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

The part where you are editing the .config file is:
- For a gui
```
make xconfig
```
- For a terminal:
```
make menuconfig
```

---

### Post by Nepherte on 2008-06-08
edit: double post

You can't just edit an existing kernel. You have to rebuild it all the way.

---

### Post by jreinis on 2008-06-08
> **Nepherte said:**
> edit: double post

You can't just edit an existing kernel. You have to rebuild it all the way.
How?
I edited in midnight commander /usr/src/linux-headers-2.6.24-18-generic/.config just uncomment CONFIG_HIGHMEM64GB=y
Now what to do?
What commands to run step-by-step (in sight that I have Ubuntu 8.04 and Ubuntu customized kernel and modules)?
Thanks.

---

### Post by jreinis on 2008-06-08
> **Nepherte said:**
> An exhaustive tutorial on how to compile your own kernel:[http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

The part where you are editing the .config file is:
- For a gui
```
make xconfig
```
- For a terminal:
```
make menuconfig
```
Thanks but I do not need own kernel, what I need just I did uncomment CONFIG_HIGHMEM64GB=y and now I want compile source code that placed in :/usr/src/linux-headers-2.6.24-18-generic by somewhat line of commands and may be I do not know modules -I mean if any so ALL modules.
My task is to recompile GENERIC KERNEL from UBUNTU team but with Option CONFIG_HIGHMEM64GB=y that's it (and of course if any all modules).
So you see I just want to improve one mistake done by Ubuntu team - all new motherboardes come with 4GB/8GB chips included, so it MUST be seen by system ALL the memory we, Users, have paid.

---

