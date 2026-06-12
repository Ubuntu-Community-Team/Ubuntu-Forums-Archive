---
title: "Question regarding Grub &amp; installation"
date: 2007-08-31
forum: General Help
---

### Post by df9517 on 2007-08-31
I have following HDD setup:
HD(0): sda: 80 GB storage/backup disk
HD(1): sdb: 250 GB main disk
PC is booting from HD(1)

On my sdb main disk I had Kubuntu feisty installed as follows:
sdb partition 1: Full installation
sdb partiition 5: swap partitition
booting into HD(1.0)

I decided to try Gutsy out. I loaded the live CD and when I came to the partitioning question during the installation I choosed to minimise the present partition 1 with 10 Gb and install gutsy on those 10 GB. The result was as follows:
sdb partition 1: Full installation feisty
sdb partition 3: Full installation gutsy
sdb partiition 5: swap partitition
sdb partition 6: swap partitition

When I tried to boot I noticed that Gutsy probably loaded the boot/grub stuff in HD(0) so I couldn't boot to Gutsy.

I made the installation one more time and this time I clearly specified installatrion of Gutsy same as before:
sdb partition 1: Full installation feisty
sdb partition 3: Full installation gutsy
sdb partiition 5: swap partitition
sdb partition 6: swap partitition
The only difference I did was to specify that boot should be made to HD(1) instead.

Now when I booted I found following problems:
1) The PC booted from the /boot located on the new gutsy installation HD (1.2) instead of previous HD (1.0)
2) But even though the boot menu showed up (with both Gutsy and Feisty options)  it didn't work because the gusty installation had faulsly noted that Gutsy should boot on HD (0.2) and Feisty on HD (0.0). I booted manually into Gutsy and changed the boot script manually to the correct HD (1.2) and HD (1.0). Now everything works.

I have following questions and comments:
1) How do the PC know that it shall use the boot script in HD(1.2) instead of HD(1.0). boot scripts exists on both places.
2) When I later decide to throw out this 5th tribe version of Gutsy, will my computer instead boot from HD(1.0) as it was before?
3) Is it expected for beginners to be able to understand all this and to be able to trouble shoot it? I think it the graphical installation interface for the booting part is terrible. You can never know what will actually happen.
4) Since I made the install of Gutsy, my Feisty installation does no longer acknowledge any swap partition (neither 5 or 6). Can I correct this easily.

Best Regards,
Daniel

---

### Post by meierfra on 2007-08-31
> 1) How do the PC know that it shall use the boot script in HD(1.2) instead of HD(1.0). boot scripts exists on both places.

When you install Gutsy, Grub was reinstalled and told to use the Gutsy boot script in HD(1,2).
You can change that by reinstalling Grub. It is  really easy. You can google it or ask here if you need help.

> 2) When I later decide to throw out this 5th tribe version of Gutsy, will my computer instead boot from HD(1.0) as it was before?

No, you will have to reinstall grub.

 > 3) Is it expected for beginners to be able to understand all this and to be able to trouble shoot it? I think it the graphical installation interface for the booting part is terrible. You can never know what will actually happen.]

Beginners should not use Gutsy before the final release.

> 4) Since I made the install of Gutsy, my Feisty installation does no longer acknowledge any swap partition (neither 5 or 6). Can I correct this easily.

Yes, you need to edit the file /etc/fstab. 
It should have a line similar to this:

UUID=bb9efa29-c42b-46fe-8cda-fa675a2416d9     none           swap         sw                                 0      0

Change it to:

/dev/sdb5     none           swap         sw                                 0      0

Also you don't need two swap  partitions. You can use the same one for Feisty and Gutsy.

---

### Post by southernman on 2007-08-31
> **df9517 said:**
> 
I have following questions and comments:
1) How do the PC know that it shall use the boot script in HD(1.2) instead of HD(1.0). boot scripts exists on both places.
2) When I later decide to throw out this 5th tribe version of Gutsy, will my computer instead boot from HD(1.0) as it was before?
3) Is it expected for beginners to be able to understand all this and to be able to trouble shoot it? I think it the graphical installation interface for the booting part is terrible. You can never know what will actually happen.
4) Since I made the install of Gutsy, my Feisty installation does no longer acknowledge any swap partition (neither 5 or 6). Can I correct this easily.


