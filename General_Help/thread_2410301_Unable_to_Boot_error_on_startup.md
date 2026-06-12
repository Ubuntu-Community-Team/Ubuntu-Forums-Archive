---
title: "Unable to Boot error on startup"
date: 2019-01-14
forum: General Help
---

### Post by chaostheory1000 on 2019-01-14
Hi,

I am unable to boot into Ubuntu 18.04.

I have a dual boot computer and am writing this message through Windows 10 from same laptop.

Problems started when I was unable to delete some files(pdf files) and it was showing error. On restart I ran Memory Test and Hard Drive test, both gave Passed report.

When I started laptop and selected Ubuntu, I got an error saying Computer is in Emergency mode, to use "systemctl reboot" to reboot, etc, I went with option to check log and I found following errors:

> [COLOR=#000000]Couldn't get size: 0x800000000000000e[/COLOR]
[COLOR=#000000]MODSIGN: Couldn't get UEFI db list[/COLOR]
[COLOR=#000000]Couldn't get size: 0x800000000000000e


Please suggest what to do.

Regards.[/COLOR]

---

### Post by yancek on 2019-01-14
Were you ever able to boot into Ubuntu?

> 
Problems started when I was unable to delete some files(pdf files) and it was showing error.

Delete files from where?  Windows?  Ubuntu?  What error showed?

---

### Post by chaostheory1000 on 2019-01-14
Hi yancek . Thanks for replying.

Yes I was using ubuntu itself while deleting those files. After my install, I had no major issues in using Windows as well as Ubuntu.

I deleted those files from ~/Documents/Folder_Name while I was inside ubuntu.

Error message shown was along lines of Path to the file you are deleting does not exist.(error that is shown after incomplete copy)



After this whole incident, I booted using Ubuntu bootable USB and copied that folder for Backup. It is working properly on Windows. 


No system file was touched by me during that session. However I don't remember if Ubuntu updated in that session. 

Regards.

---

### Post by chaostheory1000 on 2019-01-15
Hi,

I tried boot-repair but to no avail.

Now number of  boot options have increased a lot.

Report is [http://paste.ubuntu.com/p/mH6rrPBtdf/](http://paste.ubuntu.com/p/mH6rrPBtdf/)

---

### Post by oldfred on 2019-01-15
First you need to directly boot Windows from UEFI boot menu & turn off Windows fast start up.
Report says Windows is hibernated.
       Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

Have you updated UEFI from HP for your system?
Many need that. And many older HP only wanted to boot Windows or the fallback boot entry /EFI/Boot/bootx64.efi.
And if you updated UEFI or Windows ran updates (which may be why fast start up is on), it may have turned UEFI Secure Boot back on.
UEFI updates and some Windows updates reset UEFI. You have to make sure settings are what you want. I have 5 to 7 UEFI settings, some required and some optional that I have to redo with every UEFI update.

Boot-Repair sees all the HP .efi files for HP repairs in the ESP - efi system partition. Most vendors have those in a separate partition. And you probably do not need them in grub. Boot-Repair creates a new 25_custom script file which you can edit. Some delete or turn off execute bit so not run as part of grub-update.

       
 bootx64.efi Also edit of 25_custom
[http://askubuntu.com/questions/778663/what-is-the-difference-between-windows-uefi-bootmgfw-efi-and-windows-uefi-bkpboo/778705#778705](http://askubuntu.com/questions/778663/what-is-the-difference-between-windows-uefi-bootmgfw-efi-and-windows-uefi-bkpboo/778705#778705)
# Edit 25_custom entries created by Boot-Repair:
sudo cp -a /etc/grub.d/25_custom /etc/grub.d/bkp25_custom
# turn off execute bit or it will run backup also
sudo chmod a-x /etc/grub.d/bkp25_custom
sudo nano /etc/grub.d/25_custom
# Then do:
sudo update-grub

---

### Post by chaostheory1000 on 2019-01-18
Hi oldfred


Thanks for reply and I am extremely sorry for not replying sooner.


Yes, I had realised that Windows FastStart got turned on, I disabled it, but to no avail. Actually I think this update happened after these problems as I was using Windows after quite a long time once was unable to boot into Ubuntu.


I had checked and verified about Secureboot before trying boot-repait but it was not on.


I ended up using boot USB to back up all documents,etc and will be Reinstalling Ubuntu 18.04.


I thought my previous Install was Ok, however would like to hear your comment (I am Ubuntu user from 12.04, however my previous machine was BIOS and MBR rather than new one (UEFI and GPT) about which I have no clue.


Currently I have Windows 10 installed. Current Partition Structure (as shown on Windows diskmgmt) is:
Recovery NTFS OEM Partition 499 MB
EFI system Partition 100 MB
C Drive 200 GB NTFS
D drive NTFS 500 GB for sharing between OS
/ Ext4 60 GB
/home Ext4 170 GB
swap 8 GB


Except for Recovery (OEM Partition) and EFI Partition of 100 MB, all are Primary Partition.


On my Previous laptop, there was no EFI Partition and I had to use Logical Partitions due to limit of 4 Primary partitions.
Also, I did not create EFI partition or Recovery partition and though I understand suggestions say that EFI partition should be 500 MB, I don't want to play with it right now unless suggested as I don't have my Win 10 ISO.


Lastly one more question,


On my BIOS there is an option to load HP default secure keys and one to clear all keys (Once keys are deleted, secureboot gets disabled automatically)


I am in a quandry what to do about it (though I don't think it should matter as Secureboot would be disabled)


Also I was getting Error on fsck failing with error 4.


Another Error that was repeating in all attempts(disbled secureboot, cleared security keys, loaded HP default keys,etc) was 


PKCS#7 signature not signed with a trusted key.




Lastly, Thanks for your patience. I shall mark it for closure once I complete my installation and verify if there are no issues with key or fsck.


Regards.

---

### Post by oldfred on 2019-01-20
I do not fully understand all the HP settings. Users seem to have more issues with HP than other brands, but it may just be all the settings and which are correct.

Anything to do with keys is related to UEFI Secure Boot. I just currently have Secure Boot off. But may turn it on in future. You generally do not want to clear all keys.
If Secure boot is on, you have the default Microsoft key which is also used by Ubuntu. But proprietary drivers must also then have a key. In past, you could only install proprietary drivers with Secure Boot off. But now, even though Canonical cannot sign a driver, a user can if the user believes it is a trusted source.  So, for example to install the nVidia driver, you will get a pop-up to assign your own key. 

With gpt you only have one type of partition, so all are considered primary.

       BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)

---

