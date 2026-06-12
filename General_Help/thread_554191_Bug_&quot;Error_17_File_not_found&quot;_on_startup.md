---
title: "Bug: &quot;Error 17: File not found&quot; on startup"
date: 2007-09-18
forum: General Help
---

### Post by googelybear on 2007-09-18
Hi guys,

I wanted to try out wubi but right after it installed ubuntu (I already downloaded the 7.04 i386 iso file and copied it to wubi's install folder, so it didn't have to download it again) and rebootet I get the following error:

...
Booting find/menu.lst

Warning: Unrecognized partition table for drive 80. Please rebuild it using a microsoft-comptabile FDISK tool (err=24). Current C/H/S=16383/240/63
find --set-root --ignore-floppies /menu.lst

"Error 17: File not found"

Press any key to continue...

After I press any key it is followed by GRUB4DOS screen where you can select some entries (no idea what they mean, but neither works).

How can I fix this? Do you need any further information?

---

### Post by googelybear on 2007-09-19
Today I wanted to try PartitionMagic under Windows to see what's wrong and/or gather some additional info, but I also get an error msg when I start it:
"Init failed: Error 117. Partition's drive letter cannot be identified"

PartitionInfo shows some more detailed output (unfortunately this doesn't mean much to me...)
Error #108: Partition didn't end on cylinder boundary.
  ucEndHead expected to be 239, not 119.
Error #109: Partition ends after end of disk.
  ucEndCylinder (10337) must be less than 10337.
Error #105: Partition didn't begin on head boundary.
  ucBeginHead expected to be 0 or 1, not 121.
Error #109: Partition ends after end of disk.
  ucEndCylinder (10337) must be less than 10337.
Error #108: Partition didn't end on cylinder boundary.
  ucEndHead expected to be 239, not 14.

There is only 1 harddisk in this PC with 2 Ntfs partitions on it. Does any of you guys know what's wrong with my disc?

---

### Post by ago on 2007-09-19
Hmm looks like your partition table is messed up. You may want to run chkdsk /r just in case. There are various tools to restore partition table data

---

### Post by googelybear on 2007-09-19
I already ran chkdsk but unfortunately the problem still persists. Is there a way to correct the partition table without deleting/formating? Or how can I determine which partition is "corrupt"? 

Thanks in advance for any help!

edit: When I use the ubuntu live cd und start QTParted it detects my 2 partitions (primary + extended partition) without reporting any problems

---

### Post by bean123 on 2007-09-19
> **googelybear said:**
> I already ran chkdsk but unfortunately the problem still persists. Is there a way to correct the partition table without deleting/formating? Or how can I determine which partition is "corrupt"? 

Thanks in advance for any help!

edit: When I use the ubuntu live cd und start QTParted it detects my 2 partitions (primary + extended partition) without reporting any problems

The latest version of grubinst can be used to dump the content of mbr:

grubinst -t -v (hd0)

---

### Post by googelybear on 2007-09-20
Thanks for your tip, but unfortunately this command is not available in the ubuntu live cd. So I googled a bit and found the following command to dump the mbr:```
sudo dd if=/dev/sda bs=512 count=1 of=/home/ubuntu/mbr.bin
```
I attached the mbr to this post and I also made a screenshot of qtparted, hopefully you guys can figure out what's wrong with my disk ;) 
When I start the regular ubuntu setup it gives me the option to resize my 2nd partition (sda5) - is this safe to do so regarding the current state of my disk or could I end up with an unreadable disk?

Just as a side note: I never had any problems under Windows with this setup.

Thanks again for any help.

---

### Post by bean123 on 2007-09-20
I see, the chs value in mbr is wrong:

  bt  h0  s0  c0  fs  h1  s1  c1      base      leng
  80  01  01  00  07  77  FF  FF        3F   1D4B139
  00  78  C1  FF  0F  0E  FF  FF   1D4B178   77C3349
  00  00  00  00  00  00  00  00         0         0
  00  00  00  00  00  00  00  00         0         0

The correct value should be:

  bt  h0  s0  c0  fs  h1  s1  c1      base      leng
  80  01  01  00  07  FE  FF  77        3F   1D4B139
  00  00  C1  78  0F  FE  BF  00   1D4B178   77C3349
  00  00  00  00  00  00  00  00         0         0
  00  00  00  00  00  00  00  00         0         0

You can use ptedit from pqmagic or similar tools to change the mbr table.

---

### Post by googelybear on 2007-09-20
Thanks for your research. Unfortunately I'm unable to map these values to the screen in ptedit :( As far as I can see there is something wrong in the red area. I would be glad if you could give me some further advice.
Thanks a lot!

edit: I was able to figure out the following:
bt = Boot, fs = Type and h0/s0/f0 stands for the starting head/cyl/sect values und h1/s1/c1 for the ending values. 
For h1 on the first partition it matches (77 hex = 119 dec), but when I take the ending cylinder value (c1)  it does not match the value in the screen (FF = 255 dec vs. 1023 in screen) and for s1 the same (255 vs 1023) - What am I doing wrong?

---

### Post by bean123 on 2007-09-20
> **googelybear said:**
> Thanks for your research. Unfortunately I'm unable to map these values to the screen in ptedit :( As far as I can see there is something wrong in the red area. I would be glad if you could give me some further advice.
Thanks a lot!

edit: I was able to figure out the following:
bt = Boot, fs = Type and h0/s0/f0 stands for the starting head/cyl/sect values und h1/s1/c1 for the ending values. 
For h1 on the first partition it matches (77 hex = 119 dec), but when I take the ending cylinder value (c1)  it does not match the value in the screen (FF = 255 dec vs. 1023 in screen) and for s1 the same (255 vs 1023) - What am I doing wrong?

The cylinder number is splited into two parts, the lower 8 bits is stored in cyl, while the upper 2 bits is stored alongside sect. In ptedit, you should reverse this process to get the real number. Anyway, the value you set in ptedit should be:

Starting             End
Cyl Head Sect   Cyl Head Sect   
0 1 1                 887 254 63
888 0 1             512 254 63

---

### Post by googelybear on 2007-09-20
When I set these values I get the following error message:
"The ending head value for table entry 1 must be less than 240"

It seems that the disk has only 240 heads, at least that's what's indicated on the top, right to the combo box...

---

### Post by bean123 on 2007-09-20
> **googelybear said:**
> When I set these values I get the following error message:
"The ending head value for table entry 1 must be less than 240"

It seems that the disk has only 240 heads, at least that's what's indicated on the top, right to the combo box...

You can try the dos version of ptedit. If it still don't work, you can use dd to write back the mbr I edited for you. but BE CAREFUL, make sure you dd to the correct disk, otherwise you may overwrite the mbr of another disk ! Keep the original mbr in a usb flash drive would be a good idea, too.

---

### Post by googelybear on 2007-09-21
Sorry to bother you again, but I'm not sure on how to call "dd" because there are so many variants on the web
```
dd if= sda-mbr.bin of=/dev/sdX bs=1 count=64 skip=446 seek=446
``` as written [here]("http://www.cyberciti.biz/tips/linux-how-to-backup-hard-disk-partition-table-mbr.html") or ```
 dd if=/path/to/image of=/dev/hdx
```
as written [here]("http://www.debianhelp.co.uk/ddcommand.htm") or simply call it with the same arguments I used to create the dump (bs=512, count=1)?

Something strange I noticed today was, that when I use the Ubuntu live cd (instead of Kubuntu which I normally use) the screen goes (and remains) black after it loaded all the drivers/components and before displaying the UI. The same that also happens when I boot the wubi install of Ubuntu...maybe my pc doesn't like Gnome?

Btw. I do not want to second-guess you, but are you sure that 254 is the correct ending-head value (both the dos and windows version of ptedit show me that the disk has only 240 heads...and that's why they do not allow me setting a value higher than 240)?

---

### Post by bean123 on 2007-09-21
To write the mbr file back to disk, you can just swap the parameter of if= and of=, for example, if you use

sudo dd if=/dev/sda bs=512 count=1 of=/home/ubuntu/mbr.bin

to get the mbr file, you can use

sudo dd if=/home/ubuntu/mbr.bin bs=512 count=1 of=/dev/sda

to write it back.

The head number should be 255, or at least that's what the tool you use to create the partition thinks.  Because the partition align nicely when heads=255. But the geomery can change if you move the disk to another computer. Or maybe the partition tool make a mistake in the first place. There is no way to tell if it is the correct value. But anyway, even if the chs value is wrong, you can still use the disk as most system would simply use the lba value.

---

