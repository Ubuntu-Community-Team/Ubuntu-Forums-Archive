---
title: "flightgear"
date: 2007-02-16
forum: General Help
---

### Post by hca on 2007-02-16
According to documentation (which is otherwise superb) all options are optional, but clean start gave this result on the console:

hca@hca-desktop:~$ fgfs
Error reading properties: 
Failed to open file
 at /home/hca/.fgfs/autosave.xml
 (reported by SimGear XML Parser)
freeglut (fgfs): Unable to create direct context rendering for window 'FlightGear'
This may hurt performance.
  Model Author:  Unknown
  Creation Date: 2002-01-01
  Version:       $Id: c172p.xml,v 1.17 2006-03-13 15:27:14 ehofman Exp $
  Description:   Cessna C-172
Segmentation fault (core dumped)
hca@hca-desktop:~$

Then a new try based on further reading of documentation i tried :hca@hca-desktop:~$ fgfs --timeofday=noon
Error reading properties: 
Failed to open file
 at /home/hca/.fgfs/autosave.xml
 (reported by SimGear XML Parser)
freeglut (fgfs): Unable to create direct context rendering for window 'FlightGear'
This may hurt performance.
  Model Author:  Unknown
  Creation Date: 2002-01-01
  Version:       $Id: c172p.xml,v 1.17 2006-03-13 15:27:14 ehofman Exp $
  Description:   Cessna C-172
Segmentation fault (core dumped)

So now I need to be informed which options are needed or  is the problem something else.

---

### Post by roland on 2007-02-17
A segmentation fault means that memory needed to run the program is corrupted (see [Wikipedia](http://en.wikipedia.org/wiki/Segmentation_fault)). For example, if part of the RAM-memory in your computer is broken, and the program gets a broken bit of memory assigned, it won't work. Another cause may be bad programming from the creators of the software. But if that was the case, everyone using the software would have this problem and it would be more known of. So I'm afraid it is the broken memory.

Solution: try to map the broken parts of the RAM memory with memtest86. You can start this program on bootup. Assuming you use GRUB, you get a bootup-screen with some startup options before booting Ubuntu. If you get the message "Press Esc for GRUB menu", please do so. Then you can choose memtest86. If you can't, please post it here, so I can tell you how to get it in the menu. Then, let memtest86 run for a while (depending on how much RAM-memory you have, this can take long to very long), and it could give error messages from a certain point. I will explain.

Assume you have 512 MB of RAM-memory, divided on two physical strips of 256 MB memory on the motherboard. If memtest86 will give errors from megabyte no. 256, you know that the second strip of memory is broken. The solution is then to buy a new memory strip (maybe with more than 256 MB) to replace the broken one. Then run memtest86 again, to see if the errors are gone.

I know this is a real hassle, I've had this problem with my own computer as well, and memory is expensive. I hope this helps, please post any results here. By the way, the Cessna C-172 is a really nice plane!

---

### Post by hca on 2007-02-17
thank you!
i'll
follow up on this and revert ASAP
/Hans Christian

---

### Post by hca on 2007-02-17
> **roland said:**
> A segmentation fault means that memory needed to run the program is corrupted (see [Wikipedia](http://en.wikipedia.org/wiki/Segmentation_fault)). For example, if part of the RAM-memory in your computer is broken, and the program gets a broken bit of memory assigned, it won't work. Another cause may be bad programming from the creators of the software. But if that was the case, everyone using the software would have this problem and it would be more known of. So I'm afraid it is the broken memory.

Solution: try to map the broken parts of the RAM memory with memtest86. You can start this program on bootup. Assuming you use GRUB, you get a bootup-screen with some startup options before booting Ubuntu. If you get the message "Press Esc for GRUB menu", please do so. Then you can choose memtest86. If you can't, please post it here, so I can tell you how to get it in the menu. Then, let memtest86 run for a while (depending on how much RAM-memory you have, this can take long to very long), and it could give error messages from a certain point. I will explain.

Assume you have 512 MB of RAM-memory, divided on two physical strips of 256 MB memory on the motherboard. If memtest86 will give errors from megabyte no. 256, you know that the second strip of memory is broken. The solution is then to buy a new memory strip (maybe with more than 256 MB) to replace the broken one. Then run memtest86 again, to see if the errors are gone.

I know this is a real hassle, I've had this problem with my own computer as well, and memory is expensive. I hope this helps, please post any results here. By the way, the Cessna C-172 is a really nice plane!

i tried this but could not get to the possibility of pressing ESC for GRUB menu; but I had a diskette lying around booting Memtest-86 v. 3.0. It indicated no memory errors after some 20 minutes of testing and after having performed all of pass 1. 

I do want to have the simulator running, so I download the w98 version from flightgear.org. I could install it using wine, but I could not make it placing the necessary menus for disposal. But it might be a possibility of getting up flying!

---

### Post by roland on 2007-02-18
Maybe it is an installation issue after all.. Sorry for the amount of time I let you spend on checking RAM-memory (at least you now know for sure that your RAM-memory is just fine).

If you uninstall the program, and then install again, will that help? If that doesn't, I'm afraid I'm out of memory myself..

---

### Post by hca on 2007-02-18
Thank you for your efforts.
Yes, I tried do do a de-dre-install , alas with the same negative result. But other people have made it running, so it must be some other defect in my set-up.
Believe me, I keep on trying till I have a satisfactory result. I am very interested in model airplanes, and have built my first RC project in order to resume with my childhood hobby (50 years ago) and I have, I believe, sufficient experience from my professional carrier to work towards my goals.
Best regards
Hans Christian Andersen, Holte, Denmark

---

