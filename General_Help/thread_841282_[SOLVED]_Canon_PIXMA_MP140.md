---
title: "[SOLVED] Canon PIXMA MP140"
date: 2008-06-26
forum: General Help
---

### Post by pbeesley on 2008-06-26
Good day fine sirs. I recently acquired a Canon PIXMA MP140. Now the printing side works great, straight out the box however, and here's the problem, I can't get the scanner to work. I tried Canon's own software (ScanGear) that installed itself and then disappeared. And I tried "Xsane" but it wouldn't find the scanner. Can anyone help.

Thank you and good day

p.s. I don't normally talk like this I'm just in a weird mood :lolflag:

---

### Post by geraldm on 2008-06-26
Canon Pixma MP140 is not a support scanner.  If you wish hardware to work, you should check what devices are supported before a purchase is made.

Gerald

---

### Post by pbeesley on 2008-06-26
not to worry Mr Army Man I got it free from BT. The printer works so meh

---

### Post by abhilashkumar on 2008-07-07
> **pbeesley said:**
> not to worry Mr Army Man I got it free from BT. The printer works so meh

the canon website has linux drivers for the mp145. you need to get the rpm version of the drivers and then convert to deb with alien. i had found detailed instructions but cant find them again.

scangear can be accessed by going into gimp and File->acquire->scangear mp

let me know if you were able to do it!

EDIT

