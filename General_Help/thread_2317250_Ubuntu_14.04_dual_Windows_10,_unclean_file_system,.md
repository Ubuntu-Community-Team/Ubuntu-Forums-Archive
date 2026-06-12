---
title: "Ubuntu 14.04 dual Windows 10, unclean file system, hibernate"
date: 2016-03-14
forum: General Help
---

### Post by redmorning on 2016-03-14
Hello,

I have a laptop (ACER 3820TG) with a dual boot of Ubuntu 14.04 and Windows 10. A few days ago, laptop passed to hibernate mode because the lack of battery; while windows OS was running. Then I plugged it to power and booted. Unfortunately the system went in an unstable mode. It can't find the grub so the OS's installed. The result is "Unknown file system and grub rescue".  I created a clean startup disk (live USB) with 14.04 as I always do in these situations to fix the grub but I couldn't succeed to launch live USB (I verified the live USB in another laptop -same model with same OS's-) It stuck in splash screen of Ubuntu with blinking five point. When I press ESC for the log, here is what I see:

[ATTACH=CONFIG]267818[/ATTACH]

I can't understand why live USB checks existing file system when booting (as you can see in the screen shot, it checks sda1, sda2 and sda3).
I also tried to boot in safe mode but no luck. Detaching and reattaching the battery doesn't work either.
I decided to ask for help to the community.

Thanks ins advance.

---

### Post by yancek on 2016-03-14
The image you posted explains the problem which you indicate in your post.  Hibernation, you need turn off anything related to hiberation/fast boot in the BIOS.  Linux systems won't mount an ntfs partition which is hibernated.  You need to fully shut down the computer and try mounting read only as suggested in the output.  If you do get to windows, run chkdsk.

---

### Post by redmorning on 2016-03-15
Hi yancek,
Thanks for your help. There is not any option about hibernation or fast boot in BIOS. I shut down the computer many times and also de-attached/attached the battery; if these are what you mean by 'fully shut down'.  I have no tool to mount any partition, I don't even have a command prompt. Live USB didn't work as I mentioned before. 
All I have is a standard "grub rescue" command line where I don't have knowledge and I couldn't find any trustful directions  at this point on internet.

---

### Post by yancek on 2016-03-15
windowss 8 and later default to always on hibernation so it appears the system is booting faster.  Do you have the windows installation media or a windows Recovery CD?  If you get to a command prompt with either, try running chkdsk on those 3 partitions.  Maybe the link below will help.

