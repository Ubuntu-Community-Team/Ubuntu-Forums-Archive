---
title: "Windows 7 plus Truecrypt plus Ubuntu 12.10 plus Luks encryption"
date: 2012-12-30
forum: General Help
---

### Post by optimumpro on 2012-12-30
People experience lots of problems with Windows 7 and Ubuntu 12.10 both encrypted (Truecrypt and Luks) and installed on the same machine. There are different methods for different versions of Ubuntu, which involve identification of correct partitions and typing multiple commands. Most options involve alternative CDs, which are no longer used in Ubuntu 12.10.  
 
 The idea is to have:  2 partitions for Windows; 2 partitions for Ubuntu; installation of  Windows 7 first;  then Ubuntu 12.10 (with Luks); automatic Grub repair via graphical interface; and  Truecrypt.  At Truecrypt prompt, you will either enter a password to load Windows or press &#8220;Esc&#8221; to load Ubuntu (after entering your Luks password). This works in Ubuntu 12.10, which unlike Kubuntu or its other brothers, has an option to have a logical partition with encryption in its installer's "something else" option. Here are simple instructions:  
 
 You need the following:
 
 1. Ubuntu 12.10 live CD;
 2. Windows 7 CD; and
 3. Boot repair tool.
 
 First, start Windows and choose custom install.  Pick the size for your Windows 7 partition. Windows will automatically create a 100mb additional boot partition for itself. Leave the rest of your space unallocated. Install Windows and configure it the way you like it. Next, insert Ubuntu 12.10 CD and reboot your computer. Start installation. At installation type prompt, pick &#8220;something else. &#8220; Next, you will be taken to partition editor. You will see your 2 windows partitions and perhaps some other stuff depending on your computer. Highlight "free space" and create your Ubuntu boot partition by clicking &#8220;+&#8221; in the left bottom corner of the partition editor.  Boot partition is usually about 250mb in Ubuntu 12.10. Pick the size of your boot partition, set it as /boot and use it as Ext2 or 4. Leave other options untouched. In other words, you will be creating a logical partition with boot mount point. Click OK. Next, you will again be presented with partition editor reflecting your newly created boot partition. Highlight "free space" again and create your root partition for Ubuntu install. Pick the size and this time use it as &#8220;physical volume for encryption.&#8221;  You will immediately be presented with an option to enter your Luks password. Do it  and press OK (there will also be an option to overwrite your empty disk space, which is optional). You are not done yet. Once you get to the partitioner again, you will see you newly created second partition as &#8220;dev/mapper/sda*.&#8221;  Now, highlight it and choose &#8220;change&#8221; (again in the left bottom corner). This time, set the mount point as root, i.e. &#8220;/&#8221; and use Ext4.   Next, you will again be taken to the main partitioner window, which should show your boot and root partitions. DONE. Install your Ubuntu.  
 
 Once you are finished and reboot, you wouldn't be able to get into your Ubuntu, because unlike an alternative CD (which Ubuntu no longer uses), 12.10 doesn't let you choose where to install Grub. In addition, you disregarded installer's suggestion to set Ubuntu alongside Windows 7 (in that case,  you wouldn't have been able to use Luks full drive encryption). As a result, Grub has no idea about your windows 7.  
 
 Hence, you reboot with Ubuntu live CD and choose &#8220;try ubuntu.&#8221;  Now, this is crucial: click on your Luks encrypted drive icon (which should be visible on your desktop) and enter your password. Your drive will be unlocked and mounted. Next, get Boot Repair tool by entering the following in your terminal:
 
 **sudo add-apt-repository ppa:yannubuntu/boot-repair** [B]
sudo apt-get update[/B] [B]
sudo apt-get install -y boot-repair[/B] 

 Open Boot-Repair tool and let it work. It will examine your configuration and offer options. Choose recommended repair. Boot-repair will start working. At some point, it will instruct you to enter a number of commands in terminal. Do it (copy/paste). Then finally, your Grub will be repaired and properly installed. Reboot your computer and you should get to a familiar grub menu with options for Ubuntu and Windows. Make sure that you can boot both. Next, load Windows 7 and install Truecrypt. Start encryption wizard.  Choose to encrypt Windows 7 partition. Use multi-boot option. Truecrypt forces you to create a recovery CD and to test its boot loader before actual encryption takes place. Do as required and reboot your computer. You should be presented with a Truecrypt prompt. At that point, if you enter your Truecrypt password, you should be able to load Windows. If you press &#8220;Esc&#8221; you should get to Grub menu. Once you pick Ubuntu, you should get your Luks password prompt.  Again, make sure that you can load both OS. Then encrypt your Windows partition in Truecrypt.  
 
