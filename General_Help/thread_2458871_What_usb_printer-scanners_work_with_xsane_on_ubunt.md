---
title: "What usb printer-scanners work with xsane on ubuntu 20.04"
date: 2021-03-05
forum: General Help
---

### Post by wiz70 on 2021-03-05
[COLOR=#141414][FONT=&quot]I have wasted numerous hours trying to get a older Brothers printer-scanner working on 20.04. Printer works, not scanner... Even contacted xsane Gitlab and found that it wasn't supported. But yet I got it to work on 18.04. So, WHY CAN'T I FIND A ANSWER TO: what usb printer- scanners work with xsane on ubuntu 20.04. I spent a lot of time searching for what printer-scanners will work and all I find is one after another post of people trying to get their scanner working. SO, if I have to buy a new usb printer-scanner, I need to know WHAT Scanner of a USB Combo unit WILL WORK............[/FONT][/COLOR]

---

### Post by QIII on 2021-03-06
Bump

---

### Post by Quarkrad on 2021-03-06
I've always had success with hp printers. Currently got hp Envy. See [https://developers.hp.com/hp-linux-imaging-and-printing](https://developers.hp.com/hp-linux-imaging-and-printing)

---

### Post by mIk3_08 on 2021-03-06
What brother printer/scanner do you have? can you specify your printer? model? I have my brother printer/scanner works via wifi, it works smoothly on 18.04 but I haven't tried it on 20.04 cause I don't have any machine for testing purposes. If I do I have tested it for you. I used this printer for few years now. My scanner works with simple scan app and xsane via wifi. and why you change your Ubuntu O.S from 18.04 to 20.04? you still have few years to use your 18.04.

---

### Post by dragonfly41 on 2021-03-06
On reading this I was reminded that I have an old Canon LiDE 600F gathering dust which I would like to run on Ubuntu 20.04.

I will try VueSCAN .. [https://www.hamrick.com/vuescan/supported-scanners.html](https://www.hamrick.com/vuescan/supported-scanners.html)

I connected the old scanner via USB cable but I see this report ...

```
VueScan didn't find a scanner connected to your computer.


1) Make sure the scanner is plugged in and turned on before you run VueScan.
2) If you have a USB scanner, try a different USB cable and/or a different USB port.
3) If you have a WiFi scanner, make sure your firewall isn't blocking responses from the scanner.
4) If the scanner has a locking switch, make sure it's in the unlocked position.
5) Try turning your scanner off and back on.
6) If you have a USB scanner, try running VueScan as root to see if it's a libusb device protection problem.

Then exit VueScan and run it again.
The supported scanners list has more useful information about your scanner. Would you like to see this?
```

If I can get this to work I will add a note here.

[Added Note]
I tried on Ubuntu 20.04 but this scanner is not supported.
Then I tried on dual boot Windows 10, and although the scanner was detected by VueScan
when I then tried to download Canon driver I learn that it is not supported on Window 10.
My only (Windows) option offered by Canon is to install earlier Windows XP or Windows 2000 in another partition.
I guess I will have to write off this scanner. It was/is a good product otherwise.

...

Another thought. I might try installing old Windows XP on an old laptop drive, in an external USB docking bay, just to drive this scanner with no access to internet allowed. I guess that I would then have to disable the Windows 10 boot flags in my PC internal drive. A bit messy but worth a try.

---

### Post by ajgreeny on 2021-03-06
It is now usually easier, I find, to get a wireless printer/scanner working than using via USB.

Does your printer have wifi connection? If it does, try using that instead of USB, but give it a static local IP, maybe easiest done in the **router setup -> Reserved addresses**.

---

### Post by dragonfly41 on 2021-03-06
Progress.

Since experimenting with VueScan and Canon, without much success, I searched around and found this site.


[http://www.juergen-ernst.de/info_sane.html](http://www.juergen-ernst.de/info_sane.html)


I used Synaptic to install
libdevice-usb-perl-0.38-1
Next I downloaded the perl script
canoscan600f-20130118.pl (36.7 kB)


Renamed to scan.pl
Connected my Canon LiDE 600F through USB 2 port (I read somewhere not to use USB 3).
Inserted a document in scanner and ran ..
sudo perl scan.pl
It chunters away and produces a scan.ppm which I can open.
At least this is a start,


This all followed from reading ...

[https://superuser.com/questions/32393/canon-scanner-lide-600f-linux-driver](https://superuser.com/questions/32393/canon-scanner-lide-600f-linux-driver)

> The CanoScan LiDE 600F is a very good scanner. But it has the disadvantage that Canon is unwilling to release the necessary documentation to enable a Linux driver and SANE backend to be written.

[http://www.juergen-ernst.de/info_sane.html](http://www.juergen-ernst.de/info_sane.html)

=====================================

[Later Edit]
Returning to OP's issue with Brother scanner, which I have no experience with, I did find this in my reading ...

[https://itsfoss.community/t/help-me-use-my-brother-scanner/3147/2](https://itsfoss.community/t/help-me-use-my-brother-scanner/3147/2)

---

### Post by wiz70 on 2021-03-08
Sorry I hadn't got back before now.  Scanner is a DCP7040.  Connections is via USB.   Yup it worked fine on Ubuntu 18.4.  But there are issues about the lib's and locations, permissions , backends.   I have been working with a maintainer from Xsane GitLab.  We have tried numerous  approaches and maybe hit a block wall.  If we come up with a solution, I'll post it here.  But, any information is always helpful... Thx

---

### Post by him610 on 2021-03-08
Did you try the drivers provided by Brother?
[https://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=dcp7040_us_as&os=128]("https://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=dcp7040_us_as&os=128")
Download the Driver Install Tool.
Be sure to read and follow instructions.

---

### Post by wiz70 on 2021-03-09
Brother drivers were installed but they aren't talking to xsane.. That's were the problem lies...

---

### Post by wiz70 on 2021-03-21
Spent a lot of time working with the maintainer of Xsane trying many different steps and with the suggestion from member of this site, I got the scanner working.

 
[LIST=1]
[*]Install the older libusb library that aren't present in 20.04
[/LIST]
sudo apt install libusb-0.1-4
[LIST=1]
[*]Install Brother's scanner drivers from their website. It will put the libs into /usr/lib64/sane where Ubuntu will not find them.  


3. [FONT=Arial]In 64-bit Linux Mint 19.x and Ubuntu 18.04 & 20.04 the location for the supporting library files has changed, and the driver for the scanner feature doesn't always take that into account. The Brother driver then puts them in [/FONT][COLOR=blue][FONT=Arial]/usr/lib64[/FONT][/COLOR][FONT=Arial], whereas your operating system expects them in [/FONT][COLOR=blue][FONT=Arial]/usr/lib[/FONT][/COLOR][FONT=Arial].[/FONT]

[FONT=Arial]So for a 64-bit system, you now need to execute the following three commands in order to make your scanner work well ([/FONT][use copy/paste]("https://easylinuxtipsproject.blogspot.com/p/copy-paste.html")[FONT=Arial] to transfer them one by one to the terminal, and press Enter after each command):[/FONT]
[COLOR=blue][FONT=Arial]sudo ln -sf /usr/lib64/libbrscandec*.so* /usr/lib[/FONT][/COLOR]
[COLOR=blue][FONT=Arial]sudo mkdir -p /usr/lib/sane[/FONT][/COLOR]
[COLOR=blue][FONT=Arial]sudo ln -sf /usr/lib64/sane/libsane-brother*.so* /usr/lib/sane

[/FONT][/COLOR]Thanks for all the help and suggestions






[/LIST]

---

### Post by wiz70 on 2021-03-21
Solved

---