[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by redmorning on 2016-03-15
I Read about Windows default option for fast boot/hibernation. Unfortunately ubuntu was the first OS in grub list. 
Laptop has a recovery partition. Before, I was able to access rec partition by pressing F10 at startup but it doesn't work either. 
I'm in a such case where it is also impossible to format the PC! I have really important data in one partition but I started to loose my hope after reading similar cases in forums for hours...

---

### Post by yancek on 2016-03-15
Did you change the boot priority in the BIOS to set the usb drive first so you can boot it?  You should have a boot tab with boot priority listed under it to change this.    If you manage to get Ubuntu booted, take a look at the link below which may help.

[http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation](http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation)

---

### Post by redmorning on 2016-03-16
I changed the boot priority. Here is what happens when I boot from live usb (14.04 Ubuntu):

- the purple screen appears for a second with a white keyboard icon and another icon at the bottom. Normally I used to have a loading screen of Ubuntu in the next step but instead of that i see a black log screen with "failed command: READ FPDMA QUEUED" error (as you can see in threads first post) and after 4-5 sec it passes to Ubuntu loading screen (five point). Whenever I press a key as points blinking, the error log (first post) appears. Desktop never comes (waited minutes and gave up after seeing those error logs)
- Once, I pressed enter key as I saw the purple screen (with logos at bottom) and old Ubuntu installation screen appeared (1-Install Ubuntu without modifying system 2- Check file system 3- Intall Ubuntu ...) I tried all options but each try ends with same error log.

The thing is, I can't figure out why computer try to analyse/check disks when I boot from live usb. That's where I stuck. All my hands are tied up.

---

### Post by redmorning on 2016-03-18
Any suggestions? I can't even format the computer. I searched about 'grub rescue' scenarios but couldn't find a reliable documentation or information for steps to follow.

---

### Post by LostFarmer on 2016-03-18
can you get into the comps firmware setting by pressing "ESC" when you first see the ACER  logo ?  If so , try to find the boot options- if you see MS Windows put it first.  Due to all comps are different can not give you step by step, would say find the online manual and read it.  If you can find the manual post a link and more help might be provided.

You could pull the hdd and attach it to a different comp via usb, and likely be able to fix.

Can try recovery from grub repair: [https://www.howtoforge.com/tutorial/repair-linux-boot-with-grub-rescue/](https://www.howtoforge.com/tutorial/repair-linux-boot-with-grub-rescue/)  -- have your USB stick and point the recovery commands to its grub, in case the installed grub files has a problem. ( I have never had to use grub recovery so not sure).

---

### Post by redmorning on 2016-03-20
> **LostFarmer said:**
> can you get into the comps firmware setting by pressing "ESC" when you first see the ACER  logo ?  If so , try to find the boot options- if you see MS Windows put it first.  Due to all comps are different can not give you step by step, would say find the online manual and read it.  If you can find the manual post a link and more help might be provided.

You could pull the hdd and attach it to a different comp via usb, and likely be able to fix.

Can try recovery from grub repair: [https://www.howtoforge.com/tutorial/repair-linux-boot-with-grub-rescue/](https://www.howtoforge.com/tutorial/repair-linux-boot-with-grub-rescue/)  -- have your USB stick and point the recovery commands to its grub, in case the installed grub files has a problem. ( I have never had to use grub recovery so not sure).

Hi LostFarmer,

Thanks for your suggestions. Here is what I did:
- I pressed "ESC" when I first see the ACER logo and I could view the firmware settings screen for only 20-30 ms. I was able to take a photo of the screen (which has only one option for setup-which is standard setup-). Here is the screen picture: 
[ATTACH=CONFIG]267905[/ATTACH]
Unfortunately this suggestion has taken me nowhere -No boot options- (Of course I'm able to reach/change the boot options from standard setup. I thought that you were talking about another boot option)
- Pulling the HDD will be my last option regarding that it is the hardest and most solid way.
- I read about "grub rescue" option from the link that you suggested. (I admit that I'm not so brave about executing commands in this step) I could find my EXT2 (root) partition but not my /boot partition, which is apart. So I couldn't proceed. Here is what I did and how looks my partitions: 
[ATTACH=CONFIG]267906[/ATTACH] 
[I]I know that I have these partitions:
[LIST=1]
[*]Windows C (NTFS)
[*]WinRec (Recovery-NTFS)
[*]Windows D (Fat32) (where I keep my important stuff)
[*]/ (Ubuntu root)
[*]/boot (Separate boot partition)
[*]Swap
[*]Not sure about the seventh one.
[/LIST]
I found a [video]("https://www.youtube.com/watch?v=3jkCrKrQXuk") on reinstalling grub from "grub rescue" but in that system, boot is under "/" directory.

[/I]

I think "grub rescue" is my ultimate alternative. I need help in this step.

Thanks.

---

### Post by oldfred on 2016-03-20
As the screen says at the bottom did you press f2 to get into UEFI/BIOS?

If you can boot live installer:
 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by redmorning on 2016-03-21
Yes, I pressed F2 and jumped into the BIOS. I could get into the BIOS before but changing boot order and booting from live USB doesn't work (I explained what happens in this case in post #7 in this thread: [http://ubuntuforums.org/showthread.php?t=2317250#7](http://ubuntuforums.org/showthread.php?t=2317250#7)). It was also my repair tool for years.
System says that it can not mount NTFS partition because it is locked due to a hibernate issue; that's what I understand and see in the logs.
What I know till today is when one boots from live CD/USB system doesn't/mustn't check existing partitions but I think this is not totally true; this is where I came.

---

### Post by oldfred on 2016-03-21
If you left Windows hibernated, you have to turn that off.
It looks more like a BIOS install, so you need to use your Windows repair flash drive to restore a Windows boot loader and possibly run repairs.
You can use Boot-Repair to temporarily restore a Windows type boot loader that should boot Windows, but cannot do any other Windows repairs.
Once Windows fast start up is off then live installer or Ubuntu grub can be restored to MBR.

       Fast Startup off (always on hibernation)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold)

---

### Post by redmorning on 2016-03-22
[LIST]I created a windows 10 installation USB from official microsoft download site: [https://www.microsoft.com/en-gb/software-download/windows10](https://www.microsoft.com/en-gb/software-download/windows10)[/LIST]
[LIST]Boot from this live USB[/LIST]
[LIST]*(Standart Windows Screens)* Language Selection->Repair or Install->Advanced Settings->Command Prompt *(Order or menu names may be a little bit different) *[/LIST]
[LIST]In "Command Prompt" I typed
```
bootrec /fixmbr
```
than
```
exit
```[/LIST]
[LIST]Live USB took me to previous menu. I chose *Exit and continue with Windows 10*[/LIST]
And voila! (:

Now I need to reinstall grub from "live USB of Ubuntu" to get back my dual system again.

Thank you oldfred, LostFarmer, yancek and all community.

---

