---
title: "Canon Printer is Very Slow in Ubuntu 14.10"
date: 2014-11-26
forum: General Help
---

### Post by Acharn on 2014-11-26
I've just installed Ubuntu 14.10 to a USB 3.0 stick and in general I'm OK with the speed. I have room on my hard drive that I could install it there, but for the moment I prefer this. Anyway, I was really pleased with how easy it was to install my Canon PIXMA MG3570 printer. Maybe not quite as easy as Windows 7, but really easy as it should be. Now I'm a little disappointed at the speed. It seems as if the printer is printing at a much higher resolution than it does in Windows. A page takes almost 30 seconds to print out. I don't see any obvious settings in the printer windows. Everything seems to be set to "normal" or "average." Luckily, I don't print very much. Canon doesn't have a driver for this printer for Linux, and on the test page Ubuntu identifies the driver as STP00431.PPD, Canon MG3500 series, which sounds right. Anybody know of any way to set things to move faster at the sacrifice of print quality?

---

### Post by pdc on 2014-11-27
> Canon doesn't have a driver for this printer for Linux,

............actually, .................................they do: they provide linux drivers in debian and rpm packages; and as source code;

so for your 3500series device, go here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100550402.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100550402.html) and can I suggest downloading and saving the file which is [COLOR="#008000"]cnijfilter-mg3500series-4.00-1-deb.tar.gz[/COLOR]

.....assuming your setup is that downloaded files are saved to the Downloads directory, the commands in a terminal; (hit ENTER after each paste .....) .........are...........

```
cd Downloads
```

```
tar -zxvf cnijfilter-mg3500series-4.00-1-deb.tar.gz
```

```
cd cnijfilter-mg3500series-4.00-1-deb
```

```
./install.sh
```

and that will run the install script and set up the driver for you

(It is a version 4.0 driver so libtiff4 is not needed ............)

_____________________

Canon provide [COLOR="#0000FF"]ScanGearMP[/COLOR] for you for the scanner side of the device: go here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100552102.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100552102.html) and the file installs in the format of the printer driver

---

### Post by Acharn on 2014-12-01
Thank you so much. Sorry for the delay getting back to you. This driver works perfectly. Wonder why I couldn't find one on the U.S. site. Anyway this is just what I hoped for. Thanks, too, for pointing me to the scanner driver. I hadn't even thought of that yet.

---

### Post by pdc on 2014-12-01
glad you got the driver installed; 

> Wonder why I couldn't find one on the U.S. site ...........yes, it seems a curious feature of the US Canon website; various folks report it does not link to the very large library of Canon linux drivers

---

