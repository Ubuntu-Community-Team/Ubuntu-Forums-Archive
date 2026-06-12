---
title: "Lenovo B570-1068: BIOS / UEFI settings"
date: 2014-02-15
forum: General Help
---

### Post by kschumake83 on 2014-02-15
Hi everyone,

I had made a mistake and tried out windows 8 on my Lenovo B570-1068,  now my boot options are gone.  I have tried every key possible and none of them take me into bios settings or boot manager.  I also have tried formatting the hard drive, repartitioning the hard drive, reflashing my bios, rolling back to windows 7,  and installing about 10 different linux distros.  There is only one way that I am able to get into the bios settings and it is a royal pain,  I have to go into efibootmgr on ubuntu and change it to boot to settings first then when I am done in there i have to change the boot order back before I exit. Does anyone have any ideas?  I am all out of them and the lenovo forums have been absolutely no help, so even though ubuntu did not cause my issue I am hopefull that someone here is able to point me in the right direction.  Also it is a pita because ubuntu 13.04 and 13.10 will not boot or install from live cd so when I installed ubuntu I had to start at 12.04 and upgrade from there.

Thank you in advance for any insight you may give me.

---

### Post by PotatoHead007 on 2014-02-16
Hey, have you tried what it says on this page? UEFI is tricky sometimes :P
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by kschumake83 on 2014-02-16
Well I may have really screwed myself,  I decided I was going to look in the bios settings to see if there was a way to switch uefi off.  So I did my trick of going into efibootmgr in ubuntu and setting setup as the first boot order.  I have done this before and was always able to switch boot order back once in bios settings.  This time it is a no go,  bios will not save new boot order so I have a laptop that only boots into setup and cannot get it to boot from cd or hd.  Luckily I was able to get my t500 working again, and I actually like this laptop better, even though it is a little slower.  I will be looking for any Ideas anyone may have on getting this thing out of bios setup,  I am working on setting up a bootable usb stick as lenovo has a crisis flash for the bios which is a key combo that automaticly boots to usb dos to flash bios.

---

### Post by oldfred on 2014-02-17
This is an older install, but mentions your model.
[https://help.ubuntu.com/community/InstallUbuntu11.10OnLenovoEFI/GPT/WLAN/Power/BIOS](https://help.ubuntu.com/community/InstallUbuntu11.10OnLenovoEFI/GPT/WLAN/Power/BIOS)
       How to install Ubuntu 11.10 on a Lenovo (U)EFI system (tested on S205, B570)
[http://ubuntuforums.org/showthread.php?t=1867367](http://ubuntuforums.org/showthread.php?t=1867367)

    
 Samsung, Lenovo & Toshiba UEFI issues
[http://mjg59.dreamwidth.org/22028.html](http://mjg59.dreamwidth.org/22028.html)

One user posted this:

 > Lenovo's  buggy EFI Bios is will not boot from a DVD at all unless you enable 'legacy' (which you can't do because it screws with Windows 8!)
 The work around was to turn ON 'Legacy' boot mode in the BIOS and turn OFF "secure-boot" mode from locking out Ubuntu), and also make sure to turn OFF 'Legacy' SATA AHCI to ATA.
Then I installed Ubuntu from a USB stick (because these settings would only boot the Ubuntu installer from USB, but not DVD). 


 Another lenovo solution copy grubx64.efi to bootx64.efi & boot hard drive not anyother entry
[http://ubuntuforums.org/showthread.php?t=2185869&p=12884470#post12884470](http://ubuntuforums.org/showthread.php?t=2185869&p=12884470#post12884470)

---

### Post by kschumake83 on 2014-02-22
Ok so I finally got my b570 to stop booting straight to setup by reflashing the original bios and then going and reflashing my whitelist bios.  So being said I tried the boot repair disk that potatohead007 said and clicked on restore mbr, and it worked, if fing worked, a year and a half of dealing with this crap that no one was able to help me on and I finally asked in the right community.  Thank you potatohead and the ubuntu community you guys are great.  

Thank you also oldfred for the reply but I could care less about windows 8,  I am not looking to dual boot, I just wanted to fix the issue that windows 8 caused.  That is a great workaround and once you install an older version of ubuntu you can also upgrade through them to the most current, you just cannot install 13.10 from the get go which is a pita doing upgrades for hours.

Thank you again PotatoHead007  I appreciate the help and you couldn't understand how happy you have made me to have my laptop back to normal again.

---

### Post by kschumake83 on 2014-03-23
So I figured I would reply here again since I don't like starting a million posts,  this is more of an answer than a question as I have figured out a new way to get these laptops booting live media.  If you use the MAC amd64 iso from ubuntu it works perfectly,  I was a little nervous testing it but I figured what the hell and gave it a shot,  it worked flawlessly with ubuntu 14.04 on dvd.  No more usb sticks needed!

---

