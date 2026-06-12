---
title: "Bad Performance / Significantly worse than on Windows 7"
date: 2015-05-17
forum: General Help
---

### Post by juri4 on 2015-05-17
Hey,
today i've installed Ubuntu 14.04.2 on a decent hardware setup.
To my suprise the whole desktop/browser(firefox)/system performance was much lower than on Windows 7.
Can anyone relate to this problem ?
I thought it could be a driver issue ?

**MY SETUP**
_Processor:_ *Intel(R) Core(TM) i5-2400 CPU @ 3.10GHz*
_GPU:_ *AMD R9 290X*
_RAM:_*8 GB DDR3 RAM*
_Mainboard:_ *ASUS P8P67LE *
_System storage:_* SSD | Samsung 840 EVO 120GB*

---

### Post by Vladlenin5000 on 2015-05-17
```
_GPU:_ *AMD R9 290X*
``` <- This usually requires proprietary AMD drivers. The open source (and default) driver you currently have - *Radeon* - hasn't been optimized for newer chips like the R9.

You should be able to install them easily. System Settings > Software & Updates. Find the rightmost tab, additional drivers, allow some time to check your system and finally select the recommended *fglrx.*

---

### Post by QIII on 2015-05-17
In testing the R9 290X, I found that the performance of the open source   Radeon driver was, in a word, terrible.  While I absolutely commend the   developers of the open source Radeon driver for their hard and  ceaseless  work, I don't think they've caught up to this batch of GPUs  yet.

I  would also recommend using the proprietary driver, which generally  can  be installed via "Additional Drivers" or the command line.  I  prefer the  command line because it is easy to also install hardware  acceleration.
[B]
However[/B],  there is a bug with the new Hardware Enablement Stack  that causes  installation of the proprietary driver to fail when  running 12.04.5 and  14.04.2.  You can install it from the  trusty-proposed repo.

My  findings with regard to the driver and my post in the bug report   detailing how to install from -proposed are in a couple of articles in   my blog, which is linked in my signature.  Also linked is the Community   ATI Wiki, which goes into some detail about adding the hardware   acceleration packages.

OK.  Now that the servers seem to be playing nice: [ Here's ]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1424491")the bug report.

---

### Post by juri4 on 2015-05-18
Thanks for your help-
I followed your link and used the method described in post #24
> [TABLE]
[TR]
[TD][Néstor Acevedo (sainthyoga2003)]("https://launchpad.net/%7Esainthyoga2003")             wrote             on 2015-03-03:                          [/TD]
                       [TD="class: bug-comment-index"]           [ #24]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1424491/comments/24")           [/TD]
         [/TR]
            [/TABLE]
                               OK I've fixed it:
 # sudo apt-get install xserver-xorg-core
# sudo apt-get install libcheese*

 and finally do sudo apt-get install fglrx.
 Hope it can be usefull to someone, but still I think this bug have to be fixed.


              

But i had to run sudo apt-get install libcheese* first. Becuase "sudo apt-get install xserver-xorg-core" seems to be dependent on this.
Now it works **like a charm** !

---

### Post by leunam12 on 2015-05-18
Good because worse than Windoze 7 is really bad!

---

