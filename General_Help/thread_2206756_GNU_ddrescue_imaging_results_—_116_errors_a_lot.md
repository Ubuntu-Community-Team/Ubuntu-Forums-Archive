---
title: "GNU ddrescue imaging results — 116 errors a lot?"
date: 2014-02-20
forum: General Help
---

### Post by jay35 on 2014-02-20
[FONT=times new roman][SIZE=3][COLOR=#333333]A little background on this.
[/COLOR]
[COLOR=#333333]It's an 256 GB SSD drive with Windows SP3 32-bit and it's encrypted with PGP Whole Disk Encryption. The file system is corrupt and unreadable.
[/COLOR]
[COLOR=#333333]I first ran Clonezilla to clone the drive with -q1 (sector clone) and Clonezilla could not start the clone process because it said the drive is physically damaged (does it determine this by using SMART or looking at the G-List?). I then checked off -rescue (skips bad sectors) and it cloned.
[/COLOR]
[COLOR=#333333]I wanted a better image/clone so I found Ubuntu Rescue Remix Live CD and ran GNU ddrescue. I created an image of the SSD drive using the following syntax: 
[FONT=lucida console]sudo ddrescue -r 5 -v -d {source drive} {dest drive/imgfile} logfile [/FONT]
(retries bad sectors 5 times; verbose output to screen; direct access mode to skip kernel cache).
[/COLOR]
[COLOR=#333333]It finished in 2:30-3:00 hours. The average transfer rate was around (25.88 MB/s) (I used eSATA and SATA, respectively, to transfer data). It also lists "errors: 116" and "errsize: 470 kB". For the record, the program lists "Sector size: 512 bytes" and "Copy block size: 128 sectors".
[/COLOR]
[COLOR=#333333]Two things:[/COLOR]
[/SIZE][/FONT]
[LIST=1]
[*][FONT=times new roman][SIZE=3]Are the results saying that 116 errors (sectors or blocks?) totaling 470 kB were found and transferred or found and not transferred? If you notice, the program says it's about to copy 256052 MB and it says it rescued 256052 MB. So, I'm really not sure.[/SIZE][/FONT]
[*][FONT=times new roman][SIZE=3]Is 116 errors considered to be a lot and indicative of physical damage?[/SIZE][/FONT]
[/LIST]
[FONT=times new roman][SIZE=3]
[/SIZE][/FONT]
[FONT=times new roman][SIZE=3][COLOR=#333333]For the moment, I can confirm that, at the very least, over 99% of data was transferred. I'd say that's pretty good. In fact, the rough calculation is: 1 - (470 kB/256 GB) =~ 0.9999981640625 --> 0.9999981640625 * 100 ~ 99.9998%.
[/COLOR]
[COLOR=#333333]Again, Clonezilla couldn't clone, at first, because it reported that the drive is physically damaged. Yet, while GNU ddrescue reported 116 errors, at least most of the data was imaged. I know there are logical errors on the drive. But is this drive physically damaged based on 116 errors totaling 470 kB?
[/COLOR]
[COLOR=#333333]Lastly, what is an error? Is that number of bad blocks, sectors, or something else? And is it at all related to errsize. In my case, it's 116 errors and errsize of 470 kB. But I have seen other scans on the Internet with 1 error and 500 GB errsize. So, I'm not sure what the correlation is there.[/COLOR][/SIZE][/FONT]

---

### Post by jay35 on 2014-02-21
I got no reply so I'll update and hope someone out there smarter than me will reply with some answers.


I ran GNU ddrescue once more, with read retries increased from 5 to 20. Everything else is the same, including the results (it took slightly longer to image than the first time, because of the read retry increase). Yes, the error count and error size (still don't understand their relationship or what an error means in this program) are 116 and 470 kB, exactly the same as the first time I imaged with this program. What could that mean? Put a gun to my head, I'd say this SSD drive is not physically damaged. And if it is, it's slight. I still don't know if 116 errors is a lot, but here's why I think there's no physical damage. If there was, wouldn't the error count and error size go UP the 2nd time I imaged the drive, especially with increasing the read retries to 20? 


I wanted the errors to go down, which is why I tried imaging again. I don't have much experience with SSDs. But perhaps they differ from mechanical disks in that if you can't read a bad block, most likely you won't be able to, no matter how many times you retry. I'm assuming data recovery services have vastly superior software and hardware tools that could read bad blocks from an SSD, however.


This SSD drive has been slaved quite a few times to analyze and also attempt decryption. I've cloned with it Clonezilla (which claims it's physically damaged), and then I imaged it twice with GNU ddrescue with one parameter value increased and the image results are exactly the same. One would think that with all that this drive has been through, if it was failing, it would take a long time to read from/write to and the number of errors would increase. But none of that has happened. Maybe I'm just getting lucky and it is physically damaged. But if it is, I think it's slight.


But I'll ask again: Is 116 errors a lot? What's the correlation of errors to error size, when I've read accounts of image results with 1 error and an error size of many, many GBs? And is an error here in terms of sectors, blocks, or some other measurement?


Thank you.

---

