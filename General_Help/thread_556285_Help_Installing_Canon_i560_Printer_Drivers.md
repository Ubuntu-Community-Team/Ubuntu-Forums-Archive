---
title: "Help Installing Canon i560 Printer Drivers"
date: 2007-09-21
forum: General Help
---

### Post by Taxi on 2007-09-21
I'm trying to add Canon's drivers for my i560, but they're not showing up in the Driver section of the printer's Properties in Adminstration -> Printing when I select Canon as the manufacturer (and I don't believe it's hiding under some other manufacturer, either).  I'm using Feisty and I followed the directions from post #24 of this thread: [http://ubuntuforums.org/showthread.php?t=10540&page=3](http://ubuntuforums.org/showthread.php?t=10540&page=3)

> **ferrill said:**
> I got it working very well here is what I had to do:

1. Get the correct drivers from here: [ftp://download.canon.jp/pub/driver/bj/linux/](ftp://download.canon.jp/pub/driver/bj/linux/)
(they cover i550, i560, i850,i860,i950, i990)

You need:
bjfilterpixusXXXi-X.X-X.i386.rpm
AND the corresponding cups driver:
bjfiltercups-X.X-X.i386.rpm

2. use alien to convert the rpms to debs (apt-get install alien if you dont have it)
sudo alien -c <rpm package>

3.
dpkg -i bjfilterpixusXXXi_X.X-X.i386.deb
dpkg -i bjfiltercups-X.X-X.i386.deb

4.
apt-get install libtiff3g
apt-get install libpng2

5. sudo /etc/init.d/cupsys restart

6. Then remove BJC-7000 driver.  System > System Settings > Printing, right click on the printer and select remove.  If you do not delete other driver referencing the printer when print from an application it will never get sent to the printer.

7. Then use the gnome gui for adding a new printer
System > System Settings > Printing
And you will now see your new driver in the list as PIXUS XXXi verX.X

I followed the directions pretty closely, using the files bjfilterpixus560i-2.4-0.i386.rpm and bjfiltercups-2.4-0.i386.rpm from Canon.  The only thing I am aware of having done differently was using libtiff4 and libpng3 from the current repositories, but post #1 was updated by the original poster saying that those should work, too.

I initially tried the instructions from post #1 in that thread, but apparently there are scripts in one of the packages that need to be translated as well, so after I finished the instructions and that attempt failed I used the "alien -c" in those later instructions in order to avoid that error.  The only thing that I noticed that seemed out of the ordinary was that every time it converted the .rpm's to .deb's it said "hostname: Unknown host" in the terminal twice for each file it converted.  I don't know what it's talking about, but *maybe* it's significant?

I'm aware and glad that the i560 seems to be somewhat supported by the drivers that came with Feisty, but I'd like to get the Canon drivers to work.  (I'm hoping they'll have low/out of ink notifications, printer maintenance, etc. like in Windows.)  Oh, and I do still have a Windows installation with installed drivers for the printer if there's anything worthwhile in there.  I'd appreciate any help anyone can give me.  I'm new to Ubuntu, as well as GNU/Linux in general, so please be somewhat explicit in any instructions you give.  And of course I'd be happy to provide any additional information, as long as you tell me how to find it.

Thank you!

---

### Post by Taxi on 2007-09-21
I think I might have originally posted this at the wrong time of day...

Does anyone have any tips/suggestions?

---