If something goes wrong, you have Truecrypt recovery CD to take care of Windows 7 and Ubuntu CD to help your Ubuntu 12.10. Good luck and Hail to Privacy...

---

### Post by biolizard89 on 2013-01-09
I apologize if this is a stupid question, but how would I modify these instructions if I already have Windows 7 installed (haven't touched the partitioning since purchasing the computer with Windows 7 preloaded)?  I'd prefer not to reinstall Windows 7, particularly since I'm not sure I still have all the OEM discs.

Thanks.

---

### Post by optimumpro on 2013-01-11
> **biolizard89 said:**
> I apologize if this is a stupid question, but how would I modify these instructions if I already have Windows 7 installed (haven't touched the partitioning since purchasing the computer with Windows 7 preloaded)?  I'd prefer not to reinstall Windows 7, particularly since I'm not sure I still have all the OEM discs.

Thanks.

 It is possible to install Ubuntu on top of already installed windows 7, but you obviously need at least 2 partitions for your Ubuntu installation. You can try to use Windows to shrink your existing partitions, but it didn't work in my case: I would always get a not enough space error, although there was plenty of space available on my hard drive. Also, keep in mind that if your Windows 7 is already encrypted, you will need to decrypt it first unless you have a Truecrypt recovery CD. Otherwise, the instructions are the same.   On some computers, you don't even need boot-repair to fix your grub. So, once you have installed Ubuntu (on top of Windows), reboot, and if you get into Grub menue and both Windows and Ubuntu could be booted, then you are fine to proceed with encryption without boot repair.  Also, you might want to look at my post regarding dual boot encryption using Diskcryptor instead of Truecrypt:   [http://ubuntuforums.org/showthread.php?t=2100694&highlight=diskcryptor+windows](http://ubuntuforums.org/showthread.php?t=2100694&highlight=diskcryptor+windows)

---

### Post by biolizard89 on 2013-01-14
> **optimumpro said:**
> It is possible to install Ubuntu on top of already installed windows 7, but you obviously need at least 2 partitions for your Ubuntu installation. You can try to use Windows to shrink your existing partitions, but it didn't work in my case: I would always get a not enough space error, although there was plenty of space available on my hard drive. Also, keep in mind that if your Windows 7 is already encrypted, you will need to decrypt it first unless you have a Truecrypt recovery CD. Otherwise, the instructions are the same.   On some computers, you don't even need boot-repair to fix your grub. So, once you have installed Ubuntu (on top of Windows), reboot, and if you get into Grub menue and both Windows and Ubuntu could be booted, then you are fine to proceed with encryption without boot repair.  Also, you might want to look at my post regarding dual boot encryption using Diskcryptor instead of Truecrypt:   [http://ubuntuforums.org/showthread.php?t=2100694&highlight=diskcryptor+windows](http://ubuntuforums.org/showthread.php?t=2100694&highlight=diskcryptor+windows)
Excellent, thank you for the information.

---

### Post by BenWhitey on 2013-02-19
I'm having trouble following these directions.

Everything is fine until I encrypt my windows partition with truecrypt and then I am unable to boot into ubuntu. When I push escape it can't find my ubuntu partition. If windows is unencrypted then I can boot either ubuntu or windows from the grub menu following boot-repair.

---

### Post by aarons6 on 2013-02-20
why dont you use truecrypt for the linux install too?

thats how i have it setup.

---

### Post by BenWhitey on 2013-02-20
system encryption in truecrypt does not work with non-windows operating systems.

---

### Post by aarons6 on 2013-02-20
> **BenWhitey said:**
> system encryption in truecrypt does not work with non-windows operating systems.

what?

im not understanding what you mean.. 

seems to work fine for me?

---

### Post by BenWhitey on 2013-02-20
[http://www.truecrypt.org/docs/?s=sys-encryption-supported-os](http://www.truecrypt.org/docs/?s=sys-encryption-supported-os)

You need to chain your bootloaders in order to get it to work

---

