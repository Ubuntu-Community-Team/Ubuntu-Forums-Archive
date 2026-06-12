---
title: "How you clone one usb drive to smaller one!"
date: 2017-08-13
forum: General Help
---

### Post by Jan_Johansson on 2017-08-13
I looked around for a easy solution or tool to do this, as I'm not so  good at command line, but all I found were very technical and command  line options, and very few could clone something to smaller drive(only  larger) and most had to be from livecd - so I tried to figure this out  myself and here are the results:


1. First you take the NEW drive and make it bootable the same way as the original drive. Then unmount and re-mount it.


2. Then remove whatever files is on it.


3. Then copy the the contents of the original drive to the NEW drive.


4. Use Gparted or any other partition tool to verify that the NEW drive is bootable, then take it for a spin.


Finished.




In my case I had made my original drive with Yumi for windows(yes there  are a linux version but you have to look elsewhere than Software center,  Sourceforge is a good bet) - So I took the NEW drive and made it bootable  with Yumi for windows(but could just as well have used the linux one)  and followed the steps above. And all works as it should.


If I helped you than a thank you goes long way[IMG]https://ubuntuforums.org/images/smilies/icon_smile.gif[/IMG]

---

### Post by TheFu on 2017-08-14
**fsarchiver** or **rsync** will work, provided the amount of data is small enough to fit on the smaller flash drive.  It isn't a "clone" - that means something EXTREMELY SPECIFIC - but it will have all the data.

---

