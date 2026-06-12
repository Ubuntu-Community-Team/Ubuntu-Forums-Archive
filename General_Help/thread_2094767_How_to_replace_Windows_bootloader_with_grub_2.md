---
title: "How to replace Windows bootloader with grub 2?"
date: 2012-12-14
forum: General Help
---

### Post by simich on 2012-12-14
Hi all,

I am a brand new member of the forums but have been reading them for quite some time.

I installed Ubuntu after/alongside Windows 7 (with a 'live USB', not  wubi) and now I want to get rid of the latter. I've been searching the  Web for any info but unfortunately my 'replace windows 7 bootloader with  grub 2' search in Google returns results for the opposite - 'replace  grub 2 with windows 7 bootloader', which doesn't help me at all.

Having in mind my (still) little understanding of Ubuntu (and Linux  in general) I figured that the way to do what I want is to first replace  the Windows bootloader with grub2, then format my Windows partition and  finally remove the Windows boot entry. Assuming my plan is valid, I am  stuck at the beginning because I don't know how to do step 1.

So, I'd like to ask, is my plan OK? (Ubuntu is installed on the extended  partition; is this an obstacle?) If so, how would I complete step 1?

If not, could you point me to some readings that would improve my understanding of how things work  in the Linux world and get me  on the right track? (I'm currently reading [Grub 2 Full Tutorial]("http://www.dedoimedo.com/computers/grub-2.html") with the hope of having an insight at some point.) 

regards,
simich

---

### Post by JKyleOKC on 2012-12-14
Try [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) initially; its author, Yann, is a regular here and has made this package the easiest way to do what you want. A note to him will get you exact details of how to make the replacement, whether your Win7 is an EFI setup as mine was, or a MBR setup like most of the folk here expect. Once you have the grub menu coming up initially, you can probably simply delete the Windows partitions -- but if it's an EFI setup that can be tricky! Yann and OldFred can guide you through the thicket.

Having most of your system in the extended partition is perfectly okay. And since you have such a partition, your setup is probably **not** EFI-based.

---

### Post by Pjotr123 on 2012-12-14
If you have a normal dual boot installation, not Wubi, then you already have a pure Grub boot loader....

Simply delete or format the Windows partition, and then run the command:
```
sudo update-grub
```
(in order to lose the Windows entry)

---

### Post by oldfred on 2012-12-14
If you installed correctly, grub2's boot loader should have already been installed to the MBR and you would be booting from a grub menu.

Best to see what is where so we can make specific suggestions.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by simich on 2012-12-18
Thanks for your replies, guys.

@JKyleOKC: my Windows 7 bootloader is in the MBR.
@Pjotr123: I think your suggestion will work only if Grub 2 is the MBR.

@oldfred: here's the pastebin report from boot-repair: [http://paste.ubuntu.com/1448828/](http://paste.ubuntu.com/1448828/)

As I read the report it seems that repairing from boot-repair will do exactly what I want.

Is this correct?

regards,
simich

---

### Post by oldfred on 2012-12-18
Boot-Repair will install grub to the MBR for your.

But grub also remembers where it was installed. I am not sure just reinstalling updates the setting on where to reinstall. Then on a major update it may install to the wrong place.

#To see what drive grub2 uses see this  - grub-pc/install_devices:
 sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub


#to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

    
       Yann has created a easy way [OS-Uninstaller] Safely remove Windows, Ubuntu... in 1 clic ! 
[http://ubuntuforums.org/showthread.php?t=1769489](http://ubuntuforums.org/showthread.php?t=1769489)

---

### Post by simich on 2013-01-02
Thanks for the suggestions, @oldfred.

 <embarrassed> So, the third command totally borked my Ubuntu boot. </embarrassed> 

However running boot-repair through the live USB fixed it and wrote grub2 to the MBR (the thing I wanted). Finally I ran OS-Uninstaller, which basically only removed my Windows boot partition. I later can reformat the Windows drive and repartition it to utilize it.

I installed several updates and everything was fine, although I suspect a kernel update will be the real test. Anyway, that problem (if it happens at all) can be solved later.

Now I am a proud owner of a Windows-free machine :D

Thanks everyone for the help.
Happy New Year!

---

