---
title: "File recovery tips from encrypted ext4 drive with scalpel"
date: 2013-08-22
forum: General Help
---

### Post by v-tibor-a-j-1 on 2013-08-22
Hi guys!

**I recently had to recover** an important **permanently deleted** open office **document** **from an** **encrypted drive**(with success). I found that the scalpel's .conf file did not include open office file types originally, but I found this thread helpful: [http://ubuntuforums.org/showthread.php?t=1378119](http://ubuntuforums.org/showthread.php?t=1378119) Thanks[COLOR=#000000] jchedstrom for shearing.[/COLOR] The problem was that I found tons of information how to recover files, and I succeeded to recover files, but I could recover what I wanted the way they showed me, because the drive was encrypted. I could not find my important data on sda4, just some old junk. Eventually after a few hours of experimenting, I found that the sda4 image wasn't the encrypted filesystem's image.[COLOR=#000000]

What I basically done, is that I followed [/COLOR][COLOR=#000000]jchedstrom's[/COLOR][COLOR=#000000]instructions, but I opened Disk Utility, unlocked the encrypted drive, and checked the device image
> 
Device: /dev/dm-0
Capacity: 10 GB (10,024,519,168 bytes)
Available: -
Mount Point: Mounted at /media/Encrypted

You need the device image(and location) at the first row. (/dev/dm-0)
(After unlocking the device the column will be separated horizontally, and you find this info clicking on the row that does not contain an open padlock.)

Then I replaced /dev/sda4(in my case) [/COLOR][COLOR=#000000]with /dev/dm-0 because that's the encrypted filesystem's image, and typed in terminal:
[/COLOR]```
sudo scalpel /dev/dm-0 -b -o ~/Desktop/scalpel_recovered_files/
```
[COLOR=#000000]and I found my deleted .odt file(among tons of other deleted and probably even existing .odt-s in the output folder).

Oh yeah! I almost forgot... My encrypted drive was not unmounted for a half day or so, and I did not used any live cd or something like that... I didnt even turned off my computer... So I guess if no programs are writing to the partition, and you're not using it, probably doesn't matter if you unmount it or not. [/COLOR][COLOR=#000000](If you're editing a document from that partition, in office or other programs that has autosave function, that is harmful for your data as well since that includes writing to the disk. Of course copying new data to that disk or partition is the most dangerious act if you lost important data.)[/COLOR][COLOR=#000000] Now if your data is lost on your main partition from which the system is running, then you're in the biggest troubble, because running the system, upgrading, downloading from the internet or just changing any settings will most inevitably overwrite your data... If you have lost your file on a main drive or you have only one drive from which your system is running you are advised to turn off your pc immediately and re-boot from a live cd for a better chance to save your data.[/COLOR]

---

