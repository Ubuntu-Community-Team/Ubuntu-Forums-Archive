---
title: "windows breaks my ubuntu"
date: 2023-12-03
forum: General Help
---

### Post by buill on 2023-12-03
hi not sure if this os correct section but i hava a windows 10 install for games on a 500gb ssd and a seperate 500gb ssd ubuntu for working on but if i use imy windows 10 and then shut down and put my ubuntu ssd  in my ubunutu wont boot. In recovery mod it stops on error failed to evaluate_DSM.
what is causing this and ho to resolve i have had to reinstal my ubuntu twice i hate windows but the little on like games so...

---

### Post by yancek on 2023-12-03
Are they both EFI installs?  Do you have a separate EFI partition on each drive?  After booting windows, do you need to select the SSD drive on which Ubuntu is installed from the BIOS firmware Boot Option?  So Ubuntu is on an external drive?   If you have a 'live' Linux usb of any king, you can boot it and run the following command to list the above information to post here:

```
 sudo parted -l
```

What information did you get when you did an online search for the error you reported?  Any interesting links?  It would also be useful if you posted which version release of Ubuntu you are using.

---

### Post by Rubi1200 on 2023-12-03
In addition to what yancek already asked for:

system specs. especially graphic card and RAM would be useful to know.

---

### Post by buill on 2023-12-03
thanks for replys its a latitude e6430 i7 8gb ram "01:00.0 VGA compatible controller: NVIDIA Corporation GF108GLM [NVS 5200M] (rev a1)"graphic card they are both on seperate ssd i physicaly remove them from the laptop and slide the other on in 22.04 lts ubuntu

---

### Post by oldfred on 2023-12-03
So if swapping SSD's, most systems forget the UEFI entry of a removed drive.
They seem to be able to find a Windows entry in ESP - efi system partition.

Check this:
sudo efibootmgr -v

You should also have a drive entry which with full installs is a fallback boot entry, and be able to boot using that like you do with live installer when installing.
Drive entry uses /EFI/Boot/bootx64.efi 
But on my older desktop, some of the drive entries look more like old BIOS boot entries.
My laptop has this:
```
Boot0000* UEFI RST PC SN530 NVMe WDC 512GB 220305800706     HD(1,GPT,c3b854b4-f01c-485b-83b8-915bbbe8750c,0x800,0x64000)/File(\EFI\Boot\BootX64.efi)N.....YM....R,Y.
```

---

