---
title: "Won't boot"
date: 2024-09-03
forum: General Help
---

### Post by AllanP on 2024-09-03
I upped from Ubuntu Mate 22.04 to 24.04.1. I have installed it twice now and am still faced with not booting normally. I have to select advanced boot and then it will boot. I don't know if the notice "EFI stub warning failed to measure data from event 1" or words to that affect. It booted OK on the first boot after install., but from then on have to select "Advanced". Once booted all seems normal with nothing missing.

---

### Post by yancek on 2024-09-03
You will need to post more details and the easiest/best way to do that is to go to the site at the link below.  From there, read through the page to get a basic understanding then download the software from your installed Ubuntu.  Use the 2nd option discussed on the page then select the option to Create BootInfo Summary.  When it finishes, it will give you a link which you can post here so members have access to the information. 

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

This output will give information on drives/partitions, filesystem types, size of drives, whether you have an EFI install and much more.

---

### Post by AllanP on 2024-09-03
I didn't get anywhere with that boot repair; wound up with a link [http://paste/ubuntu.com/p/9HD8mjDywy/](http://paste/ubuntu.com/p/9HD8mjDywy/) which doesn't go anywhere. My manual installation was to select sda1 boot/efi. then a partition for OS /. Then an existing  /home partition and a /home/Storage partition. This has always worked fine and it worked with 22.04. So me thinks it's something with 24.04.1. Maybe I should try it again with 24.04. i just now enabled Ubuntu pro. Maybe IO should try another kernel.
Anyways enough for now; going out for a swim.

---

### Post by yancek on 2024-09-04
Your link to boot repair is broken, don't know why as that rarely happens.  You could try running it again and make sure you get the correct link.

---

### Post by AllanP on 2024-09-04
> **yancek said:**
> Your link to boot repair is broken, don't know why as that rarely happens.  You could try running it again and make sure you get the correct link.
I think you are quite right on that, but after two installs with same results; how to fix it? I will try again with the24.04 and not the 04.1. Thanks for your reply
Regards, Allan

---

### Post by oldfred on 2024-09-04
In addition to Boot-Repair report.
What brand/model system? What video card/chip?

Some systems like HP require you to change boot order in UEFI settings.
Some like Acer require you to enable "trust" on ubuntu entry in UEFI settings.
Some with proprietary video hardware like nVidia require you to install the proprietary drivers as part of install or boot to terminal and install driver then. Often easier with UEFI Secure boot off, but you can with Secure boot on if you set your own MOK or machine owner key for security.

---

### Post by AllanP on 2024-09-04
Mine is a home build and have installed Ubuntu many many times without a problem.
Edit re-installed but with basic default Ubuntu. I didn't like this version at all so installed Mate desktop and all seems OK now except that stub efi error still comes up on boot, but it does it with all my OS's.

---

