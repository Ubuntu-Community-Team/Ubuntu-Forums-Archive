---
title: "unable to reinstall grub after dual boot windows 10 upgrade"
date: 2015-12-09
forum: General Help
---

### Post by Richard_Hatfield on 2015-12-09
Hi I have an acer Aspire E15 lap top with win 8.1 / ubuntu dual boot which was working fine
I upgraded to win 10 but could then only boot into windows
using boot-repair from ubuntu 14.04 live usb initially no luck but it suggested from windows command line:
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi

This seemed to run OK

could then boot into windows & ubuntu but ubuntu boot was a bit unreliable so I ran boot-repair from ubuntu and it had a problem reinstalling grub ("broken files.....")

Now I cant boot into either os

boot repair from live usb hangs on "Purge kernels then reinstall last kernal sda6(ins).This may take several minutes...."    waited 30!

boot-repair paste   [http://paste.ubuntu.com/13859363](http://paste.ubuntu.com/13859363)

Now can only boot into live usb!

Not sure what to try next!

---

### Post by oldfred on 2015-12-09
It looks like you may have to reset "trust". This should normally say ubuntu.
```
 Boot0001* Unknown Device: 	HD(2,12c800,96000,445eb0c0-f217-4995-8b77-3742c699f994)File(EFIubuntushimx64.efi)RC


```

Boot-Repair needs good network connection preferably hard wired Ethernet to download new copy of grub & kernel for its major updates to system.

If it worked before you should not need the fix of installing an older UEFI from Acer. Some new Acer now seem to require that also.
       Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on ubuntu entries Also R14 model same fix
One of several with more details:
[http://ubuntuforums.org/showthread.php?t=2297947](http://ubuntuforums.org/showthread.php?t=2297947)
[http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[http://ubuntuforums.org/showthread.php?t=2291335](http://ubuntuforums.org/showthread.php?t=2291335)
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)
[http://acer.custhelp.com/app/answers/detail/a_id/29349/](http://acer.custhelp.com/app/answers/detail/a_id/29349/)
[http://ubuntuforums.org/showthread.php?t=2290594](http://ubuntuforums.org/showthread.php?t=2290594)

---

### Post by Richard_Hatfield on 2015-12-09
Thanks for prompt reply
I have looked at the Acer specific issues but they do not resolve the problem
It used to work with win8.1 as dual boot
For a short period it did dual boot with win 10 & ubuntu 14.04
The problem was after running boot-repair
It now wont boot into either os
On boot:

"error: File '/boot/grub/x86_64-efi/normal.mod' not found (this file presumably was there before I ran boot-repair)
Entering rescue mode...
grub rescue>"

I have tried to reinstall grub manually & via boot-repair to no avail
[COLOR=#000000]boot repair from live usb hangs on "Purge kernels then reinstall last kernal sda6(ins).This may take several minutes...."

[/COLOR]Richard

---

### Post by Richard_Hatfield on 2015-12-09
SOLVED!

running boot-repair from live ubuntu usb
This hung every time on [COLOR=#000000]"Purge kernels then reinstall last kernal sda6(ins).This may take several minutes...."

To solve this  In advance settings > GRUBoptions tab > uncheck "[/COLOR][COLOR=#000000]Purge kernels then reinstall last kernal "

followed on screen instructions & all well![/COLOR]

---

