---
title: "Need to recover formatted partition, but testdisk can't locate it."
date: 2013-12-02
forum: General Help
---

### Post by ralph.gill on 2013-12-02
Hi. Ubuntu 13.
I have a seperate (from my Ubuntu system disk) data disk that I mistakenly (in Gparted) deleted the single primary partition and then formatted.
Realising my mistake I ran testdisk - I am not sure if at this point the old partition was recoverable because after I selected the correct disk in testdisk,  I decided to choose "[ MBR CODE ] Write Testdisk MBR code to first sector". I then rebooted as per testdisk instruction, and found the drive was mounted but partition still empty. 
I went back into testdisk, did the 'Quicksearch and then Deeper search, but still only one partion appeared recoverable and also no files to be restored. I did write this recovered partion to the disk, but still no files after a reboot.

I have a horrible feeling writing over the MBR has destroyed any chance of getting the partition back - my only option now being using something like recuva in windows or photorec.

I did a DD copy to another disk and used recuva, but it found 27,000 files, and crashed after a few goes after 3 hours of recovering. And photorec as well all know is a nighmare because the file names aren't restored.

Any advice at this late stage would be appreciated.

---

### Post by sudodus on 2013-12-02
Well, I think PhotoRec is a reliable last resort. You can select what kind of files you want to recover and avoid getting all files at the same time.

[http://www.cgsecurity.org/wiki/File_Formats_Recovered_By_PhotoRec](http://www.cgsecurity.org/wiki/File_Formats_Recovered_By_PhotoRec)

See also this link

[http://ubuntuforums.org/showthread.php?t=1872548](http://ubuntuforums.org/showthread.php?t=1872548)

---

