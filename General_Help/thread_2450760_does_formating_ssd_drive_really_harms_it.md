---
title: "does formating ssd drive really harms it?"
date: 2020-09-20
forum: General Help
---

### Post by ronjjjg8885 on 2020-09-20
i've read a part of this article
[https://www.unixmen.com/secure-erase-your-ssd/](https://www.unixmen.com/secure-erase-your-ssd/)

he says that it is like that (you need to be careful about using ssd)

i want to sell my laptop and wipe it first, and then install windows 10
what do you think i should do?
thank you in advance

---

### Post by HermanAB on 2020-09-20
An SSD only need to be erased once.

Overwrite it with 00H once only, then install Windows.  Erasing flash memory actually turns all bytes into FFH, but Windows sees an all zero disk as a new disk and will then install without hassles.

---

### Post by ronjjjg8885 on 2020-09-20
how can i overwrite it with 00H once?

and thanks for the tip

---

### Post by dinkidonk on 2020-09-20
The following command will write zero on a drive from start to end:

```
sudo dd if=/dev/zero of=/dev/sdXY bs=1M
```

BE CAREFUL! There is no way back from this, choose the "of=" with extra care!

---

### Post by ronjjjg8885 on 2020-09-20
ok

do i need to type this from a live cd of ubuntu or from ubuntu itself?

---

### Post by CelticWarrior on 2020-09-20
From a live session, obviously.
And again pay special attention to "of="

---

### Post by ronjjjg8885 on 2020-09-20
i've just one drive (the ssd) so i don't think i should worry.

i will try to boot into live session and hope it will load because earlier i had a problem with it

---

### Post by HermanAB on 2020-09-20
You can blow the disk away by booting an install CD, then:
$ sudo cat /dev/zero > /dev/sda
... very long wait ...

---

### Post by ronjjjg8885 on 2020-09-20
when i try to load ubuntu live session i don't have the 'live' option. when i choose the default option i get this problem:

[ATTACH=CONFIG]286999[/ATTACH]

what can this be caused by?

---

### Post by ronjjjg8885 on 2020-09-20
the other option is faster HermanAB?

---

### Post by CelticWarrior on 2020-09-20
Is the other option faster? No, probably the same but I haven't tested one against the other so this is just an opinion.

Regarding the live session I would recommend re-doing the USB media.

---

### Post by ronjjjg8885 on 2020-09-20
> **CelticWarrior said:**
> I would recommend re-doing the USB media.


i re created the usb but the results are the same

---

### Post by CelticWarrior on 2020-09-20
How did you create it? With what software?

And have you checked the ISO?

---

### Post by ronjjjg8885 on 2020-09-20
i didn't check the .iso
i created it with startup disk creator (the tool that comes with ubuntu)
the file has been downloaded as a torrent.

should i try to find a youtube video that explains the ISO check?

---

### Post by ronjjjg8885 on 2020-09-20
i've got ```
ubuntu-20.04.1-desktop-amd64.iso: OK


```

---

### Post by CelticWarrior on 2020-09-20
Torrents are usually fine so if the torrent client says it's fine then it really is.

At this point I wonder how did you install Ubuntu in the first place? If you were able to boot the installation media to install the first time you should be able to the exact same procedure now. Are you using the latest Ubuntu release, aren't you?

---

### Post by ronjjjg8885 on 2020-09-20
wait a moment. maybe it is because it is still having references to fedora which i don't use?

i use the latest release - (ubuntu-20.04.1-desktop-amd64)

---

### Post by CelticWarrior on 2020-09-20
No.

Whatever is installed or even less the remaining entries of a former OS in the EFI partition have absolutely no impact on the ability to boot external installation/live media.

---

### Post by ronjjjg8885 on 2020-09-20
should it try something in the bios configurations?
is there such a thing as a 'reset to defaults' in the bios?

edit:
i did a reset to the bios settings but the usb still shows the same problem

---

### Post by HermanAB on 2020-09-20
There was a difference many moons ago, but nowadays, cat and dd use the same underlying device file system system code, so they are pretty much equal in performance.

---

### Post by CelticWarrior on 2020-09-20
Yes, you should try to use the one-time boot menu if available (it usually is) or in UEFI settings use the boot override for the external media. If in any case you find two entries for the same stick then you should choose the one with "UEFI" in the its name.

PS - You don't have BIOS, that's a thing from the past (1981 to be precise). All computers's firmware from the last decade is UEFI, not BIOS.

---

### Post by CelticWarrior on 2020-09-20
Now, regarding you original request that prompted all this back and forth for something that should be trivial, I understand why you want to zero out the drive before selling the computer. It's certainly the best privacy option. That said, unless you sell it to an über geek with forensic tools and the will to use them, there's really no need to do that. Just boot the Windows installation media and during the installation proceess you will be able to select and delete all partitions prior to actually installing Windows and creating new partitions for that purpose.

In summary, installing Windows on top of whatever was there before is enough for any situation unless the rare case of an über geek with too much free time.

---

### Post by oldfred on 2020-09-20
With UEFI, it remembers boot entries and the ESP - efi system partition may have folder for old install's boot files. If wanting to houseclean you can remove entries in UEFI and folder in ESP.

You want to keep ubuntu & Boot folders.
ls -l /boot/efi/EFI

# from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B
man efibootmgr

---

### Post by ronjjjg8885 on 2020-09-20
> **CelticWarrior said:**
> Yes, you should try to use the one-time boot menu if available (it usually is) or in UEFI settings use the boot override for the external media. If in any case you find two entries for the same stick then you should choose the one with "UEFI" in the its name.

PS - You don't have BIOS, that's a thing from the past (1981 to be precise). All computers's firmware from the last decade is UEFI, not BIOS.

you already told me that i don't have a bios but it's confusing because this how it is named in my computer :)

i'm trying to figure out what you guys mean because you use a lot of terms that i need to search and learn more about
TNX for now

---

### Post by CelticWarrior on 2020-09-20
The terms are pretty standard and common to a vast range of brands/models. And you are certainly familiar with some of it or you wouldn't even try to boot something else. How would you know how to boot the USB stick if not by changing the boot order somewhere in the UEFI ("BIOS") > Boot settings -or- boot override -or- the one-time boot menu (independent from the UEFI settings and called by a different key during POST, i.e., during the boot process that happens before it tries to load an OS)?

Have you tried to boot the Windows installation media already? If so, what were the results? If successful that's exactly the same method to boot the Ubuntu media. If not successful then either the media is wrong or the user is doing something wrong. There's no third possibility here.

---

### Post by ronjjjg8885 on 2020-09-20
> **CelticWarrior said:**
> Now, regarding you original request that prompted all this back and forth...

ok
i think this is what i will do
the thing is that the guy from the original link in my post says from what i understand that it is damaging to install windows or linux without zeroing out the ssd first..

i will try the windows usb media now to see if it's working

---

### Post by CelticWarrior on 2020-09-20
No, it definitely isn't saying that. And it's the opposite actually. Zeroing out a SSD drive is a full cycle of writing and any writing process wears out a tiny little bit of the drive. Not relevant considering the life expectancy for modern SSDs.

---

### Post by HermanAB on 2020-09-20
The Macbook I'm wrting this on, is 8 years old and as good as new.  So the SSD lifetime is not an issue in practise.

---

### Post by ronjjjg8885 on 2020-09-21
i see 
thanks!!!!

---

