---
title: "Canon MX925 scanner recognized [sometimes], but won't scan [all the time]"
date: 2015-01-31
forum: General Help
---

### Post by crazybear on 2015-01-31
I have a Canon, Pixma MX-925 [920 Series drivers for Linux]. I installed the drivers. 
If I type into terminal sudo sane-find-scanner
I get: found USB scanner (vendor=0x04a9 [Canon], product=0x176b [MX920 series]) at libusb:001:004

Good, but - when I type in scanimage -L
I get: No scanners were identified.

I have spent about a two days time trying various 'solutions' suggested on various places. Either it didn't work or I couldn't understand what in the World I was supposed to do. [lots of both].

Any suggestions?

---

### Post by pdc on 2015-01-31
Hi crazybear;

so to run the scanner side of your MX920 series device, Canon provide [COLOR="#0000FF"]ScanGearMP[/COLOR] to run the scanner; so that is their programme; and different from [COLOR="#008000"]xsane[/COLOR]; which is a front-end to run the open-source programme [COLOR="#008000"]sane 
[/COLOR]
so you have installed [COLOR="#0000FF"]ScanGearMP[/COLOR]?

The quickest way to check would be to have your printer turned on; and connected and type ```
scangearmp
``` in a terminal; hit the enter key and do you get ScanGearMP opening for you?

If so, one creates a launcher on Ubuntu ..................... to launch it from a GUI .................

____________

if we do things one by one: how goes it with the scangearmp command please?

---

