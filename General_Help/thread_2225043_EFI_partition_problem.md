---
title: "EFI partition problem"
date: 2014-05-19
forum: General Help
---

### Post by astronos2007 on 2014-05-19
Hello, everyone! I am new to this forum, but I didn't know where to seek help, so I posted here. Sorry for the possible mistakes. I started using Linux OS 2 months ago and I began with installing Ubuntu 12.04. Everything was fine until I had some issues with it regarding drivers and I had to dual boot with Windows 8, and replace Ubuntu with xUbuntu 14.04 64 bit. After that, I realised, using GParted that the EFI partition (90 MB) got almost full (89,99 MB used). I saw on the Internet that the EFI has to be at least 200 MB in size, so I used GParted to resize it to 300 MB, taking some space from swap partition. But alas, GParted gave me an error and let the partition in a weird state: now it has 299,99 MB size, but with 89,99 MB capacity (???) and 8 MB used. The used space is little because I deleted the entire Win 8 partition and also got rid of the EFI files. Now, my partition look like those in the photo attached.

[IMG]http://s9.postimg.org/wdgj717dr/Screenshot_19_05_2014_22_00_36.png[/IMG]

 The question is how do I restore the EFI partition to a  good state? GParted always shows it in error, and asks me to check the partition and repair it. I do this, but it shows me the error: "GNU parted cannot resize this partition to this size. We're working on it!". Can you please help me with this? I cannot do anything to it, I cannot resize, or move it at all, it just keeps getting error. 

[IMG]http://s2.postimg.org/ll4uw6jex/Screenshot_19_05_2014_22_01_35.png[/IMG]

Is it safe to delete it for good and create another one FAT32 and use it as EFI? If so, how can I safely create one without distroying GRUB and make my system unbootable? :-S Thank you!

---

### Post by oldfred on 2014-05-19
Do you have files in efi partition backed up?
With Ubuntu you can reinstall grub-efi and it will create new efi folder for Ubuntu. 
Usually I suggest larger efi partitions, but the Windows default of 100MB is usually large enough for most dual boot installs. What filled it up?

You can try this, but that may be what gparted is running in the background.
       sudo /sbin/fsck.vfat -V <the fat32 device>
sudo fsck -t vfat /dev/sda1

      
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Luke M on 2014-05-19
Copy all the files on the EFI partition to a safe place, then reformat the EFI partition and copy the files back. In case something goes wrong, have a copy of rEFInd handy on CD or USB: [http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)

---

### Post by Luke M on 2014-05-19
Same thing happened to me, by the way...you didn't do anything wrong, the FAT resizer is buggy.

---

### Post by astronos2007 on 2014-05-19
Thank you all, guys! It worked!! I solved it! I deleted and remade the partition after copying the files in it into a safe place. After that I formatted it and it finally used all the space within. Then I copied the files back so that boot-repair recognized EFI (I tried without copying back and it showed something about GPT :-??), used boot-repair and it did the trick! Followed the instructions and now I have my clean EFI back :X:X. Thank you very much for your help! You saved me from a long list of necessary repairs to my system if I tried to do it myself by all means I could think of :-S

---