1- Grub is what tells the OS which kernel to boot from. See [this link]("http://users.bigpond.net.au/hermanzone/p15.htm") for VERY detailed info. A complete grub resource it is.

2- It will if you edit the /boot/grub/menu.lst and tell it to do so. If Gutsy is set as the default kernel to boot into that is.

3- Yes and No. Mainly yes. It is *you* after all that made the decision to install an unfamiliar OS to your computer (kudos to you for doing so... its uncharted water for you, but you should still do a lot of reading prior to plopping in the hot new cd you just burnt). If you don't have any luck researching the problem on your own, whether by using google, or the search function on the forum... then a lot of us here are willing to help.

4- Easily is a relative term, for sure. Post the output of the following command:
> 
sudo fdisk -lsu

and then

> blkid

---

### Post by meierfra on 2007-08-31
> 2- It will if you edit the /boot/grub/menu.lst and tell it to do so. If Gutsy is set as the default kernel to boot into that is.

Yes, but grub will no longer work since it will look for instruction in the Gutsy install, which no longer exists. Thus  grub needs to be reinstalled.

---

### Post by southernman on 2007-08-31
lol - ok! NOT true... *mudders - at least I think not* :p

He didn't remove GRUB from the MBR meirerfra. It's totally still there. simply editing the grub menu list will tell grub which kernel to boot from... easy peasy.

---

### Post by meierfra on 2007-08-31
> **southernman said:**
> lol - ok! NOT true... *mudders - at least I think not* :p

... didn't remove GRUB from the MBR ... It's totally still there. simply editing the grub menu list will tell grub which kernel to boot from... easy peasy.


Grub is still there, but it changed. The MBR contains the information where "menu.lst" is located.  It now looks for the menu.lst file in   Gutsy, that is (hd1,2).

---

### Post by southernman on 2007-08-31
> **meierfra said:**
> Grub is still there, but it changed. The MBR contains the information where "menu.lst" is located.  It now looks for the menu.lst file in   Gutsy, that is (hd1,2).

Ok.. I buy that and a bushel of peas. ;)

You are right.. and I am wrrr wrrrrrrr wr wrrrrrrrong. *whew*

---

### Post by df9517 on 2007-08-31
Alright, many thanks to you both, Answered my questions very well really.

Just one thing about the beginner comment I had. This is not a Gutsy related problem. Exactly the same problem would happen to Feisty if I install two Feisty on the same drive.

But if you tell me, beginners should not install two Ubuntu installations on the same drive, THEN I can agree.

However, I still think that the graphical interface for installation can be improved a lot when it comes to the boot part. You can now hardly control it at all.

---

### Post by southernman on 2007-08-31
Your welcome Daniel. :) Are you now able to boot into Feisty normally?

It isn't really a beginner should or should not do something as much as it is in being prepared to handle the consequences of what may be the end result, overall. That and having a LiveCD handy if you have no other computers that you can get on the web with.

I've only tried the GUI installation method once and I agree with your point. It DOES leave a lot to be desired as far as control is concerned. I restarted my computer and put the alternate cd in the tray to use the familar text (ncurses style) based installer. It's really quite intuitave to use, just read each screen as you go along. You have this text based installer available from the LiveCD, if I recall correctly.

---

### Post by df9517 on 2007-08-31
Yes I succeeded to reinstall grub from live CD and point to the partition I wanted. That was very easy once you knew how to do ( i followed the advice in the link above.

Also I fixed the swap using your hint above. Next time I will not install more than one swap,

Regarding the graphical installation. Isn`t it really stupid though, that Gutsy installs itself correctly in HD1, install grub in HD1, install boot loader in the new Gutsy partition BUT IN menu.lst the bootloader address is HD 0 !!!!!!!!!

Is this just a Gutsy thing? I am sure Feisty does the same.

I agree graphical installation sucks. I use barebones installation from minimal CD image these days actually.

Finally, thanks for quick and perfect answers.

---

