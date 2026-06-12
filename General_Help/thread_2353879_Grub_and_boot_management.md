---
title: "Grub and boot management"
date: 2017-02-26
forum: General Help
---

### Post by EddieJoePopcorn on 2017-02-26
My apologies: I pasted this in from a word processor that showed single spacing, but it came out double spaced. Don't know how to avoid this. 

I have Windows 7 installed and working on drive C, and two Linux installations  on drive D (Ubuntu and Mint). Ubuntu is the primary installation on D, i.e.,  it controls the startup grub. Prior to encountering the problem I am writing  about, boot control was via the Windows boot manager, which defaulted to Windows 7, with "Linux" as the second entry. Selecting Linux went to the grub on drive D, giving me the choice of selecting Ubuntu (the default), or Mint. I  was perfectly happy with this arrangement; alas, I ran an update on Ubuntu, which modified the startup as follows:

     Ubuntu (default boot)

     ...

     Windows 10 boot loader (see note below)

     Windows Vista boot loader (ditto)

     ...

     Linux Mint

Notes: Windows 10 should read Windows 7; don't know how it got this way. Also,  Windows Vista is bogus, and I haven't a clue where it came from, unless it's from an old Windows 10 installation that I have deleted. 

 To get to Windows 7, I have to select the 10 boot loader, which brings up the old Windows boot loader menu:

     Windows 7 ...

     Linux

Selecting Linux takes me back to the Ubuntu display. I want to restore the Windows boot loader menu, with 7 the default operating system, and Linux pointing to the Linux choices. I have studied the Ubuntu grub files, and it's way too complicated for me to attempt any edits.

Finally, we come to my two questions: 

 1. On Windows I use the free program EasyBCD to manage the Windows boot  sequence, which it handles nicely. I plan to purchase the non-free version, which apparently can manage grub boots as well. I am wondering if there exist any similar programs on Linux for managing the boot sequence.

 2. I find the Windows boot manager to be relatively easy to understand. However, Linux booting is mystery. As I understand it, Linux places its grub file on the beginning of my drive D, and that corresponds to the old arrangement I have described above, so when I select Linux, the boot process  is transferred to the grub on drive D. However, in the new arrangement, Ubuntu  must have modified the Windows boot loader, or installed the grub on drive C so that it lists the Windows boot loader as one of the options. Where can I find extensive and reliable information on the Linux boot  process, and hopefully some kind of software for managing it all?

---

### Post by yancek on 2017-02-26
If I understand your post, you had a windows 7 install on one physical hard drive and Ubuntu and Mint on a second physical hard drive.  You had windows in the MBR of the first drive and used EasyBCD to chainload to the Ubuntu system on the second hard drive.  Is this correct?  I would not expect a standard 'update' to make the changes you report.  Probably the best way to get help is to go to the site below while booted into Ubuntu and download and run the boot repair software.  Make sure that you select the option to "Create BootInfo summary" and do not make any changes.  You will get a link which you can post here that will enable us to view details on your boot files and make realistic suggestions.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

> Ubuntu  must have modified the Windows boot loader, or installed the  grub on drive C so that it lists the Windows boot loader as one of the  options

That is probably the case and we can determine that with the output from boot repair.  I don't know how that would happen.  I have Ubuntu and Mint installed on an external drive.  I use a third system as the primary bootloader to boot both Ubuntu and Mint.  If I update-grub from Ubuntu or Mint it does not make the kind of changes you report, it doesn't overwrite the MBR but simply creates a new grub.cfg file.  Done this dozens of times with the same result.  

The naming isn't really significant since windows has been using the same boot files since vista and that can be easily changed.  I'm not sure how Grub decides whether vista, 7 or whatever is installed.  Anyhow, run the boot repair and post the link.

---

### Post by oldfred on 2017-02-26
Post link as suggested by yancek.

Grub install defaults to drive seen as sda. And install or reinstall needs to use the Something Else install option so you can change default. All other install options only use default of sda.

We do not recommend EasyBCD. But some that primarily boot Windows use it.
EasyBCD uses the very old grub4dos to chainload to the grub2 install. And it normally requires you to install grub to a partition. And grub2 does not really fit in a partition boot sector, so it has to convert to hard coded addresses which is not reliable, as they may change on updates or even fsck.

With two disks, I think you can use EasyBCD as long as you have grub in MBR, not in any partitions PBR.

Better to just use grub & Windows boot loaders in each MBR.
But with grub in MBR of sdb, you can boot directly from it, and it will offer to boot Windows.
And with Windows in MBR of sda, you can directly boot Windows from BIOS if issues booting.
Grub does only boot working Windows, so sometimes you need to directly boot Windows (and maybe f8 for repair console) to run chkdsk or make other repairs.

