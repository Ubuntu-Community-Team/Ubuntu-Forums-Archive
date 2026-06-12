---
title: "Ubuntu unable to boot in HP uefi machine"
date: 2015-05-14
forum: General Help
---

### Post by george110 on 2015-05-14
I've tried to access an installed Ubuntu on the hard drive of this computer. As I was having problems with a " no OP system error " on the hard drive it was suggested that I download Boot disc repair & forward the log result for inspection by some experts. I have done just that & the log of interest can be found at [http://paste.ubuntu.com/111251101](http://paste.ubuntu.com/111251101). If anyone can advise me what to do next I'd be grateful.

---

### Post by iojedaperez on 2015-05-14
Following the link send me to this message "The Paste you are looking for does not currently exist.", anyway i dont understand if you want simply to access the contents of the partition or to recover the boot because its broken. In the first case you only need a ubuntu live cd and once booted click on test ubuntu then you can mount the disk partition and see the contents. If what you want is to recover the boot, there are several guides on how to do that, here you have one [http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd](http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd)

---

### Post by george110 on 2015-05-14
Thank's iojedaperez for offering some assistance.
It's a pity that the log didn't open so to speak. The first time I ran Boot-repair & asked for the logs it printed something like this & I don't know whether what I am about to write about what I think was in the log is completely correct or even helpful. The second time I ran Boot- repair it didn't print the log but rather that which you have which turns out to be unhelpful. From what I can remember of the log it said something like this . Partition the Bios to an amount > than 1 or 2 Mb's then there followed some commands to place in the terminal I think or something like that & it suggested with such information to proceed to the forum & seek advice or help. I think there was a grub thing in it also.
Do you think I ought to wait until the log opens for someone & proceed from there ?

---

### Post by coffeecat on 2015-05-14
@george110, I suggest you run boot repair again and get another pastebin link from the bootinfo summary option. Don't run any repair option. It would be inadvisable to do anything until a report on your system is available. Pastebin URLs usually have 8 numerical digits at the moment, and yours has nine. It is possible you accidentally added another numeral when you transcribed the link.

**Edit:** This link added for reference: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by george110 on 2015-05-14
I did that & tested the webpage & I've got some data this time. [http://paste.ubuntu.com/11127066](http://paste.ubuntu.com/11127066)

Thank you for your patience

---

### Post by coffeecat on 2015-05-14
I've only had a quick look through the pastebin report - coffee hasn't kicked in yet this morning! - but the suggested repairs at the end are inappropriate, which worries me. It says it wouldn't install grub-efi and would install grub to the mbr, which is inappropriate. You have a UEFI system. It also says it cannot find an EFI partition, yet you have one at sda1. I wonder if the problem is as simple as the lack of a boot flag on sda1. 

Boot up an Ubuntu live session and open gparted once you get to the desktop. Select sda1, then Partition (menu) -> Manage Flags. Select the boot and esp flags and allow that to complete. Now try to boot the system.

---

