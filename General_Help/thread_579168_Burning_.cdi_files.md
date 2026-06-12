---
title: "Burning .cdi files"
date: 2007-10-18
forum: General Help
---

### Post by SupWiz17 on 2007-10-18
I have been searching this forum and google all day trying to find a way to burn a .cdi file to a cd. Has anyone ever done this with ubuntu? Any help would be appreciated.

---

### Post by SupWiz17 on 2007-10-18
I tried to conver the .cdi files to .cue files and burn them with k3b but they still dont boot up in my dreamcast. I was thinking I could run Diskjuggler in wine but it doesnt work does anyone have any help with that.

---

### Post by SupWiz17 on 2007-10-18
no one

---

### Post by A Whale Of A Time on 2008-01-08
I would love a solution.

---

### Post by celticninja on 2008-01-28
This is how i do it:

I first get the .cdi file

convert it to a .nrg file with this program, CDI2NERO, [http://www.megagames.com/dc/dc_utils_disk.shtml]("http://www.megagames.com/dc/dc_utils_disk.shtml")

(since its a windows program you have to use WINE, but it doesn't ever have an problems)

and after its done converting, i burn it with Nero Linux v3

So far i haven't had any problems with it. and all of my discs work great



Hope this helps

---

### Post by tghe-retford on 2008-02-04
Thanks for the advice. I myself would like to try a homebrew cdi for my Dreamcast but the free programs I used on Windows do not work through Wine and I can't find a way to do it through Linux. CDI2ISO in the repositories don't work with Dreamcast images and only create expensive cup mats. Some posts I read suggest not converting CDI files to other formats as it messes up the self-boot structure on the discs.

Is there any way to burn an image without Nero Linux 3, its just that a) you have to pay for it and I don't have the money to spend on software; b) I can't download the trial from the official website.

There was one way to burn CDI images using the command line that I found doing a search through the forums but its very technical and the commands look scary! I can't make head or tail of the readme. :(

---

### Post by tghe-retford on 2008-02-04
I've done some research in the hope this will help people in the future.

I tried the CDIrip/CD Record method as linked to in this thread:

[http://ubuntuforums.org/showthread.php?t=12277](http://ubuntuforums.org/showthread.php?t=12277)

and the operation failed with the error message "Unsupported image version".

I also tried converting the CDI image to NRG and then to ISO so I could burn it, but as I predicted, all it did was create a cup mat which would not work in the Dreamcast. Another idea of using Kiso in the repostories to convert CDI to ISO and then burn it using a CD burner also didn't work.

The package for the Graveman program says it can burn CDI images, but I can't see how to when I explore the program, it only shows options to burn an ISO to CD.

There is one program called Gear Pro which can burn the CDI files natively on Linux. Just one problem, its $799.99!

I think CDI burning is one of those things at the moment can only be done with paid for software or having to use Windows for the free software. WIne cannot run the free software I used to use on Windows. Shame really. :(

---

### Post by tghe-retford on 2008-02-08
Tried another homebrew CDI image, this one did work with CDIrip with these instructions:

[http://www.poptix.net/CDI-HOWTO.txt](http://www.poptix.net/CDI-HOWTO.txt)

 I burned the CD successfully using CDBurner. Tried it in the Dreamcast and it wouldn't boot. I got kicked back to the Dreamcast BIOS audio CD player. Selecting the play option booted the console, but it went back to the audio CD player again.

Another cup mat to add to the previous three I sacrificed to see whether it is possible to burn a CDI image using Linux without having to empty a wallet to use proprietary software.

---

### Post by tghe-retford on 2008-02-14
A temporary solution that I found does work but requires Wine is to use the trial version of Alcohol 120% version 1.9.5 (other versions do not work according to the WIne AppDB), and follow the instructions on this page:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=5500&iTestingId=13225](http://appdb.winehq.org/objectManager.php?sClass=version&iId=5500&iTestingId=13225)

The trial is time limited so it isn't a permanent solution, but it may help someone who really needs to burn a cdi. It would be better to have a free (as in speech and beer) Linux native solution but there isn't one at the moment.

I hope this helps someone in the future and the Dreamcast community.

---

### Post by weihenstephan on 2008-05-01
> **celticninja said:**
> 
convert it to a .nrg file with this program, CDI2NERO, [http://www.megagames.com/dc/dc_utils_disk.shtml]("http://www.megagames.com/dc/dc_utils_disk.shtml") and after its done converting, i burn it with Nero Linux v3


Thanks for this hint! As the author even put up the sources, I have created a Linux version (unfortunately I wasn't able to reach the original author, so I've put it up on [http://digitalimagecorp.de/software/cdi2nero/]("http://digitalimagecorp.de/software/cdi2nero/")).

The CDIrip / cdrecord approach should also work, with two modifications from [http://www.poptix.net/CDI-HOWTO.txt]("http://www.poptix.net/CDI-HOWTO.txt"): First, I didn't have to patch cdrecord, it worked out of the box (Note: I didn't use cdrecord distributed with Ubuntu, but the original cdrecord, as I don't have a CD recorder in my Ubuntu laptop; maybe someone could check if it also works with this version?). And second, I had to use *cdrecord dev=1000,1,0 speed=4 -v -multi -xa tdata02.iso* (not *-xa1*) to burn the data track.

Converting a Dreamcast image to a single ISO will most probably never work, as the Dreamcast needs several tracks to be able to boot, and ISO images can only contain one track. cdi2iso only extracts the data track I think, but I haven't checked that any further.

---