---

### Post by EddieJoePopcorn on 2017-02-26
Thanks to qfff for fixing the double spacing problem.

Thanks to jancek and oldfred for very useful information. I have my work cut out for me! Will report back after following your leads.

---

### Post by EddieJoePopcorn on 2017-02-26
[http://paste2.org/Fz244bhF](http://paste2.org/Fz244bhF)

---

### Post by yancek on 2017-02-27
Your boot repair output shows you have two hard drives with sda the 298GB drive and sdb the 465GB drive.  The first partition on both drives has a windows install including windows boot files.  They include the boot files used with the BCD bootloader (vista and newer) as well as the old boot.ini, ntldr and NTDETECT.COM which are used by EasyBCD.

You have Grub code in the MBR of sda pointing to the Ubuntu partition on the other drive and windows code in the MBR of sdb where you have Ubuntu and Mint so if you want to use the windows bootloader using the third party software (EasyBCD), you probably need your windows 7 installation DVD to repair the MBR of sda.  If you install Grub to the MBR of sdb, you should be able to boot all three systems from that as there are already correct entries for Ubuntu, Mint  and windows in the grub.cfg file.

---

### Post by oldfred on 2017-02-27
You can probably use Boot-Repair's advanced mode to install a Windows boot loader & grub to sdb.
Do not use auto fix as that just installs grub to all drives.
        [https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/) 
    
 How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

### Post by EddieJoePopcorn on 2017-02-27
Wow, what a mess! Thanks for the info; now back to work. (I won't mark this as solved just yet.)

---

### Post by EddieJoePopcorn on 2017-03-03
After a considerable amount of study, I finally managed to get the boot-repair file downloaded to my Ubuntu desktop, and to get the ISO image installed on my Lexar jump drive. However, when I attempt to install the ISO on a DVD, this device, whose presence is recognized by Ubuntu, shows up greyed out during the install process. To make matters worse, my computer fails to boot from the jump drive, despite its being set as the first boot device in the (legacy) BIOS. It will boot from a CD only if the CD is recognized as a Windows compatible disk, which I assume is also the reason why it won't boot from the jump drive. As a last resort I used my Windows install disk to "repair" Windows, but this had no effect on the boot sequence. Apparently, Ubuntu has completely taken over the boot process, and I'm stuck with it. Of course, all I want to accomplish is for it to boot automatically into Windows. Any suggestions, before I give up altogether?

---

### Post by oldfred on 2017-03-03
Better to use the Ubuntu live installer. Same as you used to install.
And just add Boot-Repair to it.

How did you run Boot-Repair's report in post #5?

---

### Post by EddieJoePopcorn on 2017-03-03
I ran the boot installer directly from the web site, I think. This was before I downloaded the boot package, which took over two hours (and thereby lies a tale, which I have to take up with my internet provider). If I can figure that out, I'll post an explanation here. Meantime, I'll follow your suggestion.

---

### Post by EddieJoePopcorn on 2017-03-04
Oldfred inquired, How did you run Boot-Repair's report in post #5? I have found that, serendipitously. If you go to [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info), you will see the following two commands:

     sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update
     sudo apt-get install -y boot-info && boot-info

The first downloads the boot-repair file, and the second generates the boot-info (without downloading the boot-repair file), giving you the option of saving the result to a local file, or posting it on the web. Note: I had to close all windows except terminal, else I got a conflict on running the apt-get. PS: Not sure, but the boot-repair file might have to be present in order to extract the boot-info.

---

### Post by EddieJoePopcorn on 2017-03-04
Oldfred inquired, How did you run Boot-Repair's report in post #5? I have found that, serendipitously. If you go to [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info), you will see the following two commands:

     sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update
     sudo apt-get install -y boot-info && boot-info

The first downloads the boot-repair file, and the second generates the boot-info, giving you the option of saving the result to a local file, or posting it on the web. Note: I had to close all windows except terminal, else I got a conflict on running the apt-get.

---

### Post by EddieJoePopcorn on 2017-03-07
I came across a reference to Grub Customizer, and decided to try it. Installation went smoothly, and the program works like a charm! I was able to delete the bogus grub entries, and move Windows to the top, so as to boot into it automatically. Initial problem solved. I recommend this program wholeheartedly.

While attempting to use boot-repair, it occurred to me that the DVD reader was greyed out because I hadn't mounted it. Duh! Live and learn.

Many thanks to **oldfred **and **yancek** for their generous help with this problem. I have learned a heck of a lot about grubs (not the garden variety).

---

