---
title: "Grub won't load the Grub Boot Loader"
date: 2016-11-02
forum: General Help
---

### Post by vihanagarwal on 2016-11-02
I currently have Ubunutu 16.04 (with GNOME 3) installed on my Acer  Aspire V Nitro, alongside Windows 10. The installation was fine but when  I boot into my system it loads an empty grub screen. For a while I was  stuck there but then I was guided by this: [http://askubuntu.com/questions/159846/tried-to-boot-ubuntu-but-the-grub-rescue-shows-up-instead](http://askubuntu.com/questions/159846/tried-to-boot-ubuntu-but-the-grub-rescue-shows-up-instead). This solved my issue except the last step in the solution, with the "sudo update-grub" command, didn't work. 

  So basically each time I want to load into either one of my OS's I  have to manually go through the solutions in the linked thread.  
  Is there a better solution to my issue? And why isn't "sudo update-grub" solving my issue?

---

### Post by Hewjr100 on 2016-11-02
I found this link in google.  You may want to give it a try.  [http://linuxpitstop.com/repair-grub-boot-loader-on-ubuntu-linux/](http://linuxpitstop.com/repair-grub-boot-loader-on-ubuntu-linux/)

Henry

---

### Post by oldfred on 2016-11-02
You run the sudo update-grub from inside Ubuntu after you boot. It will not work in grub> or grub rescue>

If booting in UEFI mode, have you updated UEFI from Acer and enabled "trust" on the Ubuntu/grub .efi files from UEFI?
       Acer Trust Settings - details:
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[URL="http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757"]http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757
[/URL]
 Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)
      
 Acer Aspire E15 will not dual boot, many details Trust settings in step 35
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot) 
    


[URL="http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757"]
[/URL]

---

### Post by vihanagarwal on 2016-11-02
Hi I have already assigned some grub files as trusted and can hence bring up the GRUB screen for me with only: grub>
After this I type,
root=(hd0,gpt5)
configfile /boot/grub/grub.cfg

and this takes me to the GRUB menu where I can boot into either of my OS.

After doing this, I was told sudo update-grub will prevent me from manually typing the above code, but that doesn't solve it. 

I have been recommended to reinstall GRUB

---

### Post by oldfred on 2016-11-02
May be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

