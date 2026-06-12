---
title: "Grub disapeared, unable to boot ubuntu 16.04"
date: 2018-03-16
forum: General Help
---

### Post by robingranda on 2018-03-16
I went in my ACER laptop boot options, for no particular reason. I did not change anything, but noticed that Windows 10 was first in the boot order list while Ubuntu was not there at all. I escaped and thought Grub would show up... but it did not and Windows booted.  

Since then, I've been unable to boot on Ubuntu. Windows automatically boots and Grub does not show up anymore.  

In the boot menu, there is only Windows. I'm on UEFI and secure boot is enabled - it wont let me disabled it in the options.

Prior to that, everything used to work just fine. I'm confused!

---

### Post by ajgreeny on 2018-03-16
I suspect you have just had a large Windows update which has rewritten the disk partition table and though the Ubuntu partitions are probably still present, they are not visible any more to the system.
Do not panic just yet and do something silly like reinstalling Ubuntu as that should not be necessary, and you are just one of many dual-booters who have suffered with this problem if my suspicions are correct.

Have a look at these Askubuntu pages for what seems to be the same problem.
[https://askubuntu.com/questions/957117/windows-10-major-update-wiped-grub-how-do-i-recover-partitions-properly](https://askubuntu.com/questions/957117/windows-10-major-update-wiped-grub-how-do-i-recover-partitions-properly)
[https://askubuntu.com/questions/984703/no-option-to-boot-ubuntu-after-windows-10-update-in-dual-boot](https://askubuntu.com/questions/984703/no-option-to-boot-ubuntu-after-windows-10-update-in-dual-boot)

I no longer use Windows so have no experience of dealing with the problems that have arisen with Windows 10 and large updates but with a search you may find more info.

I do not normally point users to google searches but in this case it could be the best way for you to find an answer.
Do a google search with search term **windows 10 updates remove ubuntu site:ubuntuforums.org** you will get a lot of references to this forum's threads about this problem which may help you more than I can.  

Good luck!

---

### Post by robingranda on 2018-03-16
Thanks for your answer, however I don't think it's linked to a Windows update. Windows did indeed run an update yesterday but I've been able to boot on Ubuntu after that. Problems really appeared when I went in the boot options menu !

I've run a boot-info : [http://paste.ubuntu.com/p/WkrwKsctgJ/](http://paste.ubuntu.com/p/WkrwKsctgJ/)

I don't really understand any of this, it'd be great if you could help me.

---

### Post by robingranda on 2018-03-16
If I understand the last part, I should : 
- disable Secure Boot
- boot on Windows and type [COLOR=#000000]bcdedit /set [/COLOR][COLOR=#666666]{[/COLOR][COLOR=#000000]bootmgr[/COLOR][COLOR=#666666]}[/COLOR][COLOR=#000000] path [/COLOR][COLOR=#BB6622]**\E**[/COLOR][COLOR=#000000]FI[/COLOR][COLOR=#BB6622]**\.**[/COLOR][COLOR=#000000]..[/COLOR][COLOR=#BB6622]**\g**[/COLOR][COLOR=#000000]rub*.efi in admin prompt
[/COLOR]- boot on liveUSB and run boot-repair

Is that it ?

---

### Post by ajgreeny on 2018-03-16
Sorry, I can not really help you with that; as I said I do not have Windows any more and any questions about editing bcdedit are way beyond my knowledge base.  With luck a colleague in the forums, oldfred, will see this and have more useful info to help.

---

### Post by yancek on 2018-03-16
Your boot repair output shows at the very top that you have installed and older version of Grub which has not been used on Ubuntu for over EIGHT years!  Not sure how you managed to do that?  You have both windows and Ubuntu EFI files so you need to make sure you have UEFI enabled in the BIOS and Legacy off.

If you want to use the bcdedit program in windows, make sure that you click on the Menu, mouse up to Windows PowerShell and right-click and select Run as Administrator, you should then get the prompt to enter commands.  The command below is what is suggested and it comes from the path for the grubx64.efi file you see in boot repair, the EFI partition, sda1.  If that fails, you might try replacing "grubx64.efi" in the command with "shimx64.efi" (without quotes).  Good luck.

[COLOR=#000000]> [COLOR=#000000]bcdedit /set [/COLOR][COLOR=#666666]{[/COLOR][COLOR=#000000]bootmgr[/COLOR][COLOR=#666666]}[/COLOR][COLOR=#000000] path [/COLOR][COLOR=#BB6622]**\E**[/COLOR][COLOR=#000000]FI[/COLOR][COLOR=#BB6622]**\ubuntu\**[/COLOR]grubx64.efi[/COLOR]

---

### Post by kurt18947 on 2018-03-16
I did a Windows update on a system on which Windows hadn't been run for about 3 months. When I requested updates, I got Creators which broke the boot process much like robingranda experienced. The boot-repair DVD fixed the problem however this machine was pre-UEFI. I know eventually I'm going to be forced to purchase a UEFI machine but I'm not in a rush to do so.

---

### Post by Hat-trick on 2018-03-17
I have the same problem.  If I boot into windows just once, I'll never see grub again and my laptop just boots straight to windows.  The only way to get my grub up again is to run boot repair from a live cd.  I still have this problem and I'm ready to just get rid of windows.  I don't use it anyway.  I just kind of keep it because it came installed when I bought the computer

---

### Post by robingranda on 2018-03-18
Hi, and thanks for your answers. I've fixed the problem : it appeared that on ACER laptop, one must indicate an Ubuntu EFI file in the boot options. Here's how I managed to do it, for those interested : 

- Boot the computer and press F2
- Define a password in Securty tab so that you can access options
- Go to "select an uefi as trusted for executing"
- Select HDD0 -> EFI -> Ubuntu -> shimx64.efi
- Enter the description you wish in the following pop-up

- Reboot
- Press F2 and go in the boot tab
- Put EFI File Boot 0 :.... in first
- Save and exit.

---

### Post by ajgreeny on 2018-03-18
Great news! Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