### Post by crazybear on 2015-02-01
...it is searching for scanners and taking a very long time. 
It gave a strange reply:[COLOR=#0000cd] Xlib:  extension "RANDR" missing on display ":0.0".
[/COLOR]Nothing is wrong with the three displays.
...but then when I ran scangearmp again, it opened up a tab on my browser and I was able to scan and save the file. 
However, none of the three front end programs I have detect any scanner.

Does any of this information below help anyone to figure this out? Am I going to have to do scanning by command line only?

found USB scanner(vendor=0x04a9 [Canon], product=0x176b [MX920 series]) atlibusb:001:004


-----postinst

 #!/bin/sh
PRINTER_DEPEND_PKG=scangearmp-mx920-417
model_num=`echo${PRINTER_DEPEND_PKG} | cut -d- -f3`
if [ -x/sbin/ldconfig ]; then
    /sbin/ldconfig
fi
# remove cncp* libs
for LIBS inlibcncpmsimg libcncpmslld
do
    if [ -h/usr/lib/${LIBS}${model_num}.so ]; then
        rm -f/usr/lib/${LIBS}${model_num}.so
    fi    
    if [ -h/usr/lib/${LIBS}${model_num}c.so ]; then
        rm -f/usr/lib/${LIBS}${model_num}c.so
    fi    
done


-----postrm

#!/bin/sh
if [ -x/sbin/ldconfig ]; then
    /sbin/ldconfig
fi
----

---

### Post by pdc on 2015-02-01
can you open a terminal please; and copy the command from here ```
dpkg -l | grep scangear
``` and then please paste it into the terminal; and then please copy the result and paste it back here

---

### Post by crazybear on 2015-02-01
$ dpkg -l | grep scangear
ii  scangearmp-common                                           2.10-1                                              ScanGear MP for Linux.
ii  scangearmp-mx920series                                      2.10-1                                              ScanGear MP for Linux.

is what I got. Obviously it is partly 'installed' and I can scan via command line. That's the good part. However, I'd like to be able to use the scan button on the printer/scanner, as well as the front-end programs I have. Xsane gives a 'no scanner found' and then when I hit help it gives the list of some [not all] of the various things I've seen mentioned on the internet in various places about this....

what's next?

---

### Post by pdc on 2015-02-01
so ScanGear is working for you; and it comes from Canon; 

__________________

so completely separate.....................different.................is ...................

Xsane; which is the GUI front-end to drive SANE, the open-source initiative [http://www.sane-project.org/](http://www.sane-project.org/) and when you look in that, in supported devices you find that your 920 series is listed as 

> 0x04a9/0x176b 	[COLOR="#FF0000"]Untested 	Testers needed![/COLOR]

________________

so it is the sane-pixma backend that would drive your device; if they could have some help to get it going; [http://www.sane-project.org/man/sane-pixma.5.html](http://www.sane-project.org/man/sane-pixma.5.html)

you would be just the guy to help them: the above link tells you how to contact them

_______________

the latest of the sane releases is from here [https://launchpad.net/~rolfbensch/+archive/ubuntu/sane-git](https://launchpad.net/~rolfbensch/+archive/ubuntu/sane-git) and like all the advisories, it is called untrusted because not official; but you will find Rolf works very hard on the sane project; and so is very well regarded; and many recommend adding his ppa 

............why I mention it is your MX920 series may be covered by this; so if we try that first? ............and if no joy, you could work with them to get it recognised ..................

so to add the latest the command is ```
sudo add-apt-repository ppa:rolfbensch/sane-git
```

and then ```
sudo apt-get update
``` and then if a comprehensive command ```
sudo apt-get install libsane sane-utils libsane-dev libsane-common
``` to make sure you have all 

________---

you can see in this recent posting, [http://ubuntuforums.org/showthread.php?t=2261650&page=2&highlight=canon](http://ubuntuforums.org/showthread.php?t=2261650&page=2&highlight=canon) that someone used the Rolf ppa and it solved their problem

---

### Post by crazybear on 2015-02-02
Well, now some front ends seem to work and others [XSane] used to open and report it couldn't find a scanner, but now open and then collapse [disappear] before I can even see anything.....but one [Skanlite] seemed to work on a test document. I need to see if all the functionality is there. With the scangearmp I couldn't find any functionality to crop, which is something I often want to use with a scan. On Skanlite, with one try, the crop worked only partly - and after adjusting brightness and contract the image no longer appeared...so all it not perfect, but better. Thanks. XSane is the highest rated, but simply won't work now....collapses instantly...sigh...tried re-installing it and such.

---

### Post by pdc on 2015-02-02
Hi crazybear; it must all be a bit frustrating; but the sane folks don't have the hardware to get the 920 series going; you do;

can I urge you to contact the sane-pixma folks; best way seems to be to subscribe to the sane development mailing lists; [http://lists.alioth.debian.org/mailman/listinfo/sane-devel](http://lists.alioth.debian.org/mailman/listinfo/sane-devel)

please join and hopefully the right folks will see your post; you can run some diagnostics for them

---

### Post by crazybear on 2015-02-18
> **pdc said:**
> Hi crazybear; it must all be a bit frustrating; but the sane folks don't have the hardware to get the 920 series going; you do;

can I urge you to contact the sane-pixma folks; best way seems to be to subscribe to the sane development mailing lists; [http://lists.alioth.debian.org/mailman/listinfo/sane-devel](http://lists.alioth.debian.org/mailman/listinfo/sane-devel)

please join and hopefully the right folks will see your post; you can run some diagnostics for them

Sorry to say, this has not been a good experience. I joined sane-devel and was after two short posts told to 'go away' and ask the developer of Xsane. He, in turn, said he couldn't help much and that I should join 'scanners'. Meanwhile, my Xsane doesn't work in Ubuntu 12.04 and no one knows [or tries to help figure out how to debug] the problems. I'm just being pushed from one group to another......;-(

---

### Post by birkopf on 2015-02-18
I also have Canon scanner/Printer and I solved this differently. I would suggest to remove everything and do clean installation using files from Canon website. 
You will need - cnijfilter and - scangear as advised before. Once you install, use GIMP to scan  (File - Create - Scan Gear)
Normally GIMP will fire up required software (in our case canon scangear) and use it. This is the best way!

---

### Post by pdc on 2015-02-18
Hi crazybear; sorry to hear you feel very disappointed in the response on the sane list; 

_______________________

I did have a read at the list; and Rolf; who maintains the latest sane releases did say

> [COLOR="#800080"]Something strange happens in your distro.
[/COLOR]
[COLOR="#FF0000"]Please purge *all* SANE packages in synaptic[/COLOR], [COLOR="#0000FF"]close synaptic[/COLOR] [COLOR="#B22222"]and reinstall SANE in synaptic[/COLOR]. [COLOR="#FF8C00"]Not only remove SANE![/COLOR]

You also should memorise the automatically removed packages for reinstallation, if needed.

If this won't help, you must install SANE's development version from source, as described in README.linux: [http://www.sane-project.org/docs.html](http://www.sane-project.org/docs.html).

Cheers,
Rolf

___________________________________-

So his advice was: Something strange happens in your setup

1) Please **purge** *all* SANE packages in synaptic
2) close synaptic
3) open synaptic; reinstall sane

so did you do that please? If you want guidance on this, please ask; 

I see from the link that Rolf gave [http://www.sane-project.org/lists/sane-backends-cvs.html#S-PIXMA](http://www.sane-project.org/lists/sane-backends-cvs.html#S-PIXMA) ........that they now believe the support for your MX920 series is [COLOR="#008000"]GOOD[/COLOR] 

_________________________________________________________

**[SIZE=4]SCANGEARMP[/SIZE]**     using GIMP is a very good suggestion birkop

> I would suggest to remove everything and do clean installation using files from Canon website. 

........that also is very logical, but crazybear did say earlier > I can scan via command line. That's the good part. .......and that to me means it is working fine; so you could try birkop's excellent suggestion and use GIMP; just run it on our machine and one instantly has GIMP's many edit options

---

### Post by crazybear on 2015-05-07
Sorry I missed notification of the last posts [don't know why, I'm subscribed to thread]...and just happened here by sort of chance. I just tried Gimp and it seemed to work well the little I tried it...with one problem...it seems it can only save in gimp file format - not in any standard formats...any work around there?! I usually need to have it as a jpg or pdf.

---

### Post by pdc on 2015-05-07
> .it seems it can only save in gimp file format 

.....use the EXPORT function ..............go to FILE .....top left............on version 2.8 go down to "EXPORT AS ............." and one can select there from a host of formats ...............

---

