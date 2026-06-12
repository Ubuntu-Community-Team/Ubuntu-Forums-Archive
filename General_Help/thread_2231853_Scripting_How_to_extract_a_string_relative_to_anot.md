---
title: "Scripting: How to extract a string relative to another one"
date: 2014-06-28
forum: General Help
---

### Post by actionmystique on 2014-06-28
Hello guys,

As you already know, the "**/dev/sdxn**" character numbering varies according to the USB port into which the devices have been inserted.
I do backups with the following incomplete script where **corsair** stands for a USB stick containing a complete Ubuntu 14.04 distribution and **wd** stands for a western digital disk representing the backup USB storage device:

[COLOR=#ff0000]dd if=**$corsairefi** of=**$wdcorsairefi** bs=4096 conv=notrunc
fsarchiver -j6 -v -o -A savefs /media/actionmystique/WD-Ext4/CORSAIR-Ubuntu-14/fsarchiver/CORSAIR-Ext4.fsa **$corsairext4**[/COLOR]

In order to feed the variables, I intend to use "sudo blkid":

[COLOR=#ff0000]/dev/sda1: LABEL="MSI-GE60-EF" UUID="61C8-9144" TYPE="vfat" 
/dev/sda2: LABEL="MSI-GE60-Ext4" UUID="0e92ddf7-be63-4b1f-85b1-6d3843f1098d" TYPE="ext4" 
/dev/sda3: LABEL="MSI-GE60-Swap" UUID="2b404c75-4eba-4cd6-a008-3dbb054a600b" TYPE="swap" 
/dev/sdc1: LABEL="WD-Ntfs" UUID="8C5C1CD65C1CBCC0" TYPE="ntfs" 
/dev/sdc2: LABEL="WD-Ext4" UUID="1a66d725-a8d9-483f-b69e-adc20007c8ff" TYPE="ext4" 
/dev/sdc3: LABEL="MSI-GE60-EF" UUID="61C8-9144" TYPE="vfat" 
**/dev/sdc4**: LABEL="CORSAIR-EFI" UUID="EE44-30BE" TYPE="vfat" 
/dev/sdd1: LABEL="SAMSUNG-Ext4" UUID="3501ced7-851d-416e-b559-78bc1f659d2d" TYPE="ext4" 
**/dev/sdb1**: LABEL="CORSAIR-EFI" UUID="EE44-30BE" TYPE="vfat" 
**/dev/sdb2**: LABEL="CORSAIR-Ext4" UUID="0544873e-3a01-44c3-b61e-12f3739ed514" TYPE="ext4" 
/dev/sdb3: LABEL="CORSAIR-Ntfs" UUID="58593CF4350D5791" TYPE="ntfs"[/COLOR]

In this particular **example**, [COLOR=#ff0000]**$corsairefi=/dev/sdb1**[/COLOR]**, **[COLOR=#ff0000]**$wdcorsairefi=**[/COLOR][COLOR=#ff0000]**/dev/sdc4 **[/COLOR]**and **[COLOR=#ff0000]**$corsairext4=**[/COLOR][COLOR=#ff0000]**/dev/sdb2**[/COLOR][B].

[/B]Rules for [COLOR=#ff0000]**$corsairefi **[/COLOR]and [COLOR=#ff0000]**$wdcorsairefi**[/COLOR]:
[LIST]
[*]the [COLOR=#ff0000]**$corsairefi **[/COLOR]source "CORSAIR-EFI" (1st parftition of CORSAIR) is right before "CORSAIR-Ext4" 
[*]the [COLOR=#ff0000]**$wdcorsairefi **[/COLOR]destination "CORSAIR-EFI" (4th partition of WD) is 2 lines below "WD-Ext4". 
[/LIST]
[B]
How can I script that little algorithm[/B]?

P.S: Regarding the last variable, I thought of:
[COLOR=#ff0000]**corsairext4=**[/COLOR]$( sudo blkid | grep CORSAIR-Ext4 | cut -c 1-9)

Thanks for your attention.

---

### Post by TheFu on 2014-06-28
ooops - double post ... somehow. My fault, certainly.

---

### Post by TheFu on 2014-06-28
Your first sentence is NOT correct.
> As you already know, the "/dev/sdxn" character numbering varies according to the USB port into which the devices have been inserted.
The USB port has little to do with the generated device.  Most people solve this by accessing the partitions either by-label, by-path, or by-UUID.   Look under /dev/disk/by-* for more clarity.  Just provide a different label for every partition.
 
Or am I missing something in the question?

---

### Post by actionmystique on 2014-06-29
Yes you are: 2 partitions are identical by design: CORSAIR-EFI is copied with dd: the other CORSAIR-EFI has exactly the same label and UUID.

There's absolutely no way to differenciate them only through label or UUID.

---

### Post by actionmystique on 2014-06-29
[COLOR=#ff0000]**corsairefi**[/COLOR]=${[COLOR=#ff0000]**corsairext4**[/COLOR]/${[COLOR=#ff0000]**corsairext4**[/COLOR]:8}/$(expr ${[COLOR=#ff0000]**corsairext4**[/COLOR]:8} - 1)} is one answer to the first part :)

which can be translated into: in the string [COLOR=#ff0000]**corsairext4**[/COLOR], replace the first match of the last character of [COLOR=#ff0000]**corsairext4**[/COLOR] by its last character converted into number - 1; details of the theory can be found [here]("http://tldp.org/LDP/abs/html/string-manipulation.html").

---

### Post by actionmystique on 2014-06-29
[COLOR=#ff0000]**wdext4**[/COLOR]=$( sudo blkid | grep WD-Ext4 | cut -c 1-9)
[COLOR=#ff0000]**wdcorsairefi**[/COLOR]=${[COLOR=#ff0000]**wdext4**[/COLOR]/${[COLOR=#ff0000]**wdext4**[/COLOR]:8}/$(expr ${[COLOR=#ff0000]**wdext4**[/COLOR]:8} + 2)} is one answer to the second part!

:p

---

### Post by steeldriver on 2014-06-29
I don't really get why you need to do the math - do you really expect the partition layout / numbering on the disk to change? if not, you can just replace "2" by "1" after identifying the correct disk using the label of the #2 partition

```

while IFS=$IFS: read -r dev lbl uuid type; do [[ $lbl =~ CORSAIR-Ext4 ]] && printf -v corsair_efi '%s' "${dev/%2/1}"; done < <(blkid)

```

or even simpler, use the -L switch of blkid to just grab the CORSAIR-Ext4 partition by label

```

corsair_ext4=$(blkid -L "CORSAIR-Ext4"); printf -v corsair_efi '%s\n' "${corsair_ext4/%2/1}"

```

---

### Post by actionmystique on 2014-06-29
Below are two layouts when switching 2 UDB devices:

[One layout]("https://drive.google.com/file/d/0B5fXyIn0-GDFbmN4X3JvUXE4dUE/edit?usp=sharing");
[Another layout]("https://drive.google.com/file/d/0B5fXyIn0-GDFUVJlUmEyY1hpS0U/edit?usp=sharing").

With all due respect, my solution has the advantage of being simpler. maybe you'll understand the reason I need to do this with the full solution:
Contents of the _**partitions backup script**_ that I call from the desktop, _**without needing to check which device is on which USB port**_:

[B][COLOR=#ff0000]corsairext4[/COLOR]=$( blkid | grep CORSAIR-Ext4 | cut -c 1-9 )
[COLOR=#ff0000]corsairefi[/COLOR]=${[COLOR=#ff0000]corsairext4[/COLOR]/${[COLOR=#ff0000]corsairext4[/COLOR]:8}/$(expr ${[COLOR=#ff0000]corsairext4[/COLOR]:8} - 1)}
[COLOR=#ff0000]wdext4[/COLOR]=$( sudo blkid | grep WD-Ext4 | cut -c 1-9)
[COLOR=#ff0000]wdcorsairefi[/COLOR]=${[COLOR=#ff0000]wdext4[/COLOR]/${[COLOR=#ff0000]wdext4[/COLOR]:8}/$(expr ${[COLOR=#ff0000]wdext4[/COLOR]:8} + 2)} 

dd if=$[COLOR=#ff0000]corsairefi[/COLOR] of=$[COLOR=#ff0000]wdcorsairefi[/COLOR]  bs=4096 conv=notrunc
fsarchiver -j6 -v -o -A savefs /media/actionmystique/WD-Ext4/CORSAIR-Ubuntu-14/fsarchiver/CORSAIR-Ext4.fsa $[COLOR=#ff0000]corsairext4[/COLOR]
[/B]

---

### Post by actionmystique on 2014-07-01
@TheFu: I've just made some tests with my USB devices: To be precise, in "**/dev/sdxn**", **character** **x numbering** primarly varies according to **the order of insertion** of the devices into the USB ports.
Furthermore, this numbering is remembered across reboots until the next change.
At last, there's sometimes a gap in the numbering: for example, right now, even though all the USB ports are used, I have this layout:

[COLOR=#ff0000][I]root@MSI-GE60-Ubuntu-14:~# blkid
/dev/sda1: LABEL="MSI-GE60-EF" UUID="61C8-9144" TYPE="vfat" 
/dev/sda2: LABEL="MSI-GE60-Ext4" UUID="0e92ddf7-be63-4b1f-85b1-6d3843f1098d" TYPE="ext4" 
/dev/sda3: LABEL="MSI-GE60-Swap" UUID="2b404c75-4eba-4cd6-a008-3dbb054a600b" TYPE="swap" 
/dev/sdb1: LABEL="SAMSUNG-Ext4" UUID="3501ced7-851d-416e-b559-78bc1f659d2d" TYPE="ext4" 
/dev/sde1: LABEL="WD-Ntfs" UUID="8C5C1CD65C1CBCC0" TYPE="ntfs" 
/dev/sde2: LABEL="WD-Ext4" UUID="1a66d725-a8d9-483f-b69e-adc20007c8ff" TYPE="ext4" 
/dev/sde3: LABEL="MSI-GE60-EF" UUID="61C8-9144" TYPE="vfat" 
/dev/sde4: LABEL="CORSAIR-EFI" UUID="EE44-30BE" TYPE="vfat" 
/dev/sdf1: LABEL="CORSAIR-EFI" UUID="EE44-30BE" TYPE="vfat" 
/dev/sdf2: LABEL="CORSAIR-Ext4" UUID="0544873e-3a01-44c3-b61e-12f3739ed514" TYPE="ext4" 
/dev/sdf3: LABEL="CORSAIR-Ntfs" UUID="58593CF4350D5791" TYPE="ntfs"[/I][/COLOR]

Please note that:
- I have a mix of USB 2.0 and 3.0 ports
- my USB stick is a complete Ubuntu system, not just a "LiveUSB".

This conclusion may be different on your system with different devices.[COLOR=#ff0000][/COLOR]

---

