---
title: "[SOLVED] Newbie on Ubuntu"
date: 2008-05-22
forum: General Help
---

### Post by myth1001 on 2008-05-22
I'm just another newbie who is bored of Xp and plan to try Ubuntu.
Well..from what i understand, Wubi is a windows installer which allows me to use Ubuntu in Windows..
The questions are,

I've a intel core duo processor 1.83Ghz
windows xp SP2
The iso files are stated x64 or x86.. what's that? and can my pc support it? I usually install x32 programs in windows. Does this mean that my pc is x32?? 

and well..

Am i allowed to access windows files when i'm operating on Ubuntu?
Will all my drivers work if i use Ubuntu? (e.g wireless, graphic card, in-built webcam and others)

sorry for the stupid questions^^"

---

### Post by r3m0t on 2008-05-22
You don't need to worry about all this x86/x64/x32 stuff. Just go to [http://wubi-installer.org/index.php](http://wubi-installer.org/index.php) and press "Download Now". The software will figure it all out. :)

Yes, you will be able to reach your Windows files from inside Ubuntu.

As for the drivers, it might work, but it might not work. It depends on how co-operative the hardware manufacturer has been with Linux programmers, and how popular that piece of hardware is.

There isn't an easy way to tell, apart from installing wubi and trying it out!

Good luck.

---

### Post by myth1001 on 2008-05-22
I've a weak internet connection, slow and unstable. If i were to depend on the Wubi installer to download the suitable iso for me, it'll never complete. I'm currently downloading ubuntu-8.04-desktop-i386.iso , and i'm wondering if it will work for my system..:confused:

---

### Post by Dave2k6 on 2008-05-22
> **myth1001 said:**
> I've a weak internet connection, slow and unstable. If i were to depend on the Wubi installer to download the suitable iso for me, it'll never complete. I'm currently downloading ubuntu-8.04-desktop-i386.iso , and i'm wondering if it will work for my system..:confused:

yes, the ubuntu-8.04-desktop-i386.iso will work with your system.

Download Wubi from [http://wubi-installer.org/index.php](http://wubi-installer.org/index.php), and save installer to save place as the ISO image you downloaded, then run the installer.

Choose a username and password, then click Install, Wubi will use the ISO image you downloaded to install Ubuntu.

---

### Post by phoenix_abhi on 2008-05-22
First of all Ubuntu 8.04 ISO is coming with WUBI. u do not have to d/l it separately. Ur system configuration is more than enough to run Ubuntu. Where a XP can run smoothly, Ubuntu will use half of the resources.
Ur post says u have 32 bit windows XP installed, so u have to install x86 (32 bit) Ubuntu in XP using wubi. Ur pc is certainly support 64 bits also.Through wubi ur installing Ubuntu as a virtual OS, so u can use both OS simultaneously. Most of the Intel hardwares works really well with Ubuntu. I do not know about a wireless, coz i do not have one, but the web cam, graphics and sounds are easy to install. Normally ubuntu detect and install the necessary drivers on installation. U need to d/l codec for multimedia support.

I suggest u to give a Ubuntu a separate partition, coz XP is known for BSOD and other trouble. If u use Ubuntu within any windows platform u can not enjoy the real Ubuntu's flavor. Most of the 1 GB ram will be taken away by windows and Ubuntu have to do with the rest. It is better allocate a small partition for Ubuntu and experiment. I am sure u will be hooked in to it. like me :guitar:

:lolflag:

---

### Post by myth1001 on 2008-05-22
thanks for all the replies! ^_^
I shall wait for the download to be complete and test it out.

---

### Post by Dave2k6 on 2008-05-22
When you have installed Ubuntu and boot to it, you will get the full memory of your system available to Ubuntu as Windows is not loaded in any way when you boot into Ubuntu.

All Wubi does is install Ubuntu inside a single file (virtual disk), modifies the boot menu, and thats it.

Windows doesn't run in the background when you boot into Ubuntu.

---

### Post by myth1001 on 2008-05-22
I've installed it and it's working great!! :)
I'm exploring it now and will get to know more about Ubuntu :)

---

### Post by ago on 2008-05-24
> **phoenix_abhi said:**
> Through wubi ur installing Ubuntu as a virtual OS, so u can use both OS simultaneously.

Wubi is not a VM, it runs directly on the hardware at full speed (other than harddisk I/O). And no, you cannot run both OSes simultaneously, you need to dual boot like in a standard installation.

---

