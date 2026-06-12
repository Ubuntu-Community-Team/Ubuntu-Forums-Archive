---
title: "Reboot and Select proper Boot device.....HELP!"
date: 2016-01-10
forum: General Help
---

### Post by james_adamik on 2016-01-10
[TABLE]
[TR]
[TD="class: votecell"]          

              [/TD]
              [TD="class: postcell"]        So i have been using Ubuntu 14 for a while now with no problems. My  girlfriend saw an upgrade button pop up and decided to upgrade me to  15.10. after just 2 days on 15.10 my computer shut down and when  restarting gave me the wonderful 
  ***"Reboot and Select proper Boot device or Insert Boot Media in selected Boot Device and press a key".*** 

  Once i get to this screen, nothing i do changes anything. I have  checked BIOS, and boot order is for my hard drive, hard drive is clearly  listed, it just wont boot.
  So i assumed it was my hard drive finally crapping out on me (it had  like 15 bad sectors and refused to let me change sectors to 0000 or  anything else), so i bought a new one. Ubuntu 14.04 loaded perfectly, i  was on the Internet all day, i updated it, and of course with large  amounts of updates got the restart request. 
  Not even thinking about it i clicked restart now and bam right back to 
  ***"Reboot and Select proper Boot device or Insert Boot Media in selected Boot Device and press a key".***
  Sigh. 
  So first i made a bootloader usb stick (which the computer wouldn't  recognize at all just continued to give error), then i reinstalled 14.04  and wallah perfect smooth install yet again Internet is fine everything  runs great.
  Then just to test and see if it worked this time, i clicked restart  and Error message again. I installed 14.04 again, downloaded boot repair  from terminal and ran the scan creating the link below.
  I am at my wits end, i have no idea why this is happening. Drive  seems to be flagged fine, boot order is correct, everything runs great  as long as i don't restart.

  [http://Boot Repair Link - paste.ubuntu.com/14434314]("http://Boot%20Repair%20Link%20-%20paste.ubuntu.com/14434314")
  I will be immortally grateful if you can help.
  P.S. i have gone through the forums and tried almost every fix i  could find that was different from the others still with no luck.
     

[/TD]
[/TR]
[/TABLE]

---

### Post by oldfred on 2016-01-10
You have an UEFI system and Windows installed in UEFI boot mode.
But it looks like Ubuntu is now installed in BIOS boot mode. Not sure if then upgrade did it wrong or one of the fixes changed it.

Best to just use Boot-Repair's advanced mode and do a complete uninstall/reinstall of grub2. Make sure you boot in UEFI mode from flash drive, so it reinstall grub-efi-amd64 for UEFI boot.

---

### Post by leunam12 on 2016-01-11
Have you played with your fast boot, safe boot, etc boot, settings in BIOS or UEFI settings? Try changing those settings to see if you are able to boot.

---

### Post by james_adamik on 2016-01-12
ok so i used boot repair to reinstall grub, computer booted right back up other then it asked me if i wanted *ubuntu or advanced ubuntu. though things were golden but i didn’t want to chance it for the day as i had work to get done. I got on the computer today  and it was frozen so i restarted it. same error message. In went my ubuntu usb stick, opened again in try ubuntu, reinstalled ubuntu repair, ran recommended repair and it gave me this message.

[I]An error occurred during the repair.

Please write on a paper the following URL:
[http://paste.ubuntu.com/14482488/](http://paste.ubuntu.com/14482488/)


In case you still experience boot problem, indicate this URL to:
[EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL] 

You can now reboot your computer.
Please do not forget to make your BIOS boot on sda (640GB) disk![/I]

it rebooted and again (without the stick in) gave me the option of Ubuntu or advanced. i came straight here to post the results. at least with boot repair im not losing any more data so im happy about that but this is getting ridiculous. 

Also, if there is some version of windows boot hiding in my computer how do i get that evil off. ugg windows is like a giant virus hiding itself in corners just to screw with you.

as for playing with fast boot, and safe boot and etc i haven’t since...uggg i don’t know the 4th or 5th time i got those errors. I can try again if you think it will help this time. what should i set it to?

not sure how you all put your computer information in the headings but in case you need to know

Linux 14.04 LTS 64-bit
5.2Gib Mem
AMD A6-5400K APU with Radeon(tm) HD Graphics × 2 
Gallium 0.4 on AMD ARUBA
624.2 GB

---

### Post by oldfred on 2016-01-13
What brand/model system.
A few have reported the issue where Ubuntu boots once. UEFI does have a one time boot setting.
Windows often resets itself to first in boot order on updates and maybe other setting changes.

Can you always boot ubuntu entry from UEFI boot tab or from one time boot key often f10 or f12, check your manual for correct key.

In advanced options Boot-Repair has the 'Use the standard EFI file' option. Choose that and see if you then get a fallback/default hard drive entry in UEFI that boots grub/shim. You already show a UEFI entry 0002 for hd WDC which that should be.
[https://bugs.launchpad.net/boot-repair/+bug/1531178](https://bugs.launchpad.net/boot-repair/+bug/1531178)

---

### Post by james_adamik on 2016-01-13
Its a Gateway desktop, i  have had it for a little over two years.

"Use the standard efi file" is already checked in boot repair

---

### Post by oldfred on 2016-01-13
Is then bootx64.efi in /EFI/Boot the same file as shimx64.efi in /EFI/ubuntu. You can check file size, not sure how else to compare.
Then can you boot hard drive entry in UEFI?

---