Found the instructions that worked for me last time. I have the canon mp145
> 
1. install alien Symaptic Package Managerunder System, Administration.
2. Go to [HTTP://www.canon.com](HTTP://www.canon.com), Support and get the 4 required Linux Drivers. cuijfilter common and cuijfilter MP140 series, scangearmp common and scangearmp 140 series drivers. Download them to your desktop. Get the .rpm version only for this to work.
3. These files are in the .rpm format and they need to be converted to .deb.
4. use the terminal window. cd ~/Desktop. That will put you in the desktop.
5. Convert the files to .deb by using sudo alien --scripts scangearmp-common-1.10-1.i386.rpm and sudo alien --scripts cuijfilter-common-2.80-0.i386.rpm. These are only examples and you need to be exact or it will not work.
6. Double Click the .deb files and they will be installed. Install the common files first then the 140 series next.
7. Reboot the computer and the scanner will show up in the GIMP Image Editor, File, Qcquire, Scangearmp.
8. You then need to go to System, Administration, Printing and configure the MP 145. It is called the MP 140 series and Make and model is a Canon PIXMA MP150 CUPS ..........

---

### Post by pablosanchezuy on 2008-07-07
Well,  i have an MP160 and made it work with sane, not xsane.
xsane did recognized the scanner but could not scan, instead, xscanimage (provided with sane) worked like in 7.10, very nice. 

Maybe your problem was selecting the wrong driver when the printer was recognized . Ubuntu recognized the printer but assigned a "text" driver.
I changed it and voila .

Regards.

Pablo .

---

### Post by pbeesley on 2008-07-09
hmm ok I'll give that a go when I get home tonight. I'll let you know how I get on.

---

### Post by abhilashkumar on 2008-07-09
Pixma 140 series is supported as mentioned on canon's website. when you use the instructions i mentioned, you may at times not be able to print a test page, but you should be able to print from an application... like openoffice or gimp and also to use the scanner you need to go to the gimp... File-->acquire-->scangearmp

Let me know if it worked.

---

### Post by pbeesley on 2008-07-09
Yay Thank You this worked like a charm.

---

### Post by abhilashkumar on 2008-07-09
Glad it worked for you.
However, I am not the original author. I found the original instructions [HERE]("https://answers.launchpad.net/ubuntu/+question/22690")

---

### Post by nikiboom on 2008-08-06
Hello can anyone help? about my pixma mp140 printer? i have windows vista ultimate64bit OS and when i tried to isntall the driver and connect the printer, the printer is not recognize... i already downlooaded the lates driver from canon but it still unrecognized. im just wondering because microsoft tells us that it is vista compatible (32/64). can any one help me? thanks!

---

### Post by abhilashkumar on 2008-08-06
You should try using the drivers provided in the CD that accompanied the printer. If you are trying this on windblows oops... Windows, thats the best option.

---

### Post by manoynmonic on 2008-08-16
Hi, I had this printer/scanner working fine with the Canon scangear stuff - Until I upgraded to a 64bit system.  Now obviously those 32bit debs don't work.  I understand that the sane backends for the canon pixma mp140 are out now, but still in CVS.  Could someone please post the parameters I need to input to correctly install what I download from [http://www.sane-project.org/cvs.html](http://www.sane-project.org/cvs.html) ?  $man cvs has lots of helpful info, but how do I install the newly downloaded backends into the right directory?  Thanks!

edit: this seems to be what I needed.  [http://ubuntuforums.org/showthread.php?t=856996](http://ubuntuforums.org/showthread.php?t=856996)

---

### Post by ben2talk on 2008-08-22
cnijfilter-mp140series_2.80-1_i386.deb

Canon have come up with a debian package for us, nice move.

I downloaded it here:

[http://support-asia.canon-asia.com/EN/search?canonsearch=1&lang=EN&category=Multifunctional+Printers&series=PIXMA&model=PIXMA+MP145&menu=Download](http://support-asia.canon-asia.com/EN/search?canonsearch=1&lang=EN&category=Multifunctional+Printers&series=PIXMA&model=PIXMA+MP145&menu=Download)

---

### Post by o----o on 2008-09-11
works for me as well, just one thing, there where two Models, one common and one EN, the first one doesn't work for me, but the second. ;)
thanks

---

### Post by dargles on 2008-12-12
Thanks for the hints, folks.

Actually, following the leads, and in Hardy 8.04, I found this mind-numbingly easy (almost easy enough for an MS Zombie to follow :lolflag:)

[LIST=1]
[*]I followed the lead to the Canon site ([http://support-asia.canon-asia.com/EN/search?v%3aproject=AZZ-EN&binning-state=model%3d%3dPIXMA%20MP145%0Amenu%3d%3dDownload%0Aos%3d%3dLinux&]("http://support-asia.canon-asia.com/EN/search?v%3aproject=AZZ-EN&binning-state=model%3d%3dPIXMA%20MP145%0Amenu%3d%3dDownload%0Aos%3d%3dLinux&"))
[*]I downloaded **all four** Debian packages
[*]I installed the two **common** packages first by simply double-clicking them in the desktop :)
[*]I then installed the actual drivers (also by double-clicking)
[*]I did a reboot (I guess I can't shake off the MS Zombie thinking that a reboot never harms...)
[/LIST]

The only thing I then had to watch out for was that the printer manager didn't find the driver by default, and it's listed under MP140, not PIXMA MP140 like the rest of the PIXMA series, so I nearly missed it.

Also, Gimp finds the scanner and runs it a treat - but Open Office and Xsane can't see it.  I can live with that, but if anyone's got any hints - preferably ones that don't involve too much downloading and compiling of source code that breaks other stuff - I would be pleased to hear them.

Thanks, Guys - I love this ubuntu :guitar:
Regards, David

---

### Post by bizmeds on 2009-04-09
> **abhilashkumar said:**
> the canon website has linux drivers for the mp145. you need to get the rpm version of the drivers and then convert to deb with alien. i had found detailed instructions but cant find them again.

scangear can be accessed by going into gimp and File->acquire->scangear mp

let me know if you were able to do it!

EDIT

Found the instructions that worked for me last time. I have the canon mp145

After going to the canon site to look for the suggested drivers I only found the MP140 series Printer Driver Ver. 10.1.2.0 (Mac OS X CUPS) Is this the proper download? I tried searching for the cuijfilter common, cuijfilter MP_140 series,scangearmp common, scangearmp MP140 series but to no avail. Where did you find these downloads?

Thanks,

---

### Post by bizmeds on 2009-04-09
Thanks Dargles for your advice I followed your instructions however, when printing from open office a receive an error. I tried to run a test from the print manager and received this error:
 client-error document format not supported

Opening the print manager under the settings tab change the make and model I selected the MP150 and all worked fine. Problem was that the driver was not recognized 

Thanks to all!!

---

### Post by ben2talk on 2009-11-16
I would like to leave one note here though - use Virtualbox with an XP installation, with the original Canon software installed - it gives more options, and the quality of printing is much better (Canon is great for images, but not on Linux - that's fine for text and stuff).

---

### Post by augustoschwartz on 2011-06-27
:popcorn:
Had posted the links to the download site and tried to convert the files as indicated. Disposal and got here the 02 files **.deb** for anyone interested: [http://www.4shared.com/file/PFEVha63/MP140_COOPERSOLVENDANOVA.html](http://www.4shared.com/file/PFEVha63/MP140_COOPERSOLVENDANOVA.html)

Change the permissions to run as a program.
> [cd ~/MP140_COOPERSOLVENDANOVA
sudo chmod-x *]
>> Where [*] are all the files in the folder.

First install: cnijfilter-common_2.80-2_all.deb
Then install: cnijfilter-mp140series_2.80-2_i386.deb

Be happy.

---

