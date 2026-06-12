---
title: "Extracting contents of .exe BIOS file"
date: 2007-07-03
forum: General Help
---

### Post by Zill on 2007-07-03
IBM 6339 Netvista desktop PC:
I have downloaded file 21jt32a.exe to update the BIOS of this PC.  The instructions are to run this file (presumably with Windows!) which will then extract the required files to a self-booting floppy disk to flash the BIOS.

I have tried, unsuccessfully, to open the file with both unzip and unshield.

As I don't have Windows, any ideas please on what I could try next to extract the contents of this file to a floppy using other Linux tools.  I don't really want to use Wine except as a last resort :-?

---

### Post by FuturePilot on 2007-07-03
I've done that before. But I used Winrar. You could try Unrar which is in the repos. But you might have to use it from the terminal to extract the contents. If that doesn't work, you'll probably have to use Wine and install Winrar.

---

### Post by bodhi.zazen on 2007-07-03
Take a look at this : [http://ubuntuforums.org/showthread.php?t=318789](http://ubuntuforums.org/showthread.php?t=318789)

---

### Post by cprofitt on 2007-07-03
You might have luck running it in wine; though to be honest it shocks me that Linux "friendly" IBM does not have a downloadable .iso file. There are alot of computers that do not have floppy drives these days.

---

### Post by stchman on 2007-07-03
> **Zill said:**
> IBM 6339 Netvista desktop PC:
I have downloaded file 21jt32a.exe to update the BIOS of this PC.  The instructions are to run this file (presumably with Windows!) which will then extract the required files to a self-booting floppy disk to flash the BIOS.

I have tried, unsuccessfully, to open the file with both unzip and unshield.

As I don't have Windows, any ideas please on what I could try next to extract the contents of this file to a floppy using other Linux tools.  I don't really want to use Wine except as a last resort :-?

Usually BIOS files are used in conjunction with a flashing program.  What it sounds like you have there is a .exe self extracting executable file.  You might be able to use WINE to extract it.  BIOS flashing is usually not done in Windows but in a pure DOS environment.

A lot of the mobo makers are just giving the .bin file.

---

### Post by stchman on 2007-07-03
Download the CD version, inside it there is a .iso file that can be extracted using an archive program.

---

### Post by FuturePilot on 2007-07-03
> **stchman said:**
> Usually BIOS files are used in conjunction with a flashing program.  What it sounds like you have there is a .exe self extracting executable file.  You might be able to use WINE to extract it.  BIOS flashing is usually not done in Windows but in a pure DOS environment.

A lot of the mobo makers are just giving the .bin file.

A lot of companies like HP have these Windows only flashing utilities where you can only flash the BIOS from inside Windows. So if you don't have Windows then you're pretty much screwed.:(
But basically what's in these .exe files is the .bin or sometimes the .rom file. So it's in there you just have to get it out. Sucks though.

---

### Post by stchman on 2007-07-04
Looks as though WINE will run the CD .iso .exe file.

[http://www-307.ibm.com/pc/support/site.wss/MIGR-4ZGSWX.html](http://www-307.ibm.com/pc/support/site.wss/MIGR-4ZGSWX.html)

Download:

21jz32usa.exe 2,216,104 Flash BIOS update (CD ISO image version)

Then run WINE on the .exe.  You will have a .iso file when you are done.

---

### Post by Zill on 2007-07-04
Thanks to all for the advice.  I am trying the various options suggested and am now experimenting with using Wine to produce the required floppy disk.

I will report back if I have any success :|

---

### Post by altonbr on 2007-07-04
An easier tutorial I used just last week: [http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html](http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html) [How to flash motherboard BIOS from Linux (no DOS/Windows, no floppy drive)?]

---

### Post by Zill on 2007-07-04
Thanks altonbr.  The problem I basically have is extracting the BIOS flash utility and BIOS image from the single .exe file.  This file seems to be self-extracting when run under DOS/Windows but cannot be unzipped with normal Linux tools.  I will see how far I can get with Wine...

ps.  I do have a floppy drive for use if/when I can extract the required files.

---

### Post by avik on 2007-07-04
There's always [cabextract]("http://www.kyz.uklinux.net/cabextract.php") that works on some exes.

---

### Post by altonbr on 2007-07-05
> **Zill said:**
> Thanks altonbr.  The problem I basically have is extracting the BIOS flash utility and BIOS image from the single .exe file.  This file seems to be self-extracting when run under DOS/Windows but cannot be unzipped with normal Linux tools.  I will see how far I can get with Wine...

ps.  I do have a floppy drive for use if/when I can extract the required files.

Oh sorry, that's what I get for not fully reading the thread.

---

