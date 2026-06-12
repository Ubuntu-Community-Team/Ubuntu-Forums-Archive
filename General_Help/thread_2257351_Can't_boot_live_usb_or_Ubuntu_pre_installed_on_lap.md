---
title: "Can't boot live usb or Ubuntu pre installed on laptop"
date: 2014-12-19
forum: General Help
---

### Post by vincetrapani1 on 2014-12-19
So I''ve been learning my way around ubuntu coming from windows for my entire life. Have a basic understanding of the terminal and what not and have been having fun learning it the past few weeks. All I'm running is ubuntu 14.04 on a x64, acer aspire, reluctantly ran in legacy but regardless of that it actually works(ed) fantastically. I don't see myself ever going back to Windows

Now to the problem, and this is pretty urgent as I'm in the middle of 3 projects for clients and am afraid that, since I'm too inpatient to wait for a backup(I know, I know, please don't lecture lol), that my hard drive will have to be wiped but so far this is the only specific problem i've had with ubuntu that I haven't been able to find online for a solution.

--I perviously dual booted fedora 20 just to try out some other distros and see which one had me the most comfortable and decided on ubuntu. I formatted the fedora partition, yet always came across it in the grub but just never got to looking up exactly what needed to be replaced and exactly where in the grub file. So my dumba** decided(when installing fedora) to use half of my hard drive! Genius! no. Today, I dreadfully ran out of hard drive space on my partition, and standing in between the other 250 gigs, was a tiny 500mb partition therefore not b eing able to combine them without moving the 500mb standing in the way, or at least thats what my belief from reading would be. So I read about booting into your liveusb and rearranging/deleting/adding partitions from there as they won't be mounted. Did that, copied the files from the 500mb partition which included efi and grub2 which scared me but I dug around in there and saw fedora mentioned a few times and just figured that it was the reason fedora hadn't yet been removed from the loader screen on start up. 

Somehow in that process, I guess it the partition of 500mb(sd3) got either formatted, or mounted, or both. Kept getting an error when I tried to unmount regardless of the method I chose, and therefore said screw it I'll just shutdown and start back from the liveusb and try it again(I'm a Ubuntu noob please don't critisize lol). 

WRONG---I try to boot from liveusb and get a error regarding unable to mount on /dev/loop1 , and then when I try to boot from hard drive I get an error saying that "grub2/i386-pc/normal.mod not found". I'm working from my 11 inch 1 gig of ram netbook right now and looked up some things and tried doing the (hd0,msdos*) to find where grub was, and the only useful thing out of that I found was where in one of them it said along the lines of /boot/grub and then blacklist.txt.

I just remembered the arrow key trick when the livusb first gets recognized (before it gives me the errors) and did a disk check resulting in 1 error. I don't know how to check but as of now I'm just going to try and download a new iso of ubuntu and put onto a usb and see what I can do. I really don't want to have to reinstall but if that's what has to be done then so be it but I need to figure something quick.


Thanks guys

Edit: The error on the liveusb is /dev/loop1 on /cow claiming it cant mount it.

Edit2: mint and kali wont boot from usb either, just updating n tried both. At a complete standstill

---

### Post by oldfred on 2014-12-19
Some systems just seem to get locked up with too many warm reboots and errors. Best to try a total cold reboot.
And if laptop remove battery and hold start button or 10 Sec or so to drain any remaining power. Then see if you can boot live installer in live mode.

Did you let Fedora do its default install of a separate /boot and LVM? Most suggest if dual booting to not use LVM but do it more like Ubuntu with standard ext4 partition(s). With LVM it is only a possible advantage if it is the entire drive (Ubuntu's default) so you can rearrange partitions easily. But LVM adds a level of complexity.

The error on normal not found is often related to grub version differences.  
If you reinstall be sure to use Something Else.

With multiple installs always best to run Boot-Repair and save a copy of its summary report, so you know what is installed where and which system has control of MBR and booting. And grub in any install may reinstall its grub to MBR on kernel or major grub updates unless you change that setting.

If you can get live installer working post link to summary report from Boot-Repair.
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

   Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

What model Aspire? Users have been able to install in UEFI boot mode, but have to do some work arounds. And many models of Acer require you to set a password in UEFI (never ever lose that), to be able to change settings in UEFI to boot Ubuntu.

---

