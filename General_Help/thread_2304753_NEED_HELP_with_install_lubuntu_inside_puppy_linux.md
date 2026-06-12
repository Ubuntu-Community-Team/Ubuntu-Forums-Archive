---
title: "NEED HELP with install lubuntu inside puppy linux"
date: 2015-11-29
forum: General Help
---

### Post by coma2 on 2015-11-29
Hello..I am new here and sorry if I am posting in wrong topic.....
I installed puppy linux on my old laptop..Now want to install lubuntu and delete puppy from my computer...How can I do this without USB or CD/DVD disk?

---

### Post by matt_symes on 2015-11-29
Hi

> **coma2 said:**
> Hello..I am new here and sorry if I am posting in wrong topic.....
I installed puppy linux on my old laptop.. Now want to install lubuntu and delete puppy from my computer...How can I do this without USB or CD/DVD disk?

How did you install puppy in the first place ?

Is it the case that the laptop does not have a working CD drive and USB ports or that you just don't have a spare CD ROM or USB pen drive ? 

If it's the latter, can you not get a USB pen drive or CD ROM from somewhere ?

Assuming non working hardware, there isn't any easy way although there are some ways.

These come to mind off the top of my head.

1. Put laptop hard drive into a machine with USB/CD. You may have to fix some things if you do that.
2. PXE boot and install that way but requires a PXE server.
3. Boot the ISO from grub and install into a separate partition. Not tried this method though so i can't be 100% sure it will work. 

Maybe someone else has some better ideas.

EDIT:

4. debootstrap using a chroot to install a minimal install and go from there. This assumes that puppy has debootstrap and i expect it will.

These are not newbie ways to install any flavour of Ubuntu though.

EDIT 2:

Just thought i should mention that methods 3 and 4 above require either a spare partition or some slack space on the drive to make a partition. If you have neither of these then 3 and 4 are not options for you.

I'm really interested: why can't you use a CD or a USB to install ?

As i said, there's really no easy way to do this.

EDIT 3:

I suppose you could try to uninstall the Puppy desktop and install the Lubuntu desktop but i suspect that's not what you wanted to do.

Kind regards

---

### Post by coma2 on 2015-11-30
> **matt_symes said:**
> Hi



How did you install puppy in the first place ?

Is it the case that the laptop does not have a working CD drive and USB ports or that you just don't have a spare CD ROM or USB pen drive ? 

If it's the latter, can you not get a USB pen drive or CD ROM from somewhere ?

Assuming non working hardware, there isn't any easy way although there are some ways.

These come to mind off the top of my head.

1. Put laptop hard drive into a machine with USB/CD. You may have to fix some things if you do that.
2. PXE boot and install that way but requires a PXE server.
3. Boot the ISO from grub and install into a separate partition. Not tried this method though so i can't be 100% sure it will work. 

Maybe someone else has some better ideas.

EDIT:

4. debootstrap using a chroot to install a minimal install and go from there. This assumes that puppy has debootstrap and i expect it will.

These are not newbie ways to install any flavour of Ubuntu though.

EDIT 2:

Just thought i should mention that methods 3 and 4 above require either a spare partition or some slack space on the drive to make a partition. If you have neither of these then 3 and 4 are not options for you.

I'm really interested: why can't you use a CD or a USB to install ?

As i said, there's really no easy way to do this.

EDIT 3:

I suppose you could try to uninstall the Puppy desktop and install the Lubuntu desktop but i suspect that's not what you wanted to do.

Kind regards


Thanks for reply matt...
My windows was broken.Tried to reinstall OS but boot menu was crashed and it did not read bootable CD or USB....so I made puppy linux live CD and from Live CD installed puppy as main OS....I have CD-ROM but wanted to know if I had a chance to install lubuntu without it.....are there any installers like wubi on windows?

---

### Post by matt_symes on 2015-11-30
Hi

> **coma2 said:**
> Thanks for reply matt...
My windows was broken.Tried to reinstall OS but boot menu was crashed and it did not read bootable CD or USB....so I made puppy linux live CD and from Live CD installed puppy as main OS....I have CD-ROM but wanted to know if I had a chance to install lubuntu without it.....are there any installers like wubi on windows?

Wubi on Windows is no longer supported. There is no equivalent Wubi for Linux unless your consider a virtual machine... 

...if you wanted to run Lubuntu inside Puppy then you may be able to use VirtualBox to create a virtual machine and run Lubuntu inside it, but you will still have Puppy installed on the machine and you will still need to boot into Puppy to start the virtual machine. The performance of Lubuntu inside the virtual machine will be slower than installing it directly on the hard drive.

The easiest way by far, if you want to get rid of Puppy and install Lubuntu, is to create a LiveCD or a LiveUSB of Lubuntu and perform a fresh installation directly to the hard drive. 

The methods i mentioned in post #2 are advanced methods for times where you are doing some specialist or hardware is broken (i assumed you had broken hardware).

For ( ~ :) ) 99.9999% of the time you'll want to be installing from a LiveCD/USB.

Kind regards

---

### Post by coma2 on 2015-11-30
> **matt_symes said:**
> Hi



Wubi on Windows is no longer supported. There is no equivalent Wubi for Linux unless your consider a virtual machine... 

...if you wanted to run Lubuntu inside Puppy then you may be able to use VirtualBox to create a virtual machine and run Lubuntu inside it, but you will still have Puppy installed on the machine and you will still need to boot into Puppy to start the virtual machine. The performance of Lubuntu inside the virtual machine will be slower than installing it directly on the hard drive.

The easiest way by far, if you want to get rid of Puppy and install Lubuntu, is to create a LiveCD or a LiveUSB of Lubuntu and perform a fresh installation directly to the hard drive. 

The methods i mentioned in post #2 are advanced methods for times where you are doing some specialist or hardware is broken (i assumed you had broken hardware).

For ( ~ :) ) 99.9999% of the time you'll want to be installing from a LiveCD/USB.

Kind regards

Thanks for help...I will make lubuntu liveUSB.....

---

### Post by Bucky Ball on 2015-11-30
You could install 'lubuntu-desktop' or 'lubuntu-core' from whatever package manager Puppy uses (Synaptics?) and that would do it (the second is even lighter than Lubuntu). You'd still have all the puppy stuff as well, though. :)

Just reboot and choose the lxde or Lubuntu session from the Sessions menu.

---

### Post by oui on 2015-12-04
Hi Coma
Have a look [here]("http://ubuntuforums.org/showthread.php?t=2303234"). The differenz will be: You have to try it with a alternate installation's ISO, or do what I am searching for: open the ISO and extract the preinstalled stuff. As I am now using 16.04, I did stop my efforts to do that. But the matter continues to interest me really more.
Salut

---

### Post by oui on 2015-12-05
Hi Coma
I have to amend me: the alternate ISO is absolutely nothing goods... it doesn't build on casper and can't do at all that what I am awaiting of it!

---