### Post by george110 on 2015-05-14
I did the alterations on the USB & then re-installed the altered version as a new installation on the hard disc- deleting the previous one. As the same problem persists ran Boot- repair & here is the latest log [http://paste.ubuntu.com./11140480/](http://paste.ubuntu.com./11140480/)

---

### Post by george110 on 2015-05-15
Going further I actually ran the Boot repair option culminating with the following log [http://paste.ubuntu.com/11141041/](http://paste.ubuntu.com/11141041/). This could be more helpful. I can always reinstall Ubuntu 14.10 with a fresh start if you like.

---

### Post by coffeecat on 2015-05-15
Does it boot after you ran the repair?

Did you read the last line of the boot info report and configure your efi BIOS accordingly?

Ubuntu 14.10 has only 2 months' of life left. Support ends in July. If you are thinking of doing a fresh install of Ubuntu, you would do better to install the latest version, 15.04, which will be supported until January 2016, or the current LTS, 14.04, which is supported until 2019.

---

### Post by george110 on 2015-05-15
No, it didn't boot after the repair - that's why I sent you the log. How do I go about making my BIOS boot on sda1/EFI/ubuntu/shimx64.efi file. That's the last line on the log I sent you. What do I open & what do I write ?

Have taken notice of your call for 15.04. Is it still possible for you to continue with 14.10 for a little while to see whether we can get it to boot from the HHD ? I should think 15.04 could be in the same boat as 14.10 with regards booting. Of course we wouldn't know till we try it. In the mean time though will you still send me the instructions on BIOS boot commands?

---

### Post by coffeecat on 2015-05-15
I only suggested thinking of 15.04 if you are going to be doing a fresh installation as you indicated you might be doing in post #8. If you want to get your current installation booting, there's no reason why you shouldn't carry on with 14.10. There's a couple of months life left in 14.10 and it will be easy to upgrade.

To get into the BIOS, you need to press a special key when the first splash screen appears after switching on. This varies between different makes but is often F2. Your hardware documentation should tell you. Once you are in the BIOS, the configuration pages differ greatly between different makes, but there should be an option to choose the boot order. 

It would be useful if you post details of your hardware - make and model. Some uefi BIOS's have particular quirks and someone with experience of your make might be able to help you with the specifics.

---

### Post by george110 on 2015-05-17
What do you think of this coffeecat. I got in touch with HP & eventually ended up with a chat & it was decided to send me a recovery disc. Presumably, although I doubt it, they are thinking that I will be able to re-install windows 8.1 & then I'd be able to put Ubuntu beside it instead of replacing it. That bios problem was not on their agenda to solve & independantly from the chat the directions from trouble shooting were most unhelpful  & I couldn't even get Bios to accept factory default. I suppose if the worst comes to the worst I could reinstall a complete 8.1 & continue from there as above.

---

### Post by coffeecat on 2015-05-17
You've told us that the machine is a HP, but not the model. 

Accessing BIOS in HP machines:

[http://support.hp.com/us-en/product/HP-2000-Notebook-PC-series/5091493/model/5171080/document/c01443329](http://support.hp.com/us-en/product/HP-2000-Notebook-PC-series/5091493/model/5171080/document/c01443329)

oldfred on HP systems and uefi:

[http://ubuntuforums.org/showthread.php?t=2227889&p=13041354&viewfull=1#post13041354](http://ubuntuforums.org/showthread.php?t=2227889&p=13041354&viewfull=1#post13041354)

> Every HP I have seen so far has had issues.
They seem to have modified UEFI to only boot Windows, even if ubuntu entry is in UEFI when viewed directly.

Also: [http://ubuntuforums.org/showthread.php?t=2267597](http://ubuntuforums.org/showthread.php?t=2267597)

Re-installing Windows is not going to help your BIOS problems.

**Edit:** I've amended the thread title in the hope that those with HP experience will notice and be able to advise.

---

### Post by george110 on 2015-05-17
Thank you coffeecat.
 I hope this leads somewhere.
It's beginning to look really difficult.

---

### Post by oldfred on 2015-05-17
HP has modified UEFI to only boot an entry with "Windows" in description. That is not UEFI standard and Ubuntu has a position paper that vendors should not do that.

If only using Ubuntu, not dual booting you can easily change description to read Windows in UEFI, but actually boot grub or shim file. Others that dual boot with HP add or modify the /EFI/Boot/bootx64.efi file to really be shim or grub. That entry is a hard drive entry.

       **D:  **Use efibootmgr

 **d1**:  If Description has to be Windows then change UEFI description.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

 HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)
It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. 
some also use this: To work around it also rEFInd
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)

Many are dual booting and do the rename of bootx64.efi

 Installing Ubuntu on HP Envy-6  Details of what worked post #11
[http://ubuntuforums.org/showthread.php?t=2123975](http://ubuntuforums.org/showthread.php?t=2123975)
HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

A few give up and install grub in CSM/BIOS boot mode. Be sure to boot Ubuntu live installer in UEFI mode. the message on needing a 1 or 2MB unformatted partition with the bios_grub flag is if you want to convert to BIOS boot on a gpt partitioned drive. You must have booted Ubuntu in BIOS mode and then Boot-Repair thought you wanted BIOS. Usually better to use UEFI. Only a very few systems only work with BIOS.

Boot-Repair ran this and it is in your summary report. It shows Name in UEFI and actual file used to boot. You must be in UEFI mode for this to work from live installer:
 sudo efibootmgr -v


 [http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)

---

