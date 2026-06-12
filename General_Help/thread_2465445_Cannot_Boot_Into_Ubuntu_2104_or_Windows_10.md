---
title: "Cannot Boot Into Ubuntu 21:04 or Windows 10"
date: 2021-08-02
forum: General Help
---

### Post by brucethedog on 2021-08-02
Following a reboot after applying latest Ubuntu patches, I get the following error on my dual boot pc.

Reboot and Select proper Boot Device
or Insert Boot Media in selected device and press a key

I dont see the Grub menu appearing, which defaulted to Ubuntu, and from where I could select the Windows Boot Manager to get to Windows.

I can boot from a Live 21:04 USB and can see the data on the volumes okay,

I have tried the Boot Repair tool which said successful but I got this URL
[https://paste.ubuntu.com/p/bC7KHv8zGR/](https://paste.ubuntu.com/p/bC7KHv8zGR/)
Same error as above after this attempted repair

Its a 3Tb volume, and the pc is an ACER XC-704

If I boot off the LIVE USB and select Boot from next device I see this message briefly

Failed to load image \EFI\ubuntu\ and then its like 3 characters of a question mark in black on a white background followed by an S and then another block of question mark in white then :Invalid Parameter
start_image() returned Invalid Parameter

Acer is in UEFI mode and SecureBoot disabled.

Looking for steps to get the Grub menu back and the way it was as before, and also what could have caused this?

---

### Post by tea for one on 2021-08-02
Have you tried to boot from your UEFI one-time boot menu?

---

### Post by brucethedog on 2021-08-02
hi yes, it says windows boot manager as only option, and selecting this gives same error

---

### Post by oldfred on 2021-08-02
Older Acer required setting of "trust" in UEFI.
But those typically showed "unknown" as UEFI entry as shown by efibootmgr -v. But on line 185 you do show "ubuntu". 
Newer ones also have additional setting when UEFI secure boot on & control S used.

Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742) 
Acer Swift 5 (2019) ctrl-s  in UEFI required to be able to change to AHCI mode.
[https://askubuntu.com/questions/1217061/installation-on-acer-swift-5-freezes-no-partitions-shown](https://askubuntu.com/questions/1217061/installation-on-acer-swift-5-freezes-no-partitions-shown)
Acer Aspire 5 Model A515-54-5649  Intel Core i5-10210U Install Tutorial
[https://ubuntuforums.org/showthread.php?t=2437702](https://ubuntuforums.org/showthread.php?t=2437702)

---

### Post by brucethedog on 2021-08-02
hi, still no further forward, the BIOS on the PC doesnt seem to have settings for Trust.
I suspect the EFI partition is corrupt but not sure how to verify and resolve.
I'll check out the rEFInd link above

---

### Post by brucethedog on 2021-08-03
update, nearly back in business, used the link above to get to windows boot issues section, and used diskpart to find the epr disk and rebuild. windows 10 needs a fomat and rebuild on that drive to get it booting, as fixboot gives access denied error.
so back in w10 and it seems to be applying patches, will check its okay and i can continue to boot into it.

then will look to getting grub and back to the ubuntu os once w10 is stable

will update

---

### Post by yancek on 2021-08-03
>  the BIOS on the PC doesnt seem to have settings for Trust. 

This is not likely to be the problem as you indicate you have had Ubuntu installed and functioning and the problem occurred after an update.  Before you can set trust on your Acer, you first need to set a Supervisor password in the BIOS.

Interesting that you do not see an ubuntu entry when acccessing the BIOS Boot Options as it clearly is shown in boot repair on lines 32, 57 and 185.
Lines 94-106 show EFI files for both windows and ubuntu and the standard files are there. 

>  Failed to load image \EFI\ubuntu\  

The boot entries in grub.cfg should have forware slashes rather than back as shown in your original post.  Not sure if that is a typo and if not, why it would have changed.

---

### Post by brucethedog on 2021-08-03
Update
So I managed to get it to boot into Windows 10 again, using steps at [https://www.thewindowsclub.com/fix-bootrec-fixboot-access-is-denied-error-on-windows-10](https://www.thewindowsclub.com/fix-bootrec-fixboot-access-is-denied-error-on-windows-10)
Basically recreating the EFI partition

I then used a Ubuntu Live 21.04 USB to connect and Try Ubuntu, connect to wi-fi, then download boot-repair and run
It said again successful, [https://paste.ubuntu.com/p/mr8RxvvdqX/](https://paste.ubuntu.com/p/mr8RxvvdqX/)

However rebooting then brings back the original error
[COLOR=#000000]Reboot and Select proper Boot Device[/COLOR]
[COLOR=#000000]or Insert Boot Media in selected device and press a key

So I had to do the steps again to recreate the EFI as at top of this reply

So now back with W10 again, seems every time it tries to make changes to the partition to get GRUB and Ubuntu again, it causes this error.

Maybe dual booting isnt the best option, so may just boot off a USB again, try and backup or move my data to the Windows or backup device, then remove the Ubuntu partition, and keep this PC as W10 only.


[/COLOR]

---

### Post by oldfred on 2021-08-03
Most Acer seem to work, but many have needed UEFI update.

Another alternative is an external SSD.

I was a bit surprised how fast external SSD is. I have used full installs on external flash drives and thought part of slowness was USB, but it turns out it almost all is just that flash drives are slow.
I built a system in 2016 that has a M.2 port, but NVMe drives were expensive, so added a M.2 SSD. Recently decided to update to larger NVMe to see if much difference and put M.2 SSD into an adapter USB3 to M.2. External drive then was almost as fast as it was as internal drive and lot faster than internal HDD.

---

