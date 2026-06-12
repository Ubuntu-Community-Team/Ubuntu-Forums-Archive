---
title: "My Dual Boot Does Not Work To WinXP From Grub Menu, Help?"
date: 2020-11-17
forum: General Help
---

### Post by cliff-bjazz on 2020-11-17
Hi,
I have posted here before and you guys really helped fix my issue. 
I have a new problem which is a bit tricky, or at least for me.

Firstly, I installed Lubuntu along side my Windows XP installation using the option to dual boot. When Lubuntu had installed I never tested the dual boot function to see if it worked with launching Windows XP, I just assumed it was fine.
I since went on to upgrade Lubuntu to Ubuntu Full version 20.04, this allowed me to overwrite the previous version whilst still maintaining the option to dual boot to Windows.
A few days ago I tried to test the dual boot, but it didn't work, it just produced a flashing cursor to the top left of the screen and hung there.
I was advised through research to install 'Boot Repair' from within the Ubuntu Terminal. I did this successfully and clicked the 'recommended repair' option. After rebooting I went straight to the Windows OS in the menu to try and boot that, but unfortunately the problem is still there and I cannot boot Windows from the Grub menu.
I was given a URL after the Boot Repair program had finished and I was advised to share it here in the event of an ongoing problem for anyone who may be able to understand what might be wrong.
Here it is:
[https://paste.ubuntu.com/p/675xWKpbPc/](https://paste.ubuntu.com/p/675xWKpbPc/)

I hope this makes sense to you because I have no idea what to do for the best.
Thanks for reading,
cliff.

---

### Post by yancek on 2020-11-17
Your boot repair output shows only a fraction of what is normally available and does not include some important information so I would suggest you run it again and post the new link here.

---

### Post by cliff-bjazz on 2020-11-19
ok yancek I will give it a go, thank you for responding.

---

### Post by cliff-bjazz on 2020-11-20
Hello Yancek,

I did as you suggested and I re-ran Boot Repair. First I ran it and then uploaded the boot report after the initial scan, without completing the repair process, This is the result of that scan:
[https://paste.ubuntu.com/p/7Q4kZxdKmd/](https://paste.ubuntu.com/p/7Q4kZxdKmd/)

Then I ran Boot Repair again and allowed it to complete the repair process after the initial scan, this is the result of that process:
[https://paste.ubuntu.com/p/kG2ccgDWW6/](https://paste.ubuntu.com/p/kG2ccgDWW6/)

But nonetheless, I rebooted after the repair process and my PC still hung with the blinking cursor in the top left corner of my screen after the flash screen etc. 
I don't know if I should have left it blinking for a long time or not, but I was aware that my CPU was not turning over at all during the 'blinking cursor' activity, which could suggest that it had gone dead, I'm just guessing.
I hope that these reports have offered more information than the first one did. I have no way of interpreting them because my knowledge does not extend.
I hope you can help.

Thank you,
cliff.

---

### Post by yancek on 2020-11-20
Clarify please that you CAN successfully boot the installed Ubuntu, correct?
When you select the windows option from the Grub menu, you get a blinking cursor and it fails to boot, correct?

On line 195 of the second boot repair you posted you will see this:

> # /boot/efi was on /dev/sda2 during installation 

That means Ubuntu at some point was installed UEFI which you should not do if you want to use an old OS like XP.  The boot repair output shows that the system is booted in Legacy mode which it would need to be.

Line 38 as well as line 93 show that XP was detected.  The boot repair is still incomplete as it should show the contents of the /boot/grub/grub.cfg file and an entry for XP.  Some other information generally seen is also missing.  Can you go to the /boot/grub/grub.cfg file and look for an entry for windows xp and if it there, post just that entry.

---

### Post by oldfred on 2020-11-20
What video card are you using.
Some that are over 10 years old are not supported or well supported.

---

### Post by tea for one on 2020-11-20
[COLOR="#0000FF"]Line 92[/COLOR] of [https://paste.ubuntu.com/p/kG2ccgDWW6/](https://paste.ubuntu.com/p/kG2ccgDWW6/) shows that the report was created in an installed system.

Is it not more usual to run the boot-repair utility in a [COLOR="#FF0000"]live[/COLOR] session?

---

### Post by oldfred on 2020-11-20
I run it on my working system, just to document system & copy report into /home so it becomes part of backup.
I think I have seen once or twice where it has some issue with updates on a working system, but should normally work.

---

### Post by tea for one on 2020-11-20
@oldfred

I'm sure that some of the actual repair processes of boot-repair will only work if the utility is run in a live session.
I can't identify exactly which options but, in the dim and distant past, I saw a warning [COLOR="#0000FF"]Unable to proceed[/COLOR] followed by [COLOR="#0000FF"]This should be run in a live environment[/COLOR] - or words to that effect.

Apologies, a bit off topic

---

### Post by cliff-bjazz on 2020-11-22
Thank you Yancek, Tea for one, and oldfred.

I looked at your advice and the first thing I did was to run Ubuntu in live mode from the original usb stick with the installation media on. The option to 'try Ubuntu'.
From there I connected an Ethernet cable and managed to download and run Boot Repair. This method did not work either and the result was the same when I tried to boot WinXP. here is the result of the repair process:

[https://paste.ubuntu.com/p/NkYvNsfGFb/](https://paste.ubuntu.com/p/NkYvNsfGFb/)

In regards to your request Yancek,
I found the Grub.cfg file and I found an entry within it for Windows XP. I will try to replicate the entry below:


318 ### Begin /etc/grub.d/30_os-prober ###
319 menuentry 'Microsoft Windows XP Professional (on /dev/
       sda1)' m--class windows --class os
       $menuentry_id_option 'osprober-
       chain-1448A9AE48A98ED4' {
320             insmod part_msdos
321             insmod ntfs
322             set root='hd0,msdos1'
323             if [ x$feature_platform_search_hint = xy ];
       then.........etc

The following on code seems to concern ms dos, although I have no real way to be sure. I hope that what is pertinent is shown here, if not then I could always try to find and add more code.
I also apologise if there is a better way to add code information to forum posts, I could not get the .cfg file to open in Windows 7 notepad, it just changed to mush.

Thank you for all your help,

cliff.

---

### Post by yancek on 2020-11-22
The entire entry for XP needs to be posted which you have not done and once again, the boot repair software failed to include grub.cfg for some reason.  Boot the installed Ubuntu and copy just the entry for XP from it, the entire entry and paste it here.  You can do that by clicking on the ( # ) symbol above the text entry area.

Was XP working/booting prior to this problem?  Grub won't boot a non-working windows, it doesn't actually directly boot windows in the manner it does a Linux system but rather chainloads it and turns the boot process over to windows. 

>  
The following on code seems to concern ms dos,

THe reference to msdoc in this instance simply means you are dealing with a Legacy/CSM system.

>  I could not get the .cfg file to open in Windows 7 notepad 

Not sure how windows 7 got into the equation, you should be accessing the grub.cfg file from the installed Ubuntu and copying it.  A default windows system is not capable of reading or writing to a Linux filesystem, that's the way microsoft wants it so use Linux for Linux filesystems.

---

### Post by cliff-bjazz on 2020-11-22
Thank you Yancek.

1/ My windows XP installation worked perfectly prior to my installing Ubuntu alongside. It was free of clutter and errors and was more or less a fresh install.
2/ I forgot I have Wi-Fi on the Ubuntu machine and so I tried to copy the grub.cfg file to another machine running Windows 7. That is where I made the forum post, sorry about that it was a silly mistake.
3/ I have followed your instruction and copied everything that relates to Windows XP in the Grub.cfg file. This is the only place in the whole file that explicitly references Windows XP, and so everything below that point has been copied and placed within the ```
 tags. 
However, The number lines from the grub.cfg file have not been copied?

[CODE]
### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Microsoft Windows XP Professional (on /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-1448A9AE48A98ED4' {
    insmod part_msdos
    insmod ntfs
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  1448A9AE48A98ED4
    else
      search --no-floppy --fs-uuid --set=root 1448A9AE48A98ED4
    fi
    parttool ${root} hidden-
    drivemap -s (hd0) ${root}
    chainloader +1
}
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

```

There is a lot more code before this which I will post here if you require.
I realise that this is a somewhat 'trying' post, made worse by the fact that I have no knowledge of Ubuntu or coding for that matter, and so most of what you tell me comes as completely new information which I have to first understand before acting on it.
I very much appreciate your help,

cliff.

---

### Post by cliff-bjazz on 2020-11-25
I guess my issue is non solvable then it seems,
That's a real shame, I thought that the dual boot was a real feature, but I guess I will have to reinstall Windows XP and not get to learn Linux for now. 

thanks guys in any case.

cliff.

---

### Post by dragonfly41 on 2020-11-26
I thought of trying rEFInd but yours is older MBR and [rEFInd requires GPT to work]("https://sourceforge.net/p/refind/discussion/general/thread/ce262ab2/?limit=25")..

---

### Post by yancek on 2020-11-26
Your XP entry posted in post 12 above looks correct.  It shows the correct partition and UUID for XP so I don't think that is the problem.  Seems a bit odd that your boot repair fails to provide the complete information generally shown?  I see from your initial/partial boot repair in post 2 that you initially did an EFI install of Ubuntu.  Of course, that would never work to boot a Legacy/CSM install of XP which is what you have.  Boot repair seemed to correct that by installing Grub to the MBR of the drive and removing the /boot/efi entry in fstab.  Not sure what else to suggest without more info.

 > That's a real shame, I thought that the dual boot was a real feature,  but I guess I will have to reinstall Windows XP and not get to learn  Linux for now. 
 

It's certainly possible as millions of people have been dual booting different Linux and windows systems for decades.
You might try repairing your XP b'y reinstalling the XP boot code to the MBR then reinstalling Ubuntu in Legacy mode.  Since you originally installed Ubuntu in EFI mode, you might check the BIOS firmware to see that Legacy/CSM is enabled in the Boot Options of the BIOS firmware.

---

### Post by ajgreeny on 2020-11-26
It is so long since I did anything with XP but I seem to remember that there was a repair utility on the CD/DVD that could repair the boot of XP.
Have you tried booting to your installation disk to see if that offers any hope of a solution to at least get XP booting again, then using a Ubuntu live system you can install grub to the hard disk; not to a partition on the disk, ie /dev/sda, not /dev/sda1 or any other partition.  This would end up similarly to the way suggested above by yancek, but without the reinstall of XP, just repairing the MBR XP bootloader.

When I  first began using Ubuntu 16 years ago I dual booted with XP for a few years with no difficulty, but that was in the days long before UEFI was even available, and it also used legacy grub versions, not grub 2 as we use now. I don't think that should matter

I have no idea what your hardware is but have you considered installing Ubuntu to the whole disk and then using XP in virtual mode using VirtualBox if you have sufficient resources?
I still have an XP installation running in VBox very successfully, though I only boot it about 1 or 2 times a year these days.  It does, however, run fast and would do anything that I needed it for, such as updating maps on my TomTom GPS Satnav device.

---

### Post by cliff-bjazz on 2020-11-28
> **yancek said:**
> 
You might try repairing your XP b'y reinstalling the XP boot code to the MBR then reinstalling Ubuntu in Legacy mode.  Since you originally installed Ubuntu in EFI mode, you might check the BIOS firmware to see that Legacy/CSM is enabled in the Boot Options of the BIOS firmware.

Hello Yancek,
I don't know how to set about doing that, since I cannot get into any part of WindowsXP, (not much good working in the Bios either), but I can do some research. 
Thank you for the idea.

cliff

---

### Post by cliff-bjazz on 2020-11-28
> **ajgreeny said:**
> 
Have you tried booting to your installation disk to see if that offers any hope of a solution to at least get XP booting again, then using a Ubuntu live system you can install grub to the hard disk; not to a partition on the disk, ie /dev/sda, not /dev/sda1 or any other partition.  This would end up similarly to the way suggested above by yancek, but without the reinstall of XP, just repairing the MBR XP bootloader.


Hello ajgreeny,
This is excellent, could I delete the place where Ubuntu is presently installed and reuse the disk space after the new Ubuntu installation to a different partition? I do have the installation disk for Windows XP, and I could give your method a try and see how far I get. It will be worth a try before wiping the hard drive and starting all over again. Luckily I only have mostly legacy games installed on windows because it's more of a test and research legacy machine.

Thank you very much for your input guys,
cliff.

---

### Post by yancek on 2020-11-28
I'm not really familiar with XP so I would suggest you do an online search for "repair MBR on windows XP".  You are a step ahead of most since you have the installation CD which you need.  You should find sites similar to the ones below explaining the process.

[https://www.lifewire.com/how-to-repair-the-master-boot-record-in-windows-xp-2624513](https://www.lifewire.com/how-to-repair-the-master-boot-record-in-windows-xp-2624513)

[https://www.lazesoft.com/windows-recovery/fix-a-damaged-mbr-windows-xp.html](https://www.lazesoft.com/windows-recovery/fix-a-damaged-mbr-windows-xp.html)

If this method is successful you could then use the Ubuntu install medium to reinstall Grub as suggested above.  If you decide to reinstall, there is no need to delete the partition on which you currently hav Ubuntu, just select it as the partition on which to install the OS and make sure you check the format option for that specific partition during the install.

I would also suggest that you delete the EFI partition and make sure that you instal; in Legacy mode.  See the link below which explains how to determine this during the install.  Go to the site at the link below and scroll down to the section titled "Identifying if the computer boots the Ubuntu DVD in UEFI mode".  Results the same with DVD/USB or any medium/

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by cliff-bjazz on 2020-11-29
Thank you very much Yancek,
I never expected such thorough and comprehensive help. I will have a go at this in the week, I'll let you know how it goes.
Thanks again,

cliff.

---

### Post by mastablasta on 2020-11-30
> **cliff-bjazz said:**
>  Luckily I only have mostly legacy games installed on windows because it's more of a test and research legacy machine.


i moved in 2019. i still have XP on another disk, but have not boot to it for a while. i spend time now making old games work on Linux. most of them work now. some out of the box, some need a few libraries. but so far i managed to get 1 with silver rating working perfectly and one with wine garbage rating working well. i use Playonlinux for that as it has a nice GUI. also many XP games run way better on linux. i mean Far cry 2 was slow even at low resolution. but on linux i can have it run on medium and i can barely see a slow down.

what i wanted to say is that after i sucessfuly arranged a dual boot i made a small script that will boot once to windows when i double click the icon on desktop (i use Kubuntu). by default it boots to linux as that is way fatser. when i double click the icon it boots to XP, then i can play a few games or whatever and then when you reboot windows the PC boots back to linux. anyway with playonlinux (wine) i don't have a need to boot to windows. some old games have open engine implementations (Open Jedi Academy, Open Jedi Knight, Doomsday engine for doom, OpenMW for Morrowind...) and they work better then original and make games run natively on linux. i also ran Doom3, Quake4 and the original Pray on linux. so anyway, mayn games work, many games to play, not enough time. :(

the only game i am missing for a bit is League of Legends, but it didn't work well in latest seasons (PC only has single core and it started to struggle with it after certain update).

on the other hand i installed steam on linux and bought the half life pack (most in there run natively), installed CS:GO and Team Fortress 2, Story about my uncle, Kerbal Space Program, Crusader kinds, Company of Heroes... there are a few more native ones available but i don't have time to play so i didn't buy them. oh and we are playing Minecraft a lot with the kids.

---

### Post by cliff-bjazz on 2020-12-01
Thanks mastablasta

Its really interesting to find out that Linux can be good at running legacy Windows games. Maybe in the future I might make this machine strictly an Ubuntu one, and then explore all the possibilities you have outlined to me regarding games.
it sounds like it could be a lot to learn but that might also be fun.

I really appreciate that.
Thanks,
cliff

---

### Post by cliff-bjazz on 2020-12-03
Hi Yancek,

I just tried the fixmbr process with the windows XP Installation CD, now I cannot boot into anything at all. when I boot up I get an error message telling me that the disk cannot be read, and that I should press ctrl-alt-del to restart, it just goes around in that loop.

The fixmbr process on completion confirmed that the master boot record had been written for partition 0, but Windows XP is installed on partition 1 which I find a bit strange. Other than that I have no idea what is wrong.

Thanks,
cliff

---

### Post by yancek on 2020-12-03
Do you have Legacy/CSM boot enabled in your BIOS?
Have you tried booting your windows installation DVD and selecting the repair option and then running chkdsk on the partiiton?  chkdsk with parameters will check to see if the filesystem is corrupted and stry to repair.   You might need to do an online search as to how to access and run it and which parameters to use.
Do you know the exact error since the MBR is not on any partition.

---

### Post by cliff-bjazz on 2020-12-11
Hi Yancek,

Alas, I tried all the great solutions you provided, but my system just would not comply. So I used the installation CD and wiped everything with a new XP installation. It's ok though because I learned a lot through this process. I might try Ubuntu or even a different Distro later on. And who knows, with some research I might succeed next time and get a working dual boot.

Thanks again for all your great input, (and many others who helped also).

Cliff.

---

