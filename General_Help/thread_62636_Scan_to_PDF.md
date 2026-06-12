---
title: "Scan to PDF"
date: 2005-09-05
forum: General Help
---

### Post by knathraak on 2005-09-05
Hi,

One of the critical applications I have to boot to windows for is my scanner software's ability to scan directly to single or multi page PDF. I'm using an epson perfection 1670.

Is there a utility to do this for Ubuntu or for linux in general? If not, does anyone know of a utility that works well in wine that can do this?

Thanks in advance.

---

### Post by arnieboy on 2005-09-05
[QUOTE=knathraak]Hi,

One of the critical applications I have to boot to windows for is my scanner software's ability to scan directly to single or multi page PDF. I'm using an epson perfection 1670.

Is there a utility to do this for Ubuntu or for linux in general? If not, does anyone know of a utility that works well in wine that can do this?

Thanks in advance.[/QUOTE]
not sure about the scanning as pdf part but u might wanna have a look at this:
[http://support.epson.ru/upload/library_file/11/scanner_linux.pdf](http://support.epson.ru/upload/library_file/11/scanner_linux.pdf)

---

### Post by JeffreyRatcliffe on 2006-07-07
I have a couple of scripts which use sane to scan from my OfficeJet 5510 to tiff and then from tiff to pdf

I can share if anyone is interested...

---

### Post by drtpw on 2006-07-27
I'm a newbie.  Let's get that out of the way.  I'm learning my way around Ubuntu and I love it.  I read the forums, have 2 books (college makes you have to buy books), try stuff, fail, and reinstall.  It's all good.  The promise of leaving the other stuff behind is nice.  I am able to do everything in Ubuntu as well - some things better - than I was able to in XP.  The one thing that I need to do and can not do is scan straight to PDF.  

I know that Xsane 0.99 has the capability but I have been unable to get it to load.  I have read the books, the FAQ and instruction and problem pages within 0.99.  I figured out how to download and install the compilers before 'configure' would work but 'make' has no effect whatsoever.  I have read the scant replies on the forums.  None work.  Most of it I understand and some of it I don't.  I guess I'll have to wait until it is in SPM.  And from what I've read about the convoluted ways that people are going about accomplishing this maneuver, I am not alone by any stretch of the imagination.

Here is a way that works for me without sending my stuff to a website for conversion (that makes me nervous):

Open OpenOffice writer, click on Insert, Picture, Scan, Select Source.  A scanner box opens.  Click on Create Preview.  A message comes up stating "Device does not offer preview, etc.".  Click on OK, the box closes and your document will be scanned.  Click on OK and the scanner box closes.

In OpenOffice writer, again click on Insert, Picture, Scan, and now on Request.  A new box opens and choose "Export Directly to PDF".  Name your file, highlight PDF, and Save.  The only down side is that you have to initially save the PDF to your home directory.  You can move it later.

I hope that this helps some people.  I have gotten much help from what everyone has done and written I this is my first reply to the forums.  Thank you for all your work.

---

### Post by JeffreyRatcliffe on 2006-07-27
I'm in the process of putting a gtk2-perl wrapper on my scripts to make the scan to PDF process easier. I'll post here when I have something working and I'll be looking for alpha testers!

---

### Post by drtpw on 2006-07-27
Jeff,
Look forward to it.  If I get it to work, you'll know that you have a winner on your hands.

---

### Post by pneaveill on 2006-07-30
> **JeffreyRatcliffe said:**
> I have a couple of scripts which use sane to scan from my OfficeJet 5510 to tiff and then from tiff to pdf

I can share if anyone is interested...
Anything for an HP PSC1315?

---

### Post by JeffreyRatcliffe on 2006-07-31
Anything that sane supports ought to be OK. What is the output from ```
scanimage --list-devices
```?

---

### Post by Titus A Duxass on 2006-07-31
I have just used that with my HP PSC1610, worked a treat thanks.
For info, I am running Kubuntu Dapper.

---

### Post by JeffreyRatcliffe on 2006-08-04
OK. Following the open source edict of "Release early, release often", here is version 0.1 of my new utility gscan2pdf.

This is definitely alpha software, written in Perl and GTK+. It's not going to break anything on your system, but there's absolutely no error checking in the File/Import, and at the moment the scan is hard coded to A4. The rest is on its way as soon as I find time.

There's no install script. Just extract the gzipped tar and run "gscan2pdf".

You'll need perl, libgtk2-perl (>=1.100-1), libglib-perl (>= 1.100-1), scanimage & libtiff, which are all available from the standard repositories.

As I said, I have every intention of developing it into a fully-fledged application, so please as much constructive feedback as you like. Here's my immediate todo list:

1. Allow resizing of detail view and proper thumbnails.
2. Scan preferences (# pages, paper size, scanner device, double-sided, etc.)
3. Delete single/multiple pages
4. Add save as tiff
5. Import multi-page tiffs and other formats
6. Rotate
7. Metadata in PDF
8. Reorder pages

I've now registered the project at Sourceforge ([http://sourceforge.net/projects/gscan2pdf](http://sourceforge.net/projects/gscan2pdf))

Have fun!

---

### Post by JeffreyRatcliffe on 2006-08-07
I've added a scan preference window and bumped the version number to 0.2.

---

### Post by pneaveill on 2006-08-07
> **JeffreyRatcliffe said:**
> Anything that sane supports ought to be OK. What is the output from ```
scanimage --list-devices
```?
Sorry it took so long, but here is the info:

device `hpaio:/usb/psc_1310_series?serial=MY41J1D14PO2' is a hp psc_1310_series multi-function peripheral

---

### Post by JeffreyRatcliffe on 2006-08-08
> **pneaveill said:**
> device `hpaio:/usb/psc_1310_series?serial=MY41J1D14PO2' is a hp psc_1310_series multi-function peripheral

That'll do nicely. In the mean time, as you have probably seen from my previous posts, I have released the first versions of my little app, gscan2pdf. Give it a go and tell me what you think!

---

### Post by JeffreyRatcliffe on 2006-08-08
I've added resizing widgets and more scan options. Here's gscan2pdf v0.3.

Comments, please!

---

### Post by pneaveill on 2006-08-08
I downloaded the file and really looking forward to using it. Meanwhile, it could be that I am such a noob with all this that I cannot figure out how to compile it or whatever. Could really use some assistance

---

### Post by JeffreyRatcliffe on 2006-08-09
> **pneaveill said:**
> I downloaded the file and really looking forward to using it. Meanwhile, it could be that I am such a noob with all this that I cannot figure out how to compile it or whatever. Could really use some assistance

No problem. I should perhaps have given more instructions.

1. Make sure that you downloaded gscan2pdf-0.3 from yesterday's post - I added quite a few features.

2. Start open a shell with Applications/Accessories/Terminal.

3. Change directory to wherever you downloaded the file with ```
cd <directory>
```

4. Extract the program with ```
tar xvfz gscan2pdf-0.3.tar.gz
```

5. Run it with ```
gscan2pdf/gscan2pdf
```

I'll put an install script in with the next update to make things easier.

---

### Post by pneaveill on 2006-08-09
Thanks for your patience so far.

> **JeffreyRatcliffe said:**
> No problem. I should perhaps have given more instructions.

1. Make sure that you downloaded gscan2pdf-0.3 from yesterday's post - I added quite a few features.

2. Start open a shell with Applications/Accessories/Terminal.

3. Change directory to wherever you downloaded the file with ```
cd <directory>
``` 
4. Extract the program with ```
tar xvfz gscan2pdf-0.3.tar.gz
``` 
5. Run it with ```
gscan2pdf/gscan2pdf
``` 
I'll put an install script in with the next update to make things easier.
Not sure if I did something wrong, but gave this error:

```
gscan2pdf requires libtiff (tiffcp & tiff2pdf).
Please install them.

```

I think I found them doing a search on synaptic, but not seeing anything in applications. Am I supposed to?

Paul

---

### Post by JeffreyRatcliffe on 2006-08-10
> **pneaveill said:**
> Thanks for your patience so far.


Not sure if I did something wrong, but gave this error:

```
gscan2pdf requires libtiff (tiffcp & tiff2pdf).
Please install them.

```

I think I found them doing a search on synaptic, but not seeing anything in applications. Am I supposed to?

Paul

libtiff is a library of tools for the command line, so you won't see them in applications.

Install libtiff-tools from Synaptic, and then run gscan2pdf again.

---

### Post by pneaveill on 2006-08-11
Not sure if related, but I somehow lost my scanner from the menu
```
 scanimage --list-devices 
``` shows nothing

Any ideas?

---

### Post by pneaveill on 2006-08-11
I took your advice, though I may have missed something. Regadless, I lost all printing/scanning abilities. Tried manual reinstall with fresh drivers from [http://hplip.sourceforge.net/install/step4/setup/local.html](http://hplip.sourceforge.net/install/step4/setup/local.html)

```
 error: No devices found.
error: Error occured during interactive mode. Exiting. 
```

What am I missing?

---

### Post by pneaveill on 2006-08-12
gscan2pdf had to be removed, then did printer reinstall with the HP drivers. I can at least print. Still working on scan.

---

### Post by JeffreyRatcliffe on 2006-08-14
Sorry to be so late to reply - was away for the long weekend.

I'm sorry you are having trouble with your setup.

I can't see how gscan2pdf can have been responsible for losing your scanners, because all it does is call scanimage, tiff2cp and tiff2pdf - and it changes absolutely nothing.

I also wouldn't have installed the sourceforge version of hplip, as it has dependencies which Dapper doesn't support. I looked at this myself a couple of weeks ago in an attempt to sort out some printing issues I had.

Have you ever had the scanner working from Dapper?

---

### Post by pneaveill on 2006-08-14
Printer has worked fine (under breezy, not dapper), cannot remember if scanner ever did under dapper. All it gave me was a bunch of gobble-de-gook all over the screen. Someone in another forum suggested I download the soundforge drivers. And the rest is history.

Not meaning to imply that you were at fault. May have just been the way I did something.

---

### Post by JeffreyRatcliffe on 2006-08-15
The website suggests that scanning from the PSC 1310 is supported.

If ```
scanimage --list-devices
``` isn't giving you anything, then the scanner isn't being found. If you can still print, however, then there is something strange going on.

I used to have similar problem when I had Mandrake 10.1. Cycling the power of the scanner would help. Then ```
scanimage --test
``` with nothing in the scanner confirmed that everything was in order.

If ```
scanimage --list-devices
``` finds the scanner, then use gscan2pdf or xsane to do the scanning.

---

### Post by pneaveill on 2006-08-15
printer works fine, but scanner does not from xsane. Have not attempted to reload your program yet. Meanwhile, the other day you mentioned not loading the soundforge drivers. Is there an alternative that I can use?

Any help is appreciated.  Thanks.

---

### Post by JeffreyRatcliffe on 2006-08-15
What does ```
scanimage --list-devices
``` give?

If scanimage doesn't find any scanners, then there is no point in trying gscan2pdf.

Try cycling the power on the scanner (not the computer) and then ```
scanimage --list-devices
``` again.

What error message does xsane give?

---

### Post by pneaveill on 2006-08-15
(1) Cycled the printer/scanner/copier and it did its little test print thing as expected.
(2) Ran scanimage --list-devices and says this --
```

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages). 
```

---

### Post by JeffreyRatcliffe on 2006-08-15
Presumably xsane therefore complains that there are no scanners?

You have the scanner connected directly via USB and not over the network?

---

### Post by pneaveill on 2006-08-15
Never had the scanner networked. Only used locally at this station.

---

### Post by JeffreyRatcliffe on 2006-08-15
A week ago, you said:

> **pneaveill said:**
> Sorry it took so long, but here is the info:

device `hpaio:/usb/psc_1310_series?serial=MY41J1D14PO2' is a hp psc_1310_series multi-function peripheral

What did you change in the mean time?

---

### Post by pneaveill on 2006-08-15
I forgot what the issue was (and where I posted it at), but was only getting garbage when I scanned. This person at the other place, suggested I use the sourceforge drivers, which got me to this point.

---

### Post by JeffreyRatcliffe on 2006-08-15
> **pneaveill said:**
> I forgot what the issue was (and where I posted it at), but was only getting garbage when I scanned. This person at the other place, suggested I use the sourceforge drivers, which got me to this point.

How were you scanning? If you just did ```
scanimage
``` then sane will send the scan to the stdout, which is the terminal, and you will just get garbage. To get a single scan to a file, you have to do something like ```
scanimage > file
```

---

### Post by pneaveill on 2006-08-15
Noob mistake on the xsane part. So, how do I get the beast to be seen by the computer and get it to run properly.

---

### Post by JeffreyRatcliffe on 2006-08-15
Start Synaptic, search for hplip, and mark hpijs, hplip, hplip-data & hplip-ppds for reinstallation.

I hope that will get the original Dapper driver going again, which seemed to have found the scanner.

---

### Post by pneaveill on 2006-08-15
attempted reload and reboot, then ran scanimage --list-devices

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

Do I wipe those drivers and download them from someplace?

---

### Post by pneaveill on 2006-08-15
Wiped the drivers from synaptic and followed the directions from [http://www.linuxprinting.org]("http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_1020").  Reset everything. Ran scanimage --list-devices
device `hpaio:/usb/psc_1310_series_?serial=MY41J1D14PO2' is a hp psc_1310_series_ multi-function peripheral

Did sample scan and scanned pic. Now working on the OCR part of it. 

Help is appreciated.

---

### Post by JeffreyRatcliffe on 2006-08-15
Glad to hear that thing are working. I can't say I have any experience with OCR. Sorry.

---

### Post by pneaveill on 2006-08-15
How does your program work with the OCR part of things exactly?

---

### Post by JeffreyRatcliffe on 2006-08-15
> **pneaveill said:**
> How does your program work with the OCR part of things exactly?

Not in the slightest. It is simply a GUI wrapper for scanimage and tiff2pdf, i.e. to ease the scan-to-PDF process. It does no OCR at all. I do remember seeing a couple of tools, however, that did OCR.

A quick google found kooka as the best first candidate, although I'm sure there are others.

---

### Post by JeffreyRatcliffe on 2006-08-16
Here is gscan2pdf v0.4, a little tool to ease the scan-to-PDF process.

Changes since v0.3 include thumbnails and an edit menu.

Have fun, and please give me some feedback!

---

### Post by pneaveill on 2006-08-16
scanimage --test
scanimage: scanning image of size 638x877 pixels at 24 bits/pixel
scanimage: acquiring RGB frame, 8 bits/sample
scanimage: reading one scanline, 1914 bytes...  PASS
scanimage: reading one byte...          PASS
scanimage: stepped read, 2 bytes...     PASS
scanimage: stepped read, 4 bytes...     PASS
scanimage: stepped read, 8 bytes...     PASS
scanimage: stepped read, 16 bytes...    PASS
scanimage: stepped read, 32 bytes...    PASS
scanimage: stepped read, 64 bytes...    PASS
scanimage: stepped read, 128 bytes...   PASS
scanimage: stepped read, 256 bytes...   PASS
scanimage: stepped read, 512 bytes...   PASS
scanimage: stepped read, 1024 bytes...  PASS
scanimage: stepped read, 2048 bytes...  PASS
scanimage: stepped read, 2047 bytes...  PASS
scanimage: stepped read, 1023 bytes...  PASS
scanimage: stepped read, 511 bytes...   PASS
scanimage: stepped read, 255 bytes...   PASS
scanimage: stepped read, 127 bytes...   PASS
scanimage: stepped read, 63 bytes...    PASS
scanimage: stepped read, 31 bytes...    PASS
scanimage: stepped read, 15 bytes...    PASS
scanimage: stepped read, 7 bytes...     PASS
scanimage: stepped read, 3 bytes...     PASS

---

### Post by JeffreyRatcliffe on 2006-08-21
Following the open source edict of "Release early, release often", here is version 0.5 of my utility gscan2pdf.

It's not going to break anything on your system, but there's absolutely no error checking in the File/Import. The rest is on its way as soon as I find time.

As I said, I have every intention of developing it into a fully-fledged application, so please as much constructive feedback as you like.

Here's my immediate todo list:

1. Add batch/non-batch toggle and deal with non-ADF usage.
2. Multiselect tiffs to import
3. Reorder pages (DND)
4. Add save as tiff
5. Import multi-page tiffs
6. Rotate
7. Read options from --help --device-name dev.

Have fun!

Changelog:
Added support for PDF Metadata
Added doublesided scan options

I've worked out the basics of deb packaging, so just download gscan2pdf_0.5.deb.gz, unpack it with ```
gzunzip gscan2pdf_0.5.deb.gz
``` and then ```
sudo dpkg -i gscan2pdf_0.5.deb
```
Please let me know what you think/how you get on

---

### Post by JeffreyRatcliffe on 2006-08-22
Following the open source edict of "Release early, release often", I have uploaded version 0.6 of my utility gscan2pdf to [http://sourceforge.net/projects/gscan2pdf](http://sourceforge.net/projects/gscan2pdf).

I have every intention of developing it into a fully-fledged application, so please as much constructive feedback as you like.

Here's my immediate todo list:

1. Add batch/non-batch toggle and deal with non-ADF usage.
2. Renumber pages
3. Reorder pages (DND)
4. Get documentation up to scratch
5. Translations
6. Rotate
7. Read options from --help --device-name dev.

Have fun!

Changelog:
+ Error checking on import
+ Import multiselect
+ Save as TIFF
+ Import multipage TIFFs

Just download gscan2pdf_0.6.deb.gz, unpack it with ```
gzunzip gscan2pdf_0.6.deb.gz
```

and then ```
sudo dpkg -i gscan2pdf_0.6.deb
```

Please let me know what you think/how you get on

---

### Post by pneaveill on 2006-08-22
Probably just a newbie thing, but I have yet to get this OCR thing working. Sorry I cannot be of more help with it.

---

### Post by moshuptrail on 2006-08-31
Jeffrey -
Just hoping you've been messing with xsane enough to know this, or maybe someone else does;  I've been working with xsane directly and setting the ADF option.  (using HP Officejet V40)
But it keeps scanning pages that appear to be legal size.  That is, it scans the printed page correctly, but adds white space at the bottom.  I've also noticed that it can't seem to recognize the no-more-documents-in-feeder signal.  So once it starts with ADF it just keeps going and going creating all these small, blank pages.  (ctrl-c is the only way to stop it) I realize it's not an appropriate Q for this forum, but since I've been following your progress closely I thought I'd start here.  The work you've been doing is exactly what I need and the LAST thing I need before formatting my windows XP partition!  Thanks for the good work.

---

### Post by JeffreyRatcliffe on 2006-08-31
The ADF stuff is device-specific. I also have an OfficeJet - although a 5510. I don't use xsane because I want PDF output and it doesn't support it. 

However, gscan2pdf uses the commandline tool scanimage. With the OfficeJet 5510 backend, scanimage gives me the option --batch-scan=yes, which guarantees that a "no documents" condition will be returned after the last scanned page, to prevent endless flatbed scans after a batch scan.

After a quick look at xsane, I can't see that option supported, although I notice that you can set the scan area (i.e. DIN A4 port.) with a button in the bottom left hand corner of the preview pane.

HTH

---

### Post by moshuptrail on 2006-08-31
Ahah!  I located the size option on the preview window.  Fixing that solved problem 1.  Thanks.  That was really getting to me.

But I can't seem to locate scanimage.  Got any hints on that?
When I type scanimage, it says:
bash: scanimage: command not found

I tried:
find / -name scanimage -print

no joy.

So I used xsane and manually scanned a doc and saved as tiff.  Then used tiff2pdf and manually converted to pdf.  Results were fantastic.

gscan2pdf reports "scanimage not found"
hmmmm:?:

possibly in sane-utils (not listed in synaptic)

---

### Post by JeffreyRatcliffe on 2006-09-01
I just searched for scanimage in Synaptic and saw that it was one of the files installed by sane-utils. So I've just learned something too, because I hadn't got that listed as a dependency for gscan2pdf.

---

### Post by JeffreyRatcliffe on 2006-09-01
Following the open source edict of "Release early, release often", I have uploaded version 0.6.1 of my utility gscan2pdf to [http://sourceforge.net/projects/gscan2pdf](http://sourceforge.net/projects/gscan2pdf).

I have every intention of developing it into a fully-fledged application, so please as much constructive feedback as you like.

Here's my immediate todo list:

1. Add renumber - menu item from 1..n
2. Add status line at bottom with messages like "filename saved"
3. Add Gnome menu
4. Save PDF/scan settings
5. Reorder pages (DND)
6. Rotate
7. Get documentation up to scratch
8. Tooltips
9. Translations

Have fun!

Changes:
+ Renumber by editing page number
+ Destroy window after pdf write
+ Read options from --help --device-name=<dev>
+ Test mode
+ Hides Custom paper sizes when not needed

Just download gscan2pdf_0.6.1.deb.gz, unpack it with```
gzunzip gscan2pdf_0.6.1.deb.gz
```

and then```
sudo dpkg -i gscan2pdf_0.6.1.deb
```

Please let me know what you think/how you get on

---

### Post by mrbaz on 2006-09-02
.folder.  I'm interested to see how this works out.  I'll try it later today.

---

### Post by stephensheppard on 2006-09-03
Hi Jeffrey,

Any chance you could post the source or alternatively compile a binary for a version that would run on AMD 64? I'd like to give your utility a try but I am running Dapper on a 64bit machine.

Thanks,
Steve

---

### Post by JeffreyRatcliffe on 2006-09-03
> **stephensheppard said:**
> Hi Jeffrey,

Any chance you could post the source or alternatively compile a binary for a version that would run on AMD 64? I'd like to give your utility a try but I am running Dapper on a 64bit machine.

Thanks,
Steve

It is written in GTK-Perl, so the .deb should run as installed on an AMD64, and indeed contains the source.

---

### Post by moshuptrail on 2006-09-03
Jeffrey -
I was testing last night and noticed that when I would select "Letter" as the output format, (gscan2pdf) it would not actually scan when I clicked on scan.  Changing it back to A4 allowed scanning.  When I tried to simulate this by manually starting scanimage from the cmd line, I found that I had to specify the device on the command line if I used "Letter", or it wouldn't scan.

I was reading up on scanimage and tiff2pdf.  Got a few questions/comments:
1. Are you using the --batch option to scan multiple pages, or doing that manually in the script?  Do you use tiffcp to combine multiple tiff files?

2. scanimage seems to allow for device-specific options.  My suggestion is to save those in some kind of config file. xsane has a device file that it saves.  Could you just use that? To keep it simple, just save the options as they need to appear in the cmd line.  Don't worry about clever check boxes yet.

3. Do you set up the SANE_DEFAULT_DEVICE envt variable?  Would doing so make anything simpler?

Moshup Trail

---

### Post by JeffreyRatcliffe on 2006-09-04
> **moshuptrail said:**
> I was testing last night and noticed that when I would select "Letter" as the output format, (gscan2pdf) it would not actually scan when I clicked on scan.  Changing it back to A4 allowed scanning.  When I tried to simulate this by manually starting scanimage from the cmd line, I found that I had to specify the device on the command line if I used "Letter", or it wouldn't scan.

I've just tested this. You are right. The problem was that I had specified Letter size as 216mm and your scanner had a maximum width of 215.9mm. What a difference .1mm makes! I'll release v0.6.2 to [http://sourceforge.net/projects/gscan2pdf](http://sourceforge.net/projects/gscan2pdf), so please download it from there.

> **moshuptrail said:**
> Are you using the --batch option to scan multiple pages, or doing that manually in the script?

Yes. I'm using --batch. That way it is easy easier to control the output filename.

> **moshuptrail said:**
> Do you use tiffcp to combine multiple tiff files?

Yes.

> **moshuptrail said:**
> scanimage seems to allow for device-specific options.  My suggestion is to save those in some kind of config file. xsane has a device file that it saves.  Could you just use that? To keep it simple, just save the options as they need to appear in the cmd line.  Don't worry about clever check boxes yet.

At the moment, gscan2pdf reads the device-specific options from scanimage and displays those I thought would be useful. I was considering an options window where the user could select these himself.

I intend to save some sort of config file in the future for options in general, so that one doesn't have to change resolution, paper size, etc. every time before you scan. Do you mean something over and above this? Perhaps you could file a feature request.

> **moshuptrail said:**
> Do you set up the SANE_DEFAULT_DEVICE envt variable?  Would doing so make anything simpler?

It notes whether the variable is set or not, and that is then also the default device in gscan2pdf, but gscan2pdf does not set the variable.

Thanks for the feedback.

Jeff

---

### Post by Dev_Null on 2006-09-06
gscan2pdf seems to be a very useful program for converting paper to digital documents and I'd like to have it running.
unfortunatly I'm getting this error:
```
Unknown message: scanimage: setting of option --br-y failed (Invalid argument)
```

I'm using a HP PSC 1210. It's listed by scanimage. Scanning with xsane works fine too.

---

### Post by JeffreyRatcliffe on 2006-09-06
> **Dev_Null said:**
> gscan2pdf seems to be a very useful program for converting paper to digital documents and I'd like to have it running.
unfortunatly I'm getting this error:
```
Unknown message: scanimage: setting of option --br-y failed (Invalid argument)
```

I'm using a HP PSC 1210. It's listed by scanimage. Scanning with xsane works fine too.

If you could tell me the version of gscan2pdf you are using and send me the output of ```
scanimage --help
``` to ra28145 at users.sourceforge.net then I'll fix it ASAP.

---

### Post by moshuptrail on 2006-09-07
Hi Jeffrey -

I've been testing and comparing a simple manual bash script with using gscan2pdf.  (I'm no whiz, but I use vi to edit!  I think that makes me a relic)  Here are some new thoughts:

0. Works great now!  0.6.2 rev has a lot good features already.

1. You are correct - All the scan document options, device-specific or otherwise, need to be saved.  Other scan utilities have scan *profiles* with one called *default* where you save your most commonly used preferences.

2. In addition to scan preferences, some save options (author, for example) could be saved as well.

3. The page-range in the save dialog should default to all.

4. The scan document dialog wants to come to the top of everything.  As I write this I have to close it or move it in order to see my browser window. Hmmm. That's annoying.  What other options are there?  Could it be implemented as a toolbar on the scan window?

5. On the save document dialog the only field I will use when doing lots of scans is the file name.  (too time-consuming to fill the others)  Would it make sense to put that right at the top so it's clear the others are optional?  Just a thought.

6. The preview pane only shows the last page scanned when you scan a multi-page document.  At first I thought it was a bug, but then I realized that for a flatbed scanner it makes sense.  Not sure if it's right for a multi-page document.

Great work.  I think you've got the problem licked. Just fine-tuning now.

I've got one more issue I'd like to investigate: In XP, HP has an option that seems to figure out the actual page size.  So when I scan pages that are less than 8.5x11 (like my visa bill) the resulting PDF is not padded with blank space.  I've been playing with the scanimage options and I don't see how to do that.  It's a nit though, but if you come across it...

---

### Post by JeffreyRatcliffe on 2006-09-07
> **moshuptrail said:**
> 1. You are correct - All the scan document options, device-specific or otherwise, need to be saved.  Other scan utilities have scan *profiles* with one called *default* where you save your most commonly used preferences.
I've already implemented this in the next version.

> **moshuptrail said:**
> 2. In addition to scan preferences, some save options (author, for example) could be saved as well.
OK. Done.

> **moshuptrail said:**
> 3. The page-range in the save dialog should default to all.
Now the page range is saved in the config file.

> **moshuptrail said:**
> 4. The scan document dialog wants to come to the top of everything.  As I write this I have to close it or move it in order to see my browser window. Hmmm. That's annoying.  What other options are there?  Could it be implemented as a toolbar on the scan window?
It doesn't have to stay on top. I can make it a normal window like any other. I see also that there is a bug that you can open it several times at once.

I *could* make it part of the thumbnail panel, but I think that would look messy. And maybe making it dockable is doable, but it would require a lot of work, so I'll leave that until later.

> **moshuptrail said:**
> 5. On the save document dialog the only field I will use when doing lots of scans is the file name.  (too time-consuming to fill the others)  Would it make sense to put that right at the top so it's clear the others are optional?
I can put it at the top. It is evidently clear to you that the others are optional. Is it just that you want the filename entry to automatically get the focus? I can do that with it still at the bottom.

> **moshuptrail said:**
> 6. The preview pane only shows the last page scanned when you scan a multi-page document.  At first I thought it was a bug, but then I realized that for a flatbed scanner it makes sense.  Not sure if it's right for a multi-page document.
What do you think is right? Would you like to see all the new scans at once, or just the first one? Personally I think it's OK as it is, but I'm happy to listen to other opinions.

> **moshuptrail said:**
> In XP, HP has an option that seems to figure out the actual page size.  So when I scan pages that are less than 8.5x11 (like my visa bill) the resulting PDF is not padded with blank space.  I've been playing with the scanimage options and I don't see how to do that.  It's a nit though, but if you come across it...
There's no option for that in scanimage that I know of. I could see (later in the development!) that a "crop" option might be possible in gscan2pdf. And then the autocrop that you want. I'll put it on the todo list.

Thanks for the feedback

Jeff

---

### Post by JeffreyRatcliffe on 2006-09-08
Following the open source edict of "Release early, release often", I have uploaded version 0.6.3 of my utility gscan2pdf to [http://sourceforge.net/projects/gscan2pdf](http://sourceforge.net/projects/gscan2pdf).

I have every intention of developing it into a fully-fledged application, so please as much constructive feedback as you like.

Here's my immediate todo list:

1. Add status line at bottom with messages like "filename saved"
2. Add Gnome menu
3. Reorder pages (DND)
4. Rotate
5. Get documentation up to scratch
6. Tooltips
7. Translations
8. Crop/autocrop function

Have fun!

Changes:
Fixed "scanimage: option --br-y: bad option value" bug
Child windows now hidden rather than destroyed to improve speed and prevent multiple instances.
Added # pages to scan to config file
+ Renumber menu item
+ Config save for PDF, scan and window settings
+ Added config file support for window maximize state
Changed order of options in tiff2pdf call for FreeBSD compatibility
Moved test output to external file
+ Now parses paper size from device-dependent options

Just download gscan2pdf-0.6.3.deb and then ```
sudo dpkg -i gscan2pdf-0.6.3.deb
```

Please let me know what you think/how you get on

---

### Post by unconquerable on 2006-09-10
As soon as I get Ubuntu up and running I will try out this script.  I am really excited about this endevor as it was my main reason for sticking with XP.

I am planning on digitizing all my textbooks in one PDF per book, for backup purposes.

---

### Post by unconquerable on 2006-09-10
I have not had a chance yet to use the software but I would like to add my 2 cents based on the discussion here.

I feel that crop function is need especially for people scanning in books or other such thing which would not take up the whole can screen.  This function is imperative to the success of the program.


Thanks for the great job by the way.

---

### Post by unconquerable on 2006-09-12
Used the software today to copy some notes from class.  Looks great!  Definetly add the crop feature.  I also think it could use a feature to control the quality of the scan, and some type of PDF compression.  5 pages of notes = 3.5 megs!

Great work on the project!=D>

---

### Post by JeffreyRatcliffe on 2006-09-12
I'll add the crop feature - not in the next release, but it will come.

gscan2pdf writes the PDF compressed anyway by default. The only way that the PDFs could come out uncompressed is if your version of libtiff doesn't support it. Dapper & Hoary do, but the RHE3 & 4 I use at work don't.

Alternatively, perhaps you are scanning with a very high resolution, or in colour.

As a guide - I tend to use the lineart (on Epson, binary) option which gives black and white (1 bit) in 300dpi. One side of A4 uncompressed is then around 1Mb. The compressed PDF comes in at <100kb.

I tend to scan bank statements, bills, etc. These work well with these options. If people were scanning documents with colour photos, I could understand that rather than the LZW compression I have selected, they might want JPEG. I should add this option to the PDF save window.

As to the quality of the scan, this should be controlled by the resolution. As I said, I use 300dpi. If you don't have this option, then your scanner doesn't support it, or the option has a different name with your SANE backend. In this case, please drop me a line at ra28145 at users.sourceforge.net with the output from ```
scanimage --help
```

---

### Post by moshuptrail on 2006-09-18
Here's another area to work on:  No package I've ever worked with correctly handles two-sided originals properly.  On the first pass, it's easy.  All the odd pages are captured.  On the second pass, it depends what has happened during the first pass - if the page-order was reversed by the scanner, the stack will now start with page 2.  If the page-order was not reversed, the pages will start with the even side of the last page.  I noticed you have an input for # of pages.  That might be a required input when the second side is scanned so you can properly number the pages.  Lastly, the pages need to be collated back together and merged to a single file.  (this is where most packages fail)

I tried using 0.6.3 to scan a two-sided document but I couldn't figure out how to collate and merge the two sides.  It seemed to record the odd pages as a single doc but only showed the first page in the thumbnails.  When I tried to capture the even pages it seemed to get confused about the page numbering.  Then it would say "scanning", but not actually scan.

I like the feature that allows you to select multiple thumbnails in the sidebar and save them as a single document.  That wouldn't be practical for a 20-page document though.

---

### Post by JeffreyRatcliffe on 2006-09-19
> **moshuptrail said:**
> Here's another area to work on:  No package I've ever worked with correctly handles two-sided originals properly.  On the first pass, it's easy.  All the odd pages are captured.  On the second pass, it depends what has happened during the first pass - if the page-order was reversed by the scanner, the stack will now start with page 

It should cope with double-sided OK. If it doesn't, then either there is a bug, or I haven't explained things properly.

Here's how it should work:

Select double sided, facing side and gscan2pdf should scan pages 1, 3, 5, etc.. Then turn the whole ream over, select reverse side and the scanned pages should get numbered ... 6, 4, 2. And they should get correctly sorted in the thumbnail list.

What is happening in your case? Please also check the terminal window for error messages.

v0.7 coming soon with drag and drop reordering!

Jeff

---

### Post by moshuptrail on 2006-09-19
It's almost doing everything right.
It scans pages 1, 3 (2 sheets, double-sided)
Then I flip over the stack, select reverse, and scan.
It scans 4, then shows the box [scanning page 2... [cancel]] and it just sits there.  The scanner completed the last page, and pages 1, 3, 4 are showing in the thumbnails.  The only way to stop it is to click cancel.  That leaves me missing page 2.  (Could it have something to do with attempting to scan page 0 to get the out-of-documents signal?)

Note: If I first scan a 2-page single-sided doc, and then switch to double-sided for the next document, it starts with page 3.

---

### Post by JeffreyRatcliffe on 2006-09-20
> **moshuptrail said:**
> It's almost doing everything right.
It scans pages 1, 3 (2 sheets, double-sided)
Then I flip over the stack, select reverse, and scan.
It scans 4, then shows the box [scanning page 2... [cancel]] and it just sits there.  The scanner completed the last page, and pages 1, 3, 4 are showing in the thumbnails.  The only way to stop it is to click cancel.  That leaves me missing page 2.Are there any error messages in the terminal window from where you started gscan2pdf?
> **moshuptrail said:**
> (Could it have something to do with attempting to scan page 0 to get the out-of-documents signal?)It should see that it should only scan pages 4 and 2 and then stop. i.e. It should recognise from the numbering that there are only 2 pages to scan.
> **moshuptrail said:**
> Note: If I first scan a 2-page single-sided doc, and then switch to double-sided for the next document, it starts with page 3.That is the logic I intended. When you select double-sided, it simply starts with the current highest page number + 1 and continues in 2 page increments.

---

### Post by moshuptrail on 2006-09-20
I was trying to run from a desktop icon.  I had the command line: /usr/bin/gscan2pdf >gscan2pdf.log and it wasn't creating a log file.  So I ran from a terminal and got the following:

> 
Unknown message: scanimage: sane_start: Document feeder out of documents
Unknown message: Scanned page 5. (scanner status = 7)
*** unhandled exception in callback:
***   Failed to load image '/tmp/vYXLDsiMMm/5jxqGlfF1q': Failed to load RGB data  from TIFF file: libpixbuf-tiff: Read error on strip 57; got 5376 bytes, expected 6603 at /usr/bin/gscan2pdf line 1355.
***  ignoring at /usr/bin/gscan2pdf line 335.

hmmmm.  Why is it trying to load RGB data for a lineart scan?  Should be just two colors!

The first two lines come after scanning the facing pages.

---

### Post by JeffreyRatcliffe on 2006-09-21
> **moshuptrail said:**
> I was trying to run from a desktop icon.  I had the command line: /usr/bin/gscan2pdf >gscan2pdf.log and it wasn't creating a log file.  So I ran from a terminal and got the following:

hmmmm.  Why is it trying to load RGB data for a lineart scan?  Should be just two colors!

The first two lines come after scanning the facing pages.

I have also had that error message. I think it is due to scanimage saying that the scan is finished before it has finished writing to the file. I will fix it in the next release.

The error message is produced by the GTK C library and it doesn't know at that point that the image is lineart, hence the RGB comment.

A workaround in the mean time is to cancel the scan when the error occurs, rescan just the last page, and to fix the numbering by editing the page number (click on the page number to edit it).

The out of paper error message you can ignore and I have already fixed in the next release.

Jeff

---

### Post by JeffreyRatcliffe on 2006-09-23
Following the open source edict of "Release early, release often", I have uploaded version 0.7 of my utility gscan2pdf to [http://sourceforge.net/projects/gscan2pdf](http://sourceforge.net/projects/gscan2pdf).

I have every intention of developing it into a fully-fledged application, so please as much constructive feedback as you like.

Here's my immediate todo list:

1. Crop & autocrop
2. Rotate
3. Translations
4. OCR

Have fun!

Changes:
+ Drag and drop page reordering
+ Toolbar buttons
+ Tool tips
+ View menu
+ Some documentation
+ Help viewer
+ Improved window handling
+ PDF compression options
Fixed libpixbuf-tiff Read error
Fixed dialog after unknown scan warning

Just download gscan2pdf-0.7.deb and then```
sudo dpkg -i gscan2pdf-0.7.deb
```
Please let me know what you think/how you get on

---

### Post by David Valentine on 2006-09-30
This is just a quick "thank you" for doing this.  The inability to scan straight from my ADF-scanner to a PDF file was a major liability in my book, but lo and behold, you've made great strides in fixing it.  This largely obviates my need for Acrobat Pro, and brings me one step closer to being Windows-free.  Thanks--you're a great example of why the open source community is amazing.

---

### Post by cpcgm on 2006-10-01
Thanks from my side, too. It's also great that you provide a deb-package. I found two little bugs which you might want to know:

1. The european format DIN A4 (210 x 297) can't be customized, only 210 x 296 works. Would be great if DIN A4 could also be selected like US-Letter.

2. Clicking on "Help" results in "The help viewer requires module Gtk2::Ex::PodViewer". Could you include that in the dependencies?

---

### Post by JeffreyRatcliffe on 2006-10-01
> **David Valentine said:**
> This is just a quick "thank you" for doing this.  The inability to scan straight from my ADF-scanner to a PDF file was a major liability in my book, but lo and behold, you've made great strides in fixing it.  This largely obviates my need for Acrobat Pro, and brings me one step closer to being Windows-free.  Thanks--you're a great example of why the open source community is amazing.

You're very welcome! :-)

---

### Post by JeffreyRatcliffe on 2006-10-01
> **cpcgm said:**
> The european format DIN A4 (210 x 297) can't be customized, only 210 x 296 works. Would be great if DIN A4 could also be selected like US-Letter.

There should be 3 paper size options, A4, Letter, and custom. gscan2pdf checks the scannable area, and only gives A4 or Letter if the scanner supports it. The fact that you are not getting the A4 option and that you scan specify a maximum length of 296mm indicates that gscan2pdf thinks that your scanner can only scan 296mm. If you email the output of ```
scanimage --help
``` to ra28145 at users.sourceforge.net, then I'll look into it in more detail.

> **cpcgm said:**
> Clicking on "Help" results in "The help viewer requires module Gtk2::Ex::PodViewer". Could you include that in the dependencies?

Package libgtk2-ex-podviewer-perl IS included, but as "recommends" rather as "depends". I'll make the message a little more detailed in the next release. Alternatively if you type ```
perldoc gscan2pdf
``` at the command line, then you'll get man-style help.

---

### Post by pneaveill on 2006-10-02
> **JeffreyRatcliffe said:**
> There should be 3 paper size options, A4, Letter, and custom. gscan2pdf checks the scannable area, and only gives A4 or Letter if the scanner supports it. The fact that you are not getting the A4 option and that you scan specify a maximum length of 296mm indicates that gscan2pdf thinks that your scanner can only scan 296mm. If you email the output of ```
scanimage --help
``` to ra28145 at users.sourceforge.net, then I'll look into it in more detail.



Package libgtk2-ex-podviewer-perl IS included, but as "recommends" rather as "depends". I'll make the message a little more detailed in the next release. Alternatively if you type ```
perldoc gscan2pdf
``` at the command line, then you'll get man-style help.

Guess I am still not getting this part of things. 
Ignored /usr/bin/gscan2pdf: unreadable
Ignored /usr/bin/gscan2pdf: unreadable
Ignored /usr/bin/X11/gscan2pdf: unreadable
No documentation found for "gscan2pdf".

---

### Post by JeffreyRatcliffe on 2006-10-03
> **pneaveill said:**
> Guess I am still not getting this part of things. 
Ignored /usr/bin/gscan2pdf: unreadable
Ignored /usr/bin/gscan2pdf: unreadable
Ignored /usr/bin/X11/gscan2pdf: unreadable
No documentation found for "gscan2pdf".

I sold you a bit of a dummy there. Try

```
gscan2pdf --help
```

---

### Post by pneaveill on 2006-10-03
Funny how well things work with the right stuff...


Thanks. Will work on it a bit more tomorrow.

---

### Post by JeffreyRatcliffe on 2006-10-04
> **cpcgm said:**
> The european format DIN A4 (210 x 297) can't be customized, only 210 x 296 works.

The reason that A4 is not given as an option is that the scan area that scanimage reports is not large enough:

```
     -x 0..215.9mm [215.9]
         Width of scan-area.
     -y 0..296.926mm [296.926]
         Height of scan-area.
```
A4 is exactly 210x297. 0.08mm too large.

296.926mm is exactly 11.96in. So the reason looks like a stupid bug in the SANE backend.

What are you using? Dapper? It's probably worth reporting it as a bug in Launchpad if not in the SANE project.

---

### Post by JeffreyRatcliffe on 2006-10-05
Following the open source edict of "Release early, release often", I have uploaded version 0.7.2 of my utility gscan2pdf to [http://sourceforge.net/projects/gscan2pdf](http://sourceforge.net/projects/gscan2pdf).

I have every intention of developing it into a fully-fledged application, so please as much constructive feedback as you like.

Here's my immediate todo list:

1. Crop & autocrop
2. Rotate
3. Translations
4. OCR

Have fun!

Changes:
+ button-wait scan option
+ source scan option
Fixed locale problem, forcing LC_NUMERIC=C
Tidied up drag and drop routine

Just download gscan2pdf-0.7.2.deb and then```
sudo dpkg -i gscan2pdf-0.7.2.deb
```

The help will require Gtk2::Ex::PodViewer. Having installed gscan2pdf, locate the gscan2pdf entry in Synaptic, right-click it and you can install PodViewer under "Recommends".

Please let me know what you think/how you get on

---

### Post by DermotMc on 2006-10-05
I installed gscan2pdf, apparently successfully. 
If I start the program the main GUI is displayed correctly, however when I press the scan button I am presented with a small blank box. The terminal is displaying the following:
*** unhandled exception in callback:
***   Modification of non-creatable array value attempted, subscript -1 at /usr/bin/gscan2pdf line 1282.
***  ignoring at /usr/bin/gscan2pdf line 417.

Any ideas? thanks

---

### Post by JeffreyRatcliffe on 2006-10-06
> **DermotMc said:**
> I installed gscan2pdf, apparently successfully. 
If I start the program the main GUI is displayed correctly, however when I press the scan button I am presented with a small blank box. The terminal is displaying the following:
*** unhandled exception in callback:
***   Modification of non-creatable array value attempted, subscript -1 at /usr/bin/gscan2pdf line 1282.
***  ignoring at /usr/bin/gscan2pdf line 417.

Very strange. Which version of gscan2pdf are you using? Please send the output of ```
scanimage --help
``` to ra28145 at users.sourceforge.net.

---

### Post by artisan on 2006-10-06
> **drtpw said:**
>  
Open OpenOffice writer, click on Insert, Picture, Scan, Select Source.  A scanner box opens.  Click on Create Preview.  A message comes up stating "Device does not offer preview, etc.".  Click on OK, the box closes and your document will be scanned.  Click on OK and the scanner box closes.

In OpenOffice writer, again click on Insert, Picture, Scan, and now on Request.  A new box opens and choose "Export Directly to PDF".  Name your file, highlight PDF, and Save.  The only down side is that you have to initially save the PDF to your home directory.  You can move it later.

I hope that this helps some people.  I have gotten much help from what everyone has done and written I this is my first reply to the forums.  Thank you for all your work.

Thank you for posting that it works great for me. Much better than the nothing I had. I now have a fully:)  working Printer/scanner/copier. hp psc 1317

---

### Post by DermotMc on 2006-10-06
I just sent you the requested ouput. I get this error with version 0.7.0. When I upgraded to 0.7.2 the errors remained the same, but the line numbers were offset by 1:
*** unhandled exception in callback:
***   Modification of non-creatable array value attempted, subscript -1 at /usr/bin/gscan2pdf line 1281.

---

### Post by kafkaian on 2006-10-16
Hi, this is exactly what I need. Just installed 7.2 but get the folowing error message on scan

"Unknown message: scanimage: rounded value of resolution from 150 to 150"

The scanner scans but nothing comes up in the gui window

---

### Post by JeffreyRatcliffe on 2006-10-16
> **kafkaian said:**
> Hi, this is exactly what I need. Just installed 7.2 but get the folowing error message on scan

"Unknown message: scanimage: rounded value of resolution from 150 to 150"

The scanner scans but nothing comes up in the gui window

I have a fix for this which I will release as soon as I have a moment (probably tomorrow evening). In the mean time, if you would email the output of ```
scanimage --help
``` to ra28145 at users.sourceforge.net, I'd be grateful.

Jeff

---

### Post by ahsile on 2006-10-16
Thank you for this utility. Saved the day! Just converted from windows a few weeks ago, and had to scan my first assignment in for university. gscan2pdf helped a ton!

Michael

---

### Post by kafkaian on 2006-10-17
As you intend to turn this into a major application Jeff, I think a more formal wish list is appropriate - unless there is one already!

Mine would be to emulate HP PrecisionScan - especially the multiple pdf scan into one document facility.

Incidentally, while I iron out problems with 7.2, I'm using xsane and  tiff2pdf to convert from pdf to tiff. However, on documents I'm getting a very magenta cast on most converted pdf's. Anyone know why this is the case?

---

### Post by JeffreyRatcliffe on 2006-10-17
> **kafkaian said:**
> As you intend to turn this into a major application Jeff, I think a more formal wish list is appropriate - unless there is one already!

Mine would be to emulate HP PrecisionScan - especially the multiple pdf scan into one document facility.

There is a feature request tracker on Sourceforge ([http://sourceforge.net/tracker/?group_id=174140&atid=868101)](http://sourceforge.net/tracker/?group_id=174140&atid=868101)). gscan2pdf will do multi-page PDFs, if that is what you mean. Otherwise, please explain there or here what you would like to see.

Thanks for your --help output. Unfortunately, your scanner has yet another variation of options that I hadn't catered for. I'll fix it and hope to have the new release out tomorrow.

Apologies for the delay

---

### Post by kafkaian on 2006-10-17
> **JeffreyRatcliffe said:**
> There is a feature request tracker on Sourceforge ([http://sourceforge.net/tracker/?group_id=174140&atid=868101)](http://sourceforge.net/tracker/?group_id=174140&atid=868101)). gscan2pdf will do multi-page PDFs, if that is what you mean. Otherwise, please explain there or here what you would like to see.

Thanks for your --help output. Unfortunately, your scanner has yet another variation of options that I hadn't catered for. I'll fix it and hope to have the new release out tomorrow.

Apologies for the delay

Many thanks Jeff and no need to apologise. Just grateful that someone is doing this. At the moment having fun working it all out. Although I have to rush over to Windows when stuck :)

---

### Post by JeffreyRatcliffe on 2006-10-21
Following the open source edict of "Release early, release often", I have uploaded version 0.7.11 of my utility gscan2pdf to [http://sourceforge.net/projects/gscan2pdf](http://sourceforge.net/projects/gscan2pdf). I have now created a depository, so you just have to point Synaptic or apt-get at it. See below for details.

I have every intention of developing it into a fully-fledged application, so please as much constructive feedback as you like.

Here's my immediate todo list:

1. Crop & autocrop
2. Rotate
3. Translations
4. OCR

Have fun!

Changes:
Fixed bug importing from temp
Fixed bug no PDF file created if JPEG compression selected (thanks Thomas for the patch)
+ FAQ
+ more tooltips
+ bug fix niash scanner
+ Right mouse button menus
Wrapped all strings in gettext calls for internationalisation
Now ignores "rounded br-" warnings from scanimage
Update to help to improve html look
Copes with spaces in device-dependent options
Copes with strange characters in device names
+ Uses new FileChooser instead of old FileSelection

Just add the following line to your /etc/apt/sources.list:```
deb http://gscan2pdf.sourceforge.net/download/debian binary/
```

If you are you are using Synaptic, then use menu Edit/Reload Package Information, search for gscan2pdf in the package list, and lo and behold, you can install the nice shiny new version automatically.

From the command line:```
apt-get update
apt-get install gscan2pdf
```

I still haven't got around to putting a Gnome or KDE menu entry in, so you will still have to start it from the command line.

The help will require Gtk2::Ex::PodViewer. Having installed gscan2pdf, locate the gscan2pdf entry in Synaptic, right-click it and you can install PodViewer under "Recommends".

Please let me know what you think/how you get on

---

### Post by MWAAAHAAA on 2006-10-21
Scan to a .ps (postscript) file and convert to .pdf using ps2pdf.

As a scanner front-end for linux I'd suggest using 'xsane'.

---

### Post by moshuptrail on 2006-10-21
For those of you who want a menu entry, it's easy enough to create one using the menu editor:


Applications > Accessories > Alcarte Menu Editor
Select a menu group (Graphics, or whatever you think appropriate for gscan2pdf)
Then click File > New Entry
for Name: Scan to PDF
Comment: whatever
Command: gscan2pdf

Click Close.

That should do it.  I think if you click the box to run in terminal then you'll be able to see any diagnostics in the terminal window.

---

### Post by kafkaian on 2006-10-22
It gets better and better =D> 

Buy the man a beer everyone. (I am...If I can get my paypal account back again)

---

### Post by JeffreyRatcliffe on 2006-10-22
Moshup Trail spotted a nasty little bug where the detail window wasn't displayed after multipage scans (grrrr :(). I've released v0.7.12 to Sourceforge ([http://sourceforge.net/projects/gscan2pdf](http://sourceforge.net/projects/gscan2pdf)) and the repository to fix it. See the previous release for installation details.

---

### Post by JeffreyRatcliffe on 2006-10-28
Following the open source edict of "Release early, release often", I have uploaded version 0.8.0 of my utility gscan2pdf to [http://sourceforge.net/projects/gscan2pdf](http://sourceforge.net/projects/gscan2pdf).

I have every intention of developing it into a fully-fledged application, so please as much constructive feedback as you like.

Here's my immediate todo list:

1. Crop & autocrop
2. OCR

Have fun!

Changes:
+ Rotate options
+ Automatically adds .pdf extension if not already there
Renamed Import menu to Import TIFF
Changed the scan toolbar button from print to print-preview
Made Zip compression default if not in settings
+Fixed lack of shortcut for File menu
+Start of German translation

Just add the following line to your /etc/apt/sources.list:
```
deb http://gscan2pdf.sourceforge.net/download/debian binary/
```

If you are you are using Synaptic, then use menu Edit/Reload Package Information, search for gscan2pdf in the package list, and lo and behold, you can install the nice shiny new version automatically.

From the command line:```
sudo apt-get update
sudo apt-get install gscan2pdf
```

I still haven't got around to putting a Gnome or KDE menu entry in, so you will still have to start it from the command line.

The help will require Gtk2::Ex::PodViewer. Rotating requires Imagemagick. Having installed gscan2pdf, locate the gscan2pdf entry in Synaptic, right-click it and you can install them under "Recommends".

The German translation is about 1/3 done. If anybody fancies translating gscan2pdf into any other languages, they are welcome to do so on Rosetta ([https://launchpad.net/products/gscan2pdf/trunk/+pots/gscan2pdf](https://launchpad.net/products/gscan2pdf/trunk/+pots/gscan2pdf))

Please let me know what you think/how you get on

---

### Post by JeffreyRatcliffe on 2006-10-29
I've just upgraded from Dapper to Edgy and now SANE no longer scans properly from the ADF on my OfficeJet 5510.

With both scanimage and xsane, the first page is fed and scanned properly. Subsequent pages are not fed and the frontend receives blank scans.

No error message is produced.

I assume that this is a bug in hpaio.

Anyone with an HP scanner with an ADF running Edgy - can you confirm this?

I would suggest that anyone with Dapper who uses the ADF on their HP hold off updating until this is fixed.

---

### Post by shekhark on 2006-10-29
Jeffrey, thanks for scratching our collective itch. Discovering this utility on the Forums today has changed my life for the better. For the past year I had assumed that my dependence on Adobe Acrobat would never end, keeping me slave to the Windows box in my office with Acrobat and the scanner with Automatic Document Feeder for making my PDFs. You have shown us a different way. In the old days of shareware, one would send a small gift or contribution, so let us know how we can help out! In the meantime, I am looking forward to OCR suppport. Is it possible to build this in usinghttp://www.gnu.org/software/ocrad/ocrad.html ?

---

### Post by kafkaian on 2006-10-30
> **shekhark said:**
> Jeffrey, thanks for scratching our collective itch. Discovering this utility on the Forums today has changed my life for the better. For the past year I had assumed that my dependence on Adobe Acrobat would never end, keeping me slave to the Windows box in my office with Acrobat and the scanner with Automatic Document Feeder for making my PDFs. You have shown us a different way. In the old days of shareware, one would send a small gift or contribution, so let us know how we can help out! In the meantime, I am looking forward to OCR suppport. Is it possible to build this in usinghttp://www.gnu.org/software/ocrad/ocrad.html ?

This message is almost a mirror image of my experiences and how I feel.

---

### Post by kafkaian on 2006-10-30
I think this project deserves a series of nice icons for the menus etc. At the moment I'm using an image of sputnik 1 :-D 

Jeff, could you or anyone else have a go at this at some stage? It's minor I know, but I think it's such a good piece of software that it requires some branding!

---

### Post by noynac on 2006-10-30
I agree that this is an immensely useful utility. I used to backup documents by scanning them to a PDF file, and I would end up with a large number of individual PDF files. Now I'll have just one.

BTW, I have an Epson 3490 flatbed scanner without an automatic feed. Is there any way to get the scanner's buttons to work with gscan2pdf? For now, I have set the # in gscan2pdf to 1 and scanned this way.

Thanks, 

modred

---

### Post by kafkaian on 2006-10-30
> **noynac said:**
> Is there any way to get the scanner's buttons to work with gscan2pdf?

Yes I would like this too. Got used to pressing the sync button on my HP4300

---

### Post by JeffreyRatcliffe on 2006-11-01
Following the open source edict of "Release early, release often", I have uploaded version 0.8.1 of my utility gscan2pdf to [http://sourceforge.net/projects/gscan2pdf](http://sourceforge.net/projects/gscan2pdf).

I have every intention of developing it into a fully-fledged application, so please as much constructive feedback as you like.

Here's my immediate todo list:

1. Crop & autocrop
2. OCR

Have fun!

Changes:
+ Gnome menu
fixed zoom bug
+ German translation

Just add the following line to your /etc/apt/sources.list:```

deb http://gscan2pdf.sourceforge.net/download/debian binary/
```

If you are you are using Synaptic, then use menu Edit/Reload Package Information, search for gscan2pdf in the package list, and lo and behold, you can install the nice shiny new version automatically.

From the command line:```
sudo apt-get update
sudo apt-get install gscan2pdf
```

The help will require Gtk2::Ex::PodViewer. Rotating requires Imagemagick. Having installed gscan2pdf, locate the gscan2pdf entry in Synaptic, right-click it and you can install them under "Recommends".

If anybody fancies translating gscan2pdf into any other languages, they are welcome to do so on Rosetta ([https://launchpad.net/products/gscan...pots/gscan2pdf](https://launchpad.net/products/gscan...pots/gscan2pdf))

Please let me know what you think/how you get on

---

### Post by JeffreyRatcliffe on 2006-11-01
> **shekhark said:**
> Jeffrey, thanks for scratching our collective itch. Discovering this utility on the Forums today has changed my life for the better. For the past year I had assumed that my dependence on Adobe Acrobat would never end, keeping me slave to the Windows box in my office with Acrobat and the scanner with Automatic Document Feeder for making my PDFs. You have shown us a different way.

Well... I am glad that it is useful.

> **shekhark said:**
> In the old days of shareware, one would send a small gift or contribution, so let us know how we can help out!

If you want to, there is a donate button on the gscan2pdf Sourceforge project page.

> **shekhark said:**
> I am looking forward to OCR suppport. Is it possible to build this in usinghttp://www.gnu.org/software/ocrad/ocrad.html ?

I was sort of leaving that until last, as don't really have a clear plan on how to implement it. I don't know to what extent the metatags in PDF have enough room to, say, use OCR to automate the keyword tag creation. Otherwise, we are just talking about writing a flat text file, aren't we? I'll listen to any good ideas.

---

### Post by JeffreyRatcliffe on 2006-11-01
> **kafkaian said:**
> I think this project deserves a series of nice icons for the menus etc. At the moment I'm using an image of sputnik 1 :-D 

Jeff, could you or anyone else have a go at this at some stage? It's minor I know, but I think it's such a good piece of software that it requires some branding!

The latest version at least creates a Gnome menu (if it doesn't let me know!) with a stock icon. I have near on no talent in icon-drawing, but if someone can come up with something I like, I would be glad to use it.

---

### Post by JeffreyRatcliffe on 2006-11-01
> **noynac said:**
> BTW, I have an Epson 3490 flatbed scanner without an automatic feed. Is there any way to get the scanner's buttons to work with gscan2pdf? For now, I have set the # in gscan2pdf to 1 and scanned this way.

> **kafkaian said:**
> Yes I would like this too. Got used to pressing the sync button on my HP4300

gscan2pdf is just a wrapper for scanimage. Look at the output of ```
scanimage --help
``` If there is an option there to support button operations, then I could implement it.

The wait-for-button and button-wait options are already supported. If you enable these on the scan dialog, then the scanner won't scan the page until you hit the button on the scanner.

The scan dialog only gives those options that are:

[LIST=a]
[*]supported by gscan2pdf - which I can change
[*]given by scanimage --help - which I can't
[/LIST]

---

### Post by noynac on 2006-11-01
Jeffrey,

I ran scanimage --help, and it provided a lot of information, but nothing about scanner buttons. I was going to copy the scanimage --help output into this posting but it's pretty long. Is there something in particular I should be looking for?

Thanks

---

### Post by JeffreyRatcliffe on 2006-11-02
> **noynac said:**
> I ran scanimage --help, and it provided a lot of information, but nothing about scanner buttons. I was going to copy the scanimage --help output into this posting but it's pretty long. Is there something in particular I should be looking for?

If you send the --help output to ra28145 at users.sf.net, then I'll take a look. As an example, I implemented a feature request from somebody a while ago to support the following option from his Epson scanner:

```
    --wait-for-button[=(yes|no)] [no]
        After sending the scan command, wait until the button on the scanner
        is pressed to actually start the scan process.
```

---

### Post by noynac on 2006-11-02
Thanks Jeffrey. I sent you an email with the output.

---

### Post by JeffreyRatcliffe on 2006-11-02
> **noynac said:**
> Thanks Jeffrey. I sent you an email with the output.

Thanks. I can't see any way of accessing the buttons from scanimage, but more importantly, the format of the --help for the scanner geometry means that gscan2pdf is not parsing the scanner size, and therefore does not offer you any paper sizes, so at the moment, it is defaulting to maximum.

I'll fix it in the next release.

---

### Post by noynac on 2006-11-02
Jeffrey,

I scanned two pages of a document using Scan to PDF, and then saved the two pages as one PDF file. When I opened the PDF file in Evince I could see both pages. However, when I printed the first page only about a third of it would print. I print other PDF documents without a similar problem. 

Could this be related to the problem you detected from my --help output?

Thanks!

---

### Post by JeffreyRatcliffe on 2006-11-03
> **noynac said:**
> I scanned two pages of a document using Scan to PDF, and then saved the two pages as one PDF file. When I opened the PDF file in Evince I could see both pages. However, when I printed the first page only about a third of it would print. I print other PDF documents without a similar problem. 

Could this be related to the problem you detected from my --help output?

It depends what size Evince thinks the PDFs are. If they are a standard size, then I doubt it. If the whole of the flatbed was scanned, rather than an A4 or letter-sized area, then they might be a non-standard size, which could confuse the printer. But the fact that Evince displayed them meant they were good PDFs.

---

### Post by JeffreyRatcliffe on 2006-11-10
Following the open source edict of "Release early, release often", I have uploaded version 0.8.2 of my utility gscan2pdf to [http://sourceforge.net/projects/gscan2pdf](http://sourceforge.net/projects/gscan2pdf).

I have every intention of developing it into a fully-fledged application, so please as much constructive feedback as you like.

Here's my immediate todo list:

1. Crop & autocrop
2. OCR

Have fun!

Changes:
+ Partial Swedish translation (thanks to Daniel Nylander)
+ Partial French translation (thanks to Nicolas Velin)
Updates to German translation (thanks to joeb)
Fixed bug in arguments passed to scanimage in non-English locale
+ liblocale-gettext-perl (>= 1.05) dependency in .deb
+ Support for epson_3490 and canoscan_FB_630P scanners


Just add the following line to your /etc/apt/sources.list:```
deb http://gscan2pdf.sourceforge.net/download/debian binary/
```

If you are you are using Synaptic, then use menu Edit/Reload Package Information, search for gscan2pdf in the package list, and lo and behold, you can install the nice shiny new version automatically.

From the command line:```
sudo apt-get update
sudo apt-get install gscan2pdf
```

The help will require Gtk2::Ex::PodViewer. Rotating requires Imagemagick. Having installed gscan2pdf, locate the gscan2pdf entry in Synaptic, right-click it and you can install them under "Recommends".

If anybody fancies translating gscan2pdf into any other languages, they are welcome to do so on Rosetta ([https://launchpad.net/products/gscan...pots/gscan2pdf](https://launchpad.net/products/gscan...pots/gscan2pdf))

Please let me know what you think/how you get on

---

### Post by noynac on 2006-11-10
Thanks Jeffrey! I installed the new version and so far everything seems to work well with my Epson 3490. I have paper-size and other settings, and I have not had a problem printing any pages from the PDF file.

---

### Post by JeffreyRatcliffe on 2006-11-11
> **JeffreyRatcliffe said:**
> I've just upgraded from Dapper to Edgy and now SANE no longer scans properly from the ADF on my OfficeJet 5510.

With both scanimage and xsane, the first page is fed and scanned properly. Subsequent pages are not fed and the frontend receives blank scans.

No error message is produced.

I assume that this is a bug in hpaio.

Anyone with an HP scanner with an ADF running Edgy - can you confirm this?

I would suggest that anyone with Dapper who uses the ADF on their HP hold off updating until this is fixed.

This turned into a bit of a saga. The guys at HPLIP had no idea what the problem might be and initially suggested that I install HPLIP v1.6.10 from source. I rapidly ran into dependency hell and gave up.

The next suggestion was a clean install of Edgy (as I had done a dist-upgrade from Dapper). The install went more smoothly than I expected, but didn't solve the problem.

However, the clean install DID sort out the dependency problem I had earlier. I installed v1.6.10 from source, and now everything is working properly.

---

### Post by David Valentine on 2006-11-20
When I attempt to install gscan2pdf in the manner suggested, apt-get complains that gscan2pdf cannot be found.  If I download the binary and use dpkg, I get the following error:> dpkg: error processing gscan2pdf-0.8.2.deb (--install):
 package architecture (i386) does not match system (amd64)So, does this mean I have to install from source?  If so, how?

Thanks!

---

### Post by shekhark on 2006-11-20
It would be great if one could import individual JPEGs into a PDF with GScan2PDF. I have a number of old batches of flat bed scanned image files which I would like to convert to PDF with the tool.

---

### Post by shekhark on 2006-11-20
Also, does anyone have any recommendation for purchasing an ADF (automatic document feeder) scanner which will work with Dapper and GScan2PDF? I am in the market for one now that this wonderful tool exists and I can turn my Ubuntu box into a digital archiving station. I blogged about my initial joy at discovering GScan2PDF last month on [http://heptanesia.net/2006/10/29/scan-to-pdf/](http://heptanesia.net/2006/10/29/scan-to-pdf/) Thanks again Jeffrey for your excellent contribution!

---

### Post by JeffreyRatcliffe on 2006-11-21
> **David Valentine said:**
> When I attempt to install gscan2pdf in the manner suggested, apt-get complains that gscan2pdf cannot be found.  If I download the binary and use dpkg, I get the following error:So, does this mean I have to install from source?  If so, how?

I have evidently missed some parameter in the .deb that says that it is architecture-independent.

While I try and work out how to sort that out, yes, you will have to use the  source. However, that is not a big deal, as there is no compilation to do. Just download the .tar.gz from sourceforge and extract the archive. There are installation instruction there, but in English, it should work from the command line straight from the extraction.

So, if you have extracted to /home/bob/gscan2pdf-0.8.2/, then ```
cd /home/bob/gscan2pdf-0.8.2/
./gscan2pdf
```

in a terminal window should get you started.

---

### Post by JeffreyRatcliffe on 2006-11-21
> **shekhark said:**
> It would be great if one could import individual JPEGs into a PDF with GScan2PDF. I have a number of old batches of flat bed scanned image files which I would like to convert to PDF with the tool.

I would use the convert utility in imagemagick to batch convert all the jpegs to tiffs, which you can then use with gscan2pdf.

If enough people ask, then I'll look at supporting the import of other file formats like jpg, png, etc., but it is not completely straightforward.

---

### Post by JeffreyRatcliffe on 2006-11-21
> **shekhark said:**
> Also, does anyone have any recommendation for purchasing an ADF (automatic document feeder) scanner which will work with Dapper and GScan2PDF?

HP give official support at HPLIP, so I would suggest that you pick an HP. I have an HP OfficeJet 5510 which worked out of the box with Dapper.

> **shekhark said:**
> I blogged about my initial joy at discovering GScan2PDF last month

Thanks for the good press!

---

### Post by shekhark on 2006-11-21
Jeffrey, thanks for your responses and suggestions! I am dreaming of the day when you will have OCR support and we can make this is a real practical and free alternative to the terrible rule of Acrobat. Let me know how I can buy you a beer. 

Has anyone tried using Dapper + GScan2PDF + HP LaserJet 1220 or 1220se? I had an old LJ1200 which has served me reliably for 4 years, and this seems to be a faster version with an ADF on top, which is what I need. I am anxious that it works for making PDFs. It is supported on [http://hplip.sourceforge.net/supported_devices/mono_laser_mfp.html](http://hplip.sourceforge.net/supported_devices/mono_laser_mfp.html) but if anyone has used this or other suggested HPs, please tell me your experience.

---

### Post by JeffreyRatcliffe on 2006-11-21
> **shekhark said:**
> Let me know how I can buy you a beer.

There is a donate button on the project page: [https://sourceforge.net/projects/gscan2pdf](https://sourceforge.net/projects/gscan2pdf)

---

### Post by David Valentine on 2006-11-21
When I executed ./gscan2pdf, it said that the libtiff library must be installed.  I installed libtiff-tools and libtiff-, which allowed gscan2pdf to start.  When I attempted to scan, it objected with "scanimage not found".

I'm starting to worry that as a noob kubuntu user on an AMD64 system, I may be trying to force a square peg through the proverbial round hole.  I already have libsane installed and I've been able to scan using kooka, but what else do I need to install--sane? xsane? quiteinsane?  

Thanks for the excellent work and support.  I'm excited to get this working!

Update:  As I understand it, gscan2pdf requires sane, libtiff, and gtk2-perl.  I have installed all three of these, and still get the same "scanimage not found" error.  I cannot find a program called "scanimage" in adept, and am wondering if this may be keeping me (and potentially other AMD64 users) away from using gscan2pdf...

---

### Post by moshuptrail on 2006-11-21
You are experiencing the same thing that I found with kubuntu - it's missing  lot of stuff.  You need scanimage too.  (but you knew that)

I think scanimage is in hplip (for hp scanners).  I'm not sure where you get it for other scanners.

---

### Post by David Valentine on 2006-11-21
I keep trying to find scanimage.  I already have hplip and hplipdata installed, so scanimage must be elsewhere--but search in adept does not turn it up.   Aargh.  Now I have to reboot to windows to scan a bunch of pages into pdf's...hopefully for the last time.  ](*,)

---

### Post by JeffreyRatcliffe on 2006-11-22
> **David Valentine said:**
> what else do I need to install--sane? xsane? quiteinsane?

Update:  As I understand it, gscan2pdf requires sane, libtiff, and gtk2-perl.  I have installed all three of these, and still get the same "scanimage not found" error.  I cannot find a program called "scanimage" in adept, and am wondering if this may be keeping me (and potentially other AMD64 users) away from using gscan2pdf...

gscan2pdf requires scanimage, which is in sane-utils.

I hope that this gets you up and scanning!

---

### Post by JeffreyRatcliffe on 2006-11-23
> **David Valentine said:**
> When I attempt to install gscan2pdf in the manner suggested, apt-get complains that gscan2pdf cannot be found.  If I download the binary and use dpkg, I get the following error:So, does this mean I have to install from source?  If so, how?

Thanks!

I have found the reason for this and will be releasing a new version in the next couple of days, after which I'd appreciate it if you could tell whether I have fixed it for you or not.

---

### Post by shekhark on 2006-11-23
Rummaging around my parents' garage this Thanksgiving, I happened on an old Brother MFC 5100c, which I've got mostly working to print, scan, and copy on Dapper. :D There's even an automatic document feeder, but when I work it with GScan2PDF, I can only scan one page in the batch, after which I get the message "Unknown message: scanimage: sane_start: Invalid argument" and the rest of the pages spool through the ADF without scanning. It may be my own configuration, and the Brother linux tools are good but this is an old model. I cannot also do multi-page scanning in xsane or kooka, so it may be another problem. But can someone advise me on how to get this working with gscan2pdf?

---

### Post by JeffreyRatcliffe on 2006-11-23
> **shekhark said:**
> Rummaging around my parents' garage this Thanksgiving, I happened on an old Brother MFC 5100c, which I've got mostly working to print, scan, and copy on Dapper. :D There's even an automatic document feeder, but when I work it with GScan2PDF, I can only scan one page in the batch, after which I get the message "Unknown message: scanimage: sane_start: Invalid argument" and the rest of the pages spool through the ADF without scanning. It may be my own configuration, and the Brother linux tools are good but this is an old model. I cannot also do multi-page scanning in xsane or kooka, so it may be another problem. But can someone advise me on how to get this working with gscan2pdf?

If you send me the output from ```
scanimage --help
``` I'll take a look. What happens if you try ```
scanimage --batch
```?

---

### Post by shekhark on 2006-11-23
Thanks for your prompt response! scanimage --batch does the same thing as in gscan2pdf. It just scans the first page in the batch and spins the rest through without scanning, giving scanimage: sane_start: Invalid argument. 

Here is my output from scanimage --help. Would appreciate if you could tell me what I may need to tweak to get this working. See the output here:

```


shekhar@nowhereman:~$ scanimage --help
Usage: scanimage [OPTION]...

Start image acquisition on a scanner device and write PNM image data to
standard output.

-d, --device-name=DEVICE   use a given scanner device (e.g. hp:/dev/scanner)
    --format=pnm|tiff      file format of output file
-i, --icc-profile=PROFILE  include this ICC profile into TIFF file
-L, --list-devices         show available scanner devices
-f, --formatted-device-list=FORMAT similar to -L, but the FORMAT of the output
                           can be specified: %d (device name), %v (vendor),
                           %m (model), %t (type), and %i (index number)
-b, --batch[=FORMAT]       working in batch mode, FORMAT is `out%d.pnm' or
                           `out%d.tif' by default depending on --format
    --batch-start=#        page number to start naming files with
    --batch-count=#        how many pages to scan in batch mode
    --batch-increment=#    increase number in filename by an amount of #
    --batch-double         increment page number by two for 2sided originals
                           being scanned in a single sided scanner
    --batch-prompt         ask for pressing a key before scanning a page
    --accept-md5-only      only accept authorization requests using md5
-p, --progress             print progress messages
-n, --dont-scan            only set options, don't actually scan
-T, --test                 test backend thoroughly
-h, --help                 display this help message and exit
-v, --verbose              give even more status messages
-B, --buffer-size          change default input buffersize
-V, --version              print version information
scanimage: rounded value of br-x from 208 to 207.981
scanimage: rounded value of br-y from 297 to 296.973

Options specific to device `brother:bus1;dev2':
  Mode:
    --mode Black & White|Gray[Error Diffusion]|True Gray|24bit Color [24bit Color]
        Select the scan mode
    --resolution 100|150|200|300|400|600|1200|2400|4800|9600dpi [200]
        Sets the resolution of the scanned image.
    --source FlatBed|Automatic Document Feeder [Automatic Document Feeder]
        Selects the scan source (such as a document-feeder).
    --brightness -50..50% (in steps of 1) [inactive]
        Controls the brightness of the acquired image.
    --contrast -50..50% (in steps of 1) [inactive]
        Controls the contrast of the acquired image.
  Geometry:
    -l 0..208mm (in steps of 0.0999908) [0]
        Top-left x position of scan area.
    -t 0..355.6mm (in steps of 0.0999908) [0]
        Top-left y position of scan area.
    -x 0..208mm (in steps of 0.0999908) [207.981]
        Width of scan-area.
    -y 0..355.6mm (in steps of 0.0999908) [296.973]
        Height of scan-area.

Type ``scanimage --help -d DEVICE'' to get list of all options for DEVICE.

List of available devices:
    brother:bus1;dev2


```

---

### Post by JeffreyRatcliffe on 2006-11-24
> **shekhark said:**
> I cannot also do multi-page scanning in xsane or kooka, so it may be another problem. But can someone advise me on how to get this working with gscan2pdf?

That scanimage, xsane and kooka all have the same problem makes it fairly certain that this is a problem with the SANE-backend for the scanner. Perhaps there is a newer version of the backend available?

---

### Post by JeffreyRatcliffe on 2006-11-25
Following the open source edict of "Release early, release often", I have uploaded version 0.8.3 of my utility gscan2pdf to [http://sourceforge.net/projects/gscan2pdf](http://sourceforge.net/projects/gscan2pdf).

I have every intention of developing it into a fully-fledged application, so please as much constructive feedback as you like.

Here's my immediate todo list:

1. Crop & autocrop
2. OCR

Have fun!

Changes:
Stickier right mouse button
+ Dutch translation (thanks to Tikkel)
+ Update to German translation (thanks to Christoph Langner)
+ Update to French translation (thanks to Simon Leblanc)
Rewrote Makefile with MakeMaker
Corrected .deb to all instead of i386 architecture
+ code to allow translation of scanimage commandline options

Just add the following line to your /etc/apt/sources.list:```
deb http://gscan2pdf.sourceforge.net/download/debian binary/

```
If you are you are using Synaptic, then use menu Edit/Reload Package Information, search for gscan2pdf in the package list, and lo and behold, you can install the nice shiny new version automatically.

From the command line:```
sudo apt-get update
sudo apt-get install gscan2pdf
```

The help will require Gtk2::Ex::PodViewer. Rotating requires Imagemagick. Having installed gscan2pdf, locate the gscan2pdf entry in Synaptic, right-click it and you can install them under "Recommends".

If anybody fancies translating gscan2pdf into any other languages, they are welcome to do so on Rosetta ([https://launchpad.net/products/gscan...pots/gscan2pdf](https://launchpad.net/products/gscan...pots/gscan2pdf))

Please let me know what you think/how you get on

---

### Post by noynac on 2006-11-26
Jeffrey,

I upgraded to 0.8.3 and all works well except that the  "paper size" setting no longer sticks from session to session. As a result, I have to reset this from A4 to Letter every time that I use Scan to PDF. I went back to version 0.8.2 and the setting stays at letter.

Thanks

---

### Post by JeffreyRatcliffe on 2006-11-26
> **noynac said:**
> I upgraded to 0.8.3 and all works well except that the  "paper size" setting no longer sticks from session to session. As a result, I have to reset this from A4 to Letter every time that I use Scan to PDF. I went back to version 0.8.2 and the setting stays at letter.

OK. I see that. The bug seems to have been introduced while coding translations for the device-dependent options. I'll get a fix out in the course of the week.

---

### Post by shekhark on 2006-11-27
I'm still stumped on using gscan2pdf with my Brother MFC 5100c's automatic document feeder. My problem is that when I put a pile of papers into the feeder, I can only scan one page in the batch, after which I get the message "Unknown message: scanimage: sane_start: Invalid argument" and the rest of the pages spool through the ADF without scanning. 

I am able to do multi-page scanning in xsane, so this is not a general problem. I am also using the [latest Brother drivers]("http://solutions.brother.com/linux/sol/printer/linux/sane_drivers.html") which work fine for flatbed scanning and printing from Dapper. So I am hopeful that I can get this working with gscan2pdf and appreciate any help. 

Here is the output from scanimage -L and scanimage --batch :

```


shekhar@nowhereman:~$ scanimage -L
device `brother:bus1;dev1' is a Brother MFC-5100C USB scanner

shekhar@nowhereman:~$ scanimage --batch
scanimage: rounded value of br-x from 208 to 207.981
scanimage: rounded value of br-y from 297 to 296.973
Scanning -1 pages, incrementing by 1, numbering from 1
Scanning page 1
Scanned page 1. (scanner status = 5)
Scanning page 2
scanimage: sane_start: Invalid argument
Scanned page 2. (scanner status = 4)


```

---

### Post by JeffreyRatcliffe on 2006-11-27
> **shekhark said:**
> I am able to do multi-page scanning in xsane, so this is not a general problem.

OK. So the problem is apparently not SANE, but scanimage, which gscan2pdf at the moment relies on. Can I ask you to contact the authors of the drivers and give them the scanimage --batch output?

In the meantime, in gscan2pdf, rather than the scan "all" option, try selecting the number of pages (start with 2!). Just a thought.

---

### Post by shekhark on 2006-11-27
> **JeffreyRatcliffe said:**
> OK. So the problem is apparently not SANE, but scanimage, which gscan2pdf at the moment relies on. Can I ask you to contact the authors of the drivers and give them the scanimage --batch output?

In the meantime, in gscan2pdf, rather than the scan "all" option, try selecting the number of pages (start with 2!). Just a thought.

I have contacted the Brother Linux helpdesk with the output of scanimage and await their reply (which I wish was as prompt as yours!). I tried specifying the number of pages, but the same error comes on the second page. :(

---

### Post by David Valentine on 2006-11-27
> I have found the reason for this and will be releasing a new version in the next couple of days, after which I'd appreciate it if you could tell whether I have fixed it for you or not.You have, indeed.  It works great--thanks!  :-D

The only problem I have now is that I cannot zoom at all, even though I have all required and recommended packages installed.  Any ideas?

---

### Post by JeffreyRatcliffe on 2006-11-28
> **David Valentine said:**
> The only problem I have now is that I cannot zoom at all, even though I have all required and recommended packages installed.

Strange. Did you start it from the command line? Can you do so, and tell me whether you receive an error messages, especially when you try and zoom?

---

### Post by David Valentine on 2006-11-28
In response to your request, here is a bit of a diary of how gscan2pdf is working on my system (Kubuntu 6.10 on AMD64 Sempron with an HP 6390c scanner).

1.  The scan dialog box sometimes does and sometimes does not contain the paper size option under "Device-dependent options".  It tends to show up after I've scanned.  Given the default behavior of scanning each page as though it were 14" long, I'd like to be able to specify 279 mm before scanning.  Update:  I restarted X, and the paper size option showed up and worked just fine.  Weird...

2.  If I start gscan2pdf at the command line, I get the following message after each page is scanned:> GdkPixbuf-CRITICAL **: gdk_pixbuf_new: assertion `width > 0' failed at /usr/bin/gscan2pdf line 686.
*** unhandled exception in callback:
***   Can't call method "get_width" on an undefined value at /usr/bin/gscan2pdf line 644.
***  ignoring at /usr/lib/perl5/Gtk2/SimpleList.pm line 186.Otherwise, scanning proceeds without any other problems.

3.  Once the scanning is complete and I want to manipulate the images, I get a different set of errors that vary from the one above only in the last line.  For example, the last line of the error message I get is> ***  ignoring at /usr/bin/gscan2pdf line 561. after selecting one page and
>  ***  ignoring at /usr/bin/gscan2pdf line 1828.after selecting all pages.

4.  Zooming does not work and yields no error messages.

5.  Rotating does work, albeit slowly.

6.  "Clear all pages" does not work.  It gives me a confirmation dialog that I cannot dismiss with "OK"--it simply sits there until I close it or close down gscan2pdf.

Please let me know if you think I've left out some key info or can sleuth something out here on my machine.  I think you're doing the community a great service, and reporting my experience is the least I can do!  :p

---

### Post by JeffreyRatcliffe on 2006-11-29
> **David Valentine said:**
> The scan dialog box sometimes does and sometimes does not contain the paper size option under "Device-dependent options".  It tends to show up after I've scanned.  Given the default behavior of scanning each page as though it were 14" long, I'd like to be able to specify 279 mm before scanning.  Update:  I restarted X, and the paper size option showed up and worked just fine.  Weird...

Very strange. Sounds like a problem with X to me, because the presence of the paper size option depends on the scanimage --help output. i.e. it should only change on changing scanner.

> **David Valentine said:**
> 2.  If I start gscan2pdf at the command line, I get the following message after each page is scanned:Otherwise, scanning proceeds without any other problems.

3.  Once the scanning is complete and I want to manipulate the images, I get a different set of errors that vary from the one above only in the last line.  For example, the last line of the error message I get is after selecting one page and
after selecting all pages.

4.  Zooming does not work and yields no error messages.

6.  "Clear all pages" does not work.  It gives me a confirmation dialog that I cannot dismiss with "OK"--it simply sits there until I close it or close down gscan2pdf.

I've just been able to provoke this by moving the thumbnail/detail window divider as far right as possible, thereby making the detail window basically disappear. I'll fix the code so that the error message disappears and so that something sensible happens to the detail view.

However, it suggests to me that you have somehow managed to move the divider completely to the right. As the zoom function only works on the detail view and not the thumbnail, it therefore seems to you that the zoom buttons do not work.

Indeed, with no detail window, the clear all pages function fails because the detail window doesn't exist to be cleared. I'll fix this too.

If you cannot find the divider to drag it left, delete file ```
~/.gscan2pdf
``` This will put all settings back to default, and you should see the divider again.

---

### Post by David Valentine on 2006-11-29
> I've just been able to provoke this by moving the thumbnail/detail window divider as far right as possible, thereby making the detail window basically disappear. I'll fix the code so that the error message disappears and so that something sensible happens to the detail view.

However, it suggests to me that you have somehow managed to move the divider completely to the right. As the zoom function only works on the detail view and not the thumbnail, it therefore seems to you that the zoom buttons do not work.Hmm...  I don't remember moving anything to the right, but once I deleted ~/.gscan2pdf, I got a whole new window I'd never seen before, which looks much nicer!  Zooming works fine now that I know the detail window exists.  I think I know the reason why this happened.  On occasion, consecutive restarts of gscan2pdf moves the divider substantially to the right.  This afternoon, 3 restarts moved it all the way across my 21" monitor.  Right now, restarts are not doing that.  Anyhow, major kudos to you for sleuthing that one out.

> Sounds like a problem with X to me, because the presence of the paper size option depends on the scanimage --help output. i.e. it should only change on changing scanner.I don't seem to be having any other problems with X or with scanning, and ```
scanimage --help -d hp:libusb:001:002
``` gives the following device specific options (among others)> Geometry:
    -l 0..215.788mm (in steps of 1.52588e-05) [0]
        Top-left x position of scan area.
    -t -0.0846558..0mm (in steps of 1.52588e-05) [0]
        Top-left y position of scan area.
    -x 0..215.788mm (in steps of 1.52588e-05) [215.788]
        Width of scan-area.
    -y 0.0846558..355.47mm (in steps of 1.52588e-05) [355.47]
        Height of scan-area.
    --mirror-horizontal Off|On [Off]
        Mirror image horizontally.
    --mirror-vertical Off|On [Off]
        Mirror image vertically.
which look fine to me.  Is there some way to provoke gscan2pdf into including the paper size button, or invoking gscan2pdf with the correct paper size?

---

### Post by JeffreyRatcliffe on 2006-11-30
> **David Valentine said:**
> I don't seem to be having any other problems with X or with scanning, and ```
scanimage --help -d hp:libusb:001:002
``` gives the following device specific options (among others)which look fine to me.

If you send the complete output to ra28145 at users.sf.net, I'll have a more detailed look and do some testing.

---

### Post by shekhark on 2006-11-30
After having various errors related to scanimage in gscan2pdf, I got a message from Brother's Linux helpdesk telling me to try "scanadf" and not "scanimage" from the command line, which now works perfectly with my Brother MFC 51000c. Is there any possibility of implementing "scanadf" directly in gscan2pdf in addition to "scanimage" so I can get this working with my ADF? I imagine that many other document scanners also rely on scanadf and this might be a good feature to have in gscan2pdf -- as well as OCR, to which I look forward with great excitement!

---

### Post by JeffreyRatcliffe on 2006-12-01
> **shekhark said:**
> After having various errors related to scanimage in gscan2pdf, I got a message from Brother's Linux helpdesk telling me to try "scanadf" and not "scanimage" from the command line, which now works perfectly with my Brother MFC 51000c. Is there any possibility of implementing "scanadf" directly in gscan2pdf in addition to "scanimage" so I can get this working with my ADF? I imagine that many other document scanners also rely on scanadf and this might be a good feature to have in gscan2pdf -- as well as OCR, to which I look forward with great excitement!

This is the first example I have heard where scanadf works and scanimage not. Evidently, there is a bug in scanimage. It would be worth reporting it to the SANE project, comparing scanimage to scanadf.

scanadf doesn't support tiff directly, so the pnm file produced must first be converted. Implementing scanadf in gscan2pdf is also not trivial, as scanimage is pretty fundemental to the program at the moment.

I intend long term either to rewrite gscan2pdf in Python (at the moment it is Perl), and use the SANE Python bindings, or write some Perl bindings for SANE. Either of these would bypass problems with scanimage. Neither, however, is trivial either.

---

### Post by shekhark on 2006-12-01
Thanks for your response. Before I report this to the SANE Project, are we sure this is a bug in scanimage? The Brother Linux helpdesk told me that the --source option of the scanimage command only defines from which paper source ONE page of the scan should be done, and that it cannot set scanning for multiple pages from the automatic document feeder (ADF). Is this a bug, or are scanadf and scanimage meant for different things (feeders and flatbeds respectively)?

---

### Post by JeffreyRatcliffe on 2006-12-01
> **shekhark said:**
> The Brother Linux helpdesk told me that the --source option of the scanimage command only defines from which paper source ONE page of the scan should be done, and that it cannot set scanning for multiple pages from the automatic document feeder (ADF). Is this a bug, or are scanadf and scanimage meant for different things (feeders and flatbeds respectively)?

If you read the scanadf page ([http://www.martoneconsulting.com/sane-scanadf.html)](http://www.martoneconsulting.com/sane-scanadf.html)), it wasn't written by the SANE project, but by a chap who wanted SANE to support the ADF in the fancy scanner he was using. He describes his program as: "scanadf, a modified version of the SANE frontend, scanimage, that incorporates some enhanced features".

scanimage supports ADF perfectly well in my HP OfficeJet 5510. There is even a --source option with the options ADF, flatbed, or auto.

scanadf is a SANE-frontend. The fact that it works with your scanner demonstrates that the Brother SANE-backend works. So, yes, I am saying that this is a bug in scanimage.

---

### Post by moshuptrail on 2006-12-01
What about creating a symbolic link called scanimage that points to scanadf?

---

### Post by JeffreyRatcliffe on 2006-12-02
> **moshuptrail said:**
> What about creating a symbolic link called scanimage that points to scanadf?

Unfortunately, scanadf has different options and output, so it isn't as simple as that. Foremost, scanadf doesn't support tiff. That COULD be got around, and the options are similar, so it wouldn't be impossible. It isn't as hard I first thought, but it isn't trivial.

I'll put it on the todo list.

---

### Post by shekhark on 2006-12-02
I do believe that gscan2pdf is a tool best exploited with the use of an automatic document feeder, and from poking around on the net I see that quite a few popular scanners rely on scanadf in Linux. I hope you can implement scanadf! :)

---

### Post by JeffreyRatcliffe on 2006-12-11
Following the open source edict of "Release early, release often", I have uploaded version 0.8.4 of my utility gscan2pdf to [http://sourceforge.net/projects/gscan2pdf](http://sourceforge.net/projects/gscan2pdf).

I have every intention of developing it into a fully-fledged application, so please as much constructive feedback as you like.

Here's my immediate todo list:

1. Support scanadf frontend
2. Crop & autocrop
3. OCR

Have fun!

Changes:
+ Polish translation (thanks to Wojciech Myrda)
+ Update to French translation (thanks to Nicolas Velin)
+ Support for HP ScanJet 6390c.
+ Fixed bug caused by moving thumbnail/detail window divider so that detail window disappears.
+ Fixed missing translations in scanimage commandline options
+ Set open or save buttons as default on all FileChooserDialogs
+ Added 1mm tolerance to paper size check

Just add the following line to your /etc/apt/sources.list:```
deb http://gscan2pdf.sourceforge.net/download/debian binary/
```
If you are you are using Synaptic, then use menu Edit/Reload Package Information, search for gscan2pdf in the package list, and lo and behold, you can install the nice shiny new version automatically.

From the command line:```
sudo apt-get update
sudo apt-get install gscan2pdf
```

The help will require Gtk2::Ex::PodViewer. Rotating requires Imagemagick. Having installed gscan2pdf, locate the gscan2pdf entry in Synaptic, right-click it and you can install them under "Recommends".

If anybody fancies translating gscan2pdf into any other languages, they are welcome to do so on Rosetta ([https://launchpad.net/products/gscan2pdf/trunk/+pots/gscan2pdf](https://launchpad.net/products/gscan2pdf/trunk/+pots/gscan2pdf))

Please let me know what you think/how you get on

---

### Post by David Valentine on 2006-12-11
Woot!  :-D  The new version (0.8.4) worked flawlessly for me.  The "paper size" feature was enabled and allowed me to select "letter" rather than a hard-to-remember metric equivalent to 8.5"x11".  Thanks!!!

---

### Post by lodp on 2006-12-13
this is AWESOME, many thanks for this magnificent application! will safe me a lot of time, i love the simplicity of it.

i wanted to give back somehow, so i slapped together two suggestions for a new icon (using kde icons), maybe you wanna use one of them:

[IMG]http://img367.imageshack.us/img367/8519/gscan2pdffa9.png[/IMG]

or

[IMG]http://img504.imageshack.us/img504/2943/gscan2pdf2xh8.png[/IMG]

personally, i like the first one. the second one doesn't look so great when scaled down in the taskbar.

also, i thought you may wanna use these icons (taken from kde) for the rotating buttons --  i think they get the point across better than the current ones:

[IMG]http://img390.imageshack.us/img390/686/rotatecwqr2.png[/IMG]

[IMG]http://img390.imageshack.us/img390/3263/rotateccwkd6.png[/IMG]

don't know what you could use for the 180° button, though.

and there's one thing i'd like to point out: when you drag a page up or down in the list, and you want to go further than the current scrollbar position allows you, you can't do it -- the scrollbar doesn't go along. is this something that could be fixed?

will this get into the official ubuntu repositories? it's evidently useful...

---

### Post by shekhark on 2006-12-13
Great to see this new version, looking forward to the scandadf and OCR implementation. Great work Jeffrey! :)

---

### Post by JeffreyRatcliffe on 2006-12-13
> **lodp said:**
> i wanted to give back somehow, so i slapped together two suggestions for a new icon (using kde icons), maybe you wanna use one of them:

I like them a lot! Thanks. I, too, prefer the first and I'll look at using it for the next release.

> **lodp said:**
> also, i thought you may wanna use these icons (taken from kde) for the rotating buttons --  i think they get the point across better than the current ones:

I take your point - I just picked (as with the gscan2pdf icon) the nearest GTK stock icon. It would look a bit strange with those two and the current 180 button.

> **lodp said:**
> and there's one thing i'd like to point out: when you drag a page up or down in the list, and you want to go further than the current scrollbar position allows you, you can't do it -- the scrollbar doesn't go along. is this something that could be fixed?

Probably. I'll have to sit down and figure out how the signal works.

> **lodp said:**
> will this get into the official ubuntu repositories? it's evidently useful...

I got as far as finding out that the Universe repository is controlled by the "Masters of the Universe" (MOTU), but didn't get round to contacting one of them... That was a while ago and at that point the packaging was a bit Heath Robinson to say the least. Now it might stand some chance of conforming to the packaging standards.

---

### Post by lodp on 2006-12-14
> It would look a bit strange with those two and the current 180 button.

how about this one:

[IMG]http://img99.imageshack.us/img99/7109/rotate180up0.png[/IMG]

---

### Post by JeffreyRatcliffe on 2006-12-14
> **lodp said:**
> how about this one:

[IMG]http://img99.imageshack.us/img99/7109/rotate180up0.png[/IMG]

Like it! Thanks!

---

### Post by JeffreyRatcliffe on 2006-12-31
Following the open source edict of "Release early, release often", I have uploaded version 0.8.7 of my utility gscan2pdf to [http://sourceforge.net/projects/gscan2pdf](http://sourceforge.net/projects/gscan2pdf).

I have every intention of developing it into a fully-fledged application, so please as much constructive feedback as you like.

Here's my immediate todo list:

1. Support scanadf frontend
2. Crop & autocrop
3. OCR

Have fun!

Changes:
+ Belarusian translation (thanks to booxter)
+ Chinese (Taiwan) translation (thanks to cwchien)
+ Czech translation (thanks to Petr Jelínek)
+ Russian translation (thanks to Alexandre Prokoudine)
+ Update to Swedish translation (thanks to Daniel Nylander)
- 2 scanimage calls (speedup).
Adds the device to the model name if the same model present more than once.
+ Drag-n-drop now autoscrolls the thumbnail list.
+ Error now thrown if Locale::gettext version < 1.05.
+ New icons for application and rotate buttons (thanks to lodp)

Just add the following line to your /etc/apt/sources.list:```
deb http://gscan2pdf.sourceforge.net/download/debian binary/
```
If you are you are using Synaptic, then use menu Edit/Reload Package Information, search for gscan2pdf in the package list, and lo and behold, you can install the nice shiny new version automatically.

From the command line:```
sudo apt-get update
sudo apt-get install gscan2pdf
```

The help will require Gtk2::Ex::PodViewer. Rotating requires Imagemagick. Having installed gscan2pdf, locate the gscan2pdf entry in Synaptic, right-click it and you can install them under "Recommends".

If anybody fancies translating gscan2pdf into any other languages, they are welcome to do so on Rosetta ([https://launchpad.net/products/gscan2pdf/trunk/+pots/gscan2pdf](https://launchpad.net/products/gscan2pdf/trunk/+pots/gscan2pdf))

Please let me know what you think/how you get on

---

### Post by Whoopie on 2006-12-31
Hi,

first, thanks for you great work. I think, gscan2pdf is a great tool!

What I'd like to suggest: After installing the deb package, I saw that the ownership of all files is the user 1000.
You should change the ownership of the files to root:root.

Best regards,
Whoopie

---

### Post by JeffreyRatcliffe on 2006-12-31
> **Whoopie said:**
> What I'd like to suggest: After installing the deb package, I saw that the ownership of all files is the user 1000.
You should change the ownership of the files to root:root.

You are absolutely right, and I quite thought that the ownership was root:root already. I'll fix this for the next release.

What I don't understand is why someone hasn't spotted this before, as it must have been like that from day one.

Thanks

Jeff

---

### Post by moshuptrail on 2006-12-31
I realize this is perhaps an off-topic post, but there's a lot of scanner folks watching this thread...

I've been using gscan2pdf since Jeffrey started writing it.  It's very cool.  Exactly what is needed.

But I've run into a wall recently, having to do with sane scanner identification.  I hadn't used my scanner in a few weeks, and when I went to use gscan2pdf, I got a box saying "no scanners found". 

All of a sudden, sane-find-scanner is not finding my HP all-in-one usb printer/scanner/fax. (OfficeJet V40) I'm not sure what got upgraded, but it's really gone and I've been struggling with this for a few days.  It seems a lot of poeple using hplip and multi-function printers/scanners have had this problem, but I've not found a solution.  Has anyone reading this thread encountered this?

sane-find-scanner output: (in part)
```
  # No USB scanners found. If you expected something different, make sure that
  # you have loaded a kernel driver for your USB host controller and have setup
  # the USB system correctly. See man sane-usb for details.
```

Of course USB is working, I've got USB keyboard, mouse, and memory stick - all working.
This is really killing me. I had to use Windows (makes sign of cross with his fingers) to scan yesterday!

---

### Post by JeffreyRatcliffe on 2006-12-31
> **moshuptrail said:**
> All of a sudden, sane-find-scanner is not finding my HP all-in-one usb printer/scanner/fax. (OfficeJet V40) I'm not sure what got upgraded, but it's really gone and I've been struggling with this for a few days.  It seems a lot of poeple using hplip and multi-function printers/scanners have had this problem, but I've not found a solution.  Has anyone reading this thread encountered this?

Upgrading Dapper-Edgy did this to me. Edgy has HPLIP 1.6.9. I had to remove that and install v1.6.10 which was the latest at the time. This solved the problem for me.

I find the HP guys who support HPLIP at [https://lists.sourceforge.net/lists/listinfo/hplip-help](https://lists.sourceforge.net/lists/listinfo/hplip-help) generally very useful.

---

### Post by moshuptrail on 2006-12-31
Thanks.  I've upgraded hplip to 1.6.12 with no success.  ](*,) 
There's some stupid little thing it's missing - I'm just sure of it!   I've been trying to figure out what sane does to identify scanners.  I found some "rules" in /etc/udev/rules.d called 45-libsane.rules  that I thought would just need an entry for the V40.  No luck though.

hp-check reports everything okay except it doesn't like my PDF printer. :-k  I don't think that should bother it.

p.s. I've written to the hplip-help list and provided some output.

---

### Post by noynac on 2007-01-02
Jeffrey

Thanks for the new version.

When I scan something using gscan2pdf, I sometimes get a box that states "Unknown message:  [snapscan] Scanner warming up - waiting 31 seconds." I do not get this message when using the XSane software. Is there some way to change or to prevent this message from appearing?

BTW, when I get the warming-up message, I click OK and the scan is completed without problem, and I do not get this message after the scanner has warmed up. My scanner is an Epson Pefection 3490 Photo. 

Thanks

---

### Post by JeffreyRatcliffe on 2007-01-02
> **noynac said:**
> When I scan something using gscan2pdf, I sometimes get a box that states "Unknown message:  [snapscan] Scanner warming up - waiting 31 seconds." I do not get this message when using the XSane software. Is there some way to change or to prevent this message from appearing?

BTW, when I get the warming-up message, I click OK and the scan is completed without problem, and I do not get this message after the scanner has warmed up. My scanner is an Epson Pefection 3490 Photo.

gscan2pdf uses the commandline utility (part of SANE) scanimage to control the scanner. Any message that scanimage returns that it doesn't understand gets posted in a dialog box in case it is important.

Are you saying that with xsane, the scanner never needs to warm up? Or that xsane just gives you no message? Does it actually take 31 seconds?

If you capture this output from scanimage and put it in an email to ra28145 at users.sf.net, then I can do something with it.

Now - in your opinion, how do you want the warming up message handled? Ignored - i.e. no dialog? A "warming up" dialog (that presumably cancels itself)?

Personally, I think it useful to know that the scanner is warming up and therefore why it hasn't started doing anything yet.

---

### Post by noynac on 2007-01-02
Jeffrey,

With XSane, the scanner does take about 30 seconds to warm up when I haven't used it for a while (the same as with gscan2pdf). During this warm-up period, the XSane "scan" button is greyed-out but no message box appears. 

If given a choice, I would prefer that (1) a dialog notifies me that the scanner is warming up and (2) the dialog cancels itself when the warm-up period is complete. So, I agree with you.

I have emailed you the output from scanimage. I have also uploaded a screenshot of the  warming-up dialog to:

[http://home.socal.rr.com/grandcanyon/scanscreen.png](http://home.socal.rr.com/grandcanyon/scanscreen.png)

BTW, this issue is an aesthetic one that fits in the nit-picky category. I have found gscan2pdf to be immensely useful and appreciate the time you spend on it.

noynac

---

### Post by JeffreyRatcliffe on 2007-01-13
Following the open source edict of "Release early, release often", I have uploaded version 0.8.9 of my utility gscan2pdf to [http://sourceforge.net/projects/gscan2pdf](http://sourceforge.net/projects/gscan2pdf).

I have every intention of developing it into a fully-fledged application, so please as much constructive feedback as you like.

Here's my immediate todo list:

1. Crop & autocrop
2. OCR

Have fun!

Changes:
+ Spanish translation (thanks to mecedesjorge)
+ Update to Czech translation (thanks to Petr Jelínek)
+ Support for scanadf frontend
+ Email as PDF
+ Displays warm-up message if backend supports it
+ Now ghosts out the rotate menus and buttons if imagemagick not installed

Just add the following line to your /etc/apt/sources.list:```
deb http://gscan2pdf.sourceforge.net/download/debian binary/
```
If you are you are using Synaptic, then use menu Edit/Reload Package Information, search for gscan2pdf in the package list, and lo and behold, you can install the nice shiny new version automatically.

From the command line:```
sudo apt-get update
sudo apt-get install gscan2pdf
```

The help will require Gtk2::Ex::PodViewer. Rotating requires Imagemagick. The scanadf frontend is in sane. For Email as PDF, you need xdg-utils. Having installed gscan2pdf, locate the gscan2pdf entry in Synaptic, right-click it and you can install them under "Recommends".

If anybody fancies translating gscan2pdf into any other languages, they are welcome to do so on Rosetta ([https://launchpad.net/products/gscan2pdf/trunk/+pots/gscan2pdf](https://launchpad.net/products/gscan2pdf/trunk/+pots/gscan2pdf))

Please let me know what you think/how you get on

---

### Post by noynac on 2007-01-13
Thanks for the upgrade. It works great.

I did a scan and saved it as a PDF file. I then went to the File menu and found that Email as PDF is greyed-out. Is that because I do not have sane (scanadf) or imagemagick installed on the computer? I'm using Thunderbird as my email client, and I have selected Thunderbird as my preferred "Mail Reader" application. I'm using scanimage as the frontend.

---

### Post by JeffreyRatcliffe on 2007-01-13
> **noynac said:**
> I did a scan and saved it as a PDF file. I then went to the File menu and found that Email as PDF is greyed-out. Is that because I do not have sane (scanadf) or imagemagick installed on the computer? I'm using Thunderbird as my email client, and I have selected Thunderbird as my preferred "Mail Reader" application. I'm using scanimage as the frontend.

Whoops. Forgot to mention that you need xdg-email, which is part of xdg-utils for email as PDF.

I'll edit the release message accordingly.

---

### Post by yahoo on 2007-01-15
Jeffrey, thanks for the great gscan2pdf v0.8.9.
I installed it using the source.list edit with no problems.

Finally allows me to multi-page scan with my HP Scanjet 5470C.
Not that XSane wouldn't work, but multi-page was not available.

Trouble is, there is no option to change the paper size to 294 x 210.
My scans all have the tops cropped off!!

I'm not sure if the cause is the default options of the scanner.
Any help appreciated.

Also can't email, same problem as noynac, but currently can't connect to the local Ubuntu archive, so will try again later.

Cheers

---

### Post by JeffreyRatcliffe on 2007-01-15
> **yahoo said:**
> Trouble is, there is no option to change the paper size to 294 x 210.

A4 is 210x297. Is this what you mean? If you sent the output from ```
scanimage --help
``` to ra28145 at users.sf.net, then I'll look at the scanner options. In the meantime, if you change the paper size to custom, then you can see the maximum paper size that your scanner supports.

---

### Post by Whoopie on 2007-01-15
Hi Jeffrey,

could you add xdg-utils to Recommends?

Best regards,
Whoopie

---

### Post by JeffreyRatcliffe on 2007-01-15
> **Whoopie said:**
> could you add xdg-utils to Recommends?

Yes. It'll be in the next release. I realised I had forgotten about an hour after releasing the new version.

---

### Post by JeffreyRatcliffe on 2007-01-19
Following the open source edict of "Release early, release often", I have uploaded version 0.9.0 of my utility gscan2pdf to [http://sourceforge.net/projects/gscan2pdf](http://sourceforge.net/projects/gscan2pdf).

I have every intention of developing it into a fully-fledged application, so please as much constructive feedback as you like.

Here's my immediate todo list:

1. Crop & autocrop
2. unpaper support

Have fun!

Changes:
+ OCR support
+ scanadf frontend now uses own device-dependent options
+ Displays start-up message if optional packages missing

Just add the following line to your /etc/apt/sources.list:```
deb http://gscan2pdf.sourceforge.net/download/debian binary/
```
If you are you are using Synaptic, then use menu Edit/Reload Package Information, search for gscan2pdf in the package list, and lo and behold, you can install the nice shiny new version automatically.

From the command line:```
sudo apt-get update
sudo apt-get install gscan2pdf
```

The help will require Gtk2::Ex::PodViewer. Rotating requires Imagemagick. The scanadf frontend is in sane. For Email as PDF, you need xdg-utils. OCR requires gocr. Having installed gscan2pdf, locate the gscan2pdf entry in Synaptic, right-click it and you can install them under "Recommends".

If anybody fancies translating gscan2pdf into any other languages, they are welcome to do so on Rosetta ([https://launchpad.net/products/gscan2pdf/trunk/+pots/gscan2pdf](https://launchpad.net/products/gscan2pdf/trunk/+pots/gscan2pdf))

Please let me know what you think/how you get on, particularly with the new OCR support. Is this how you want it handled? Improvements to the GUI?

---

### Post by noynac on 2007-01-19
> **JeffreyRatcliffe said:**
> ...Please let me know what you think/how you get on, particularly with the new OCR support. Is this how you want it handled? Improvements to the GUI?

I installed the new version, and all seems to work well. I haven't tried the OCR but will test it in a few days. The one GUI change I would like to see is to have the program remember the application window size from session to session. Thanks for the update.

---

### Post by JeffreyRatcliffe on 2007-01-20
> **noynac said:**
> The one GUI change I would like to see is to have the program remember the application window size from session to session.

This appeared in one of the very first versions, and on my system (Gnome) works well. The only thing that I can think of is that you are running KDE or another window manager that is not respecting the window position and size requests. Strange.

Is this not working properly on anybody else's system?

---

### Post by noynac on 2007-01-20
I'm running stock Edgy with all available updates and no special window managers. As a test, I did the following:

1) Open gscan2pdf.

2) Resize the gscan2pdf application window.

3) Scan and save a document.

3) Exit gscan2pdf.

4) Open gscan2pdf.

When I open gscan2pdf in step 4, the application window is the default size--not the size set in step 2. I repeated the above process 3 or 4 times, and I always get the default window size. Other programs, such as gedit, do remember the application window size from session to session, so I assume that I have not changed a global setting or broken something.

As a point of clarification, when gscan2pdf first loads, the application has two panes. One pane contains a thumbnail; the other shows a larger preview of the highlighted thumbnail. I can slide the vertical divider between the thumbnail and preview panes, and this is remembered from session to session. What is not remembered is the size of the entire application window, which, by default, takes up about 60 percent of the height and width of the screen.

---

### Post by JeffreyRatcliffe on 2007-01-20
> **noynac said:**
> I'm running stock Edgy with all available updates and no special window managers.

Ubuntu, Kubuntu, or Xubuntu, i.e. Gnome, KDE or Xfce?

---

### Post by noynac on 2007-01-20
Sorry! I always (and mistakenly) identify Edgy with Ubuntu and not with Kubuntu or anything else. 

Anyway, I'm running Ubuntu 6.10.

---

### Post by JeffreyRatcliffe on 2007-01-20
> **noynac said:**
> Anyway, I'm running Ubuntu 6.10.

That's exactly what I've got and it works fine here. So... what locale are you using? ```
locale
``` will tell you this. It might be worth quitting gscan2pdf, and seeing if deleting the ~/.gscan2pdf file (where the settings are stored) makes a difference.

---

### Post by noynac on 2007-01-20
The results of the locale command were:

LANG=en_US.UTF-8
LANGUAGE=en
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=

I closed gscan2pdf and deleted the gscan2pdf configuration file. I then opened, resized, and closed gscan2pdf. When I next loaded gscan2pdf, the application window size had returned to the default. To make matters worse, I was unable to scan a document and instead got the message: Unknown message: sh: scanadf: not found. I checked and scanimage was selected under edit>frontend. I do not have sane loaded in this computer, which accounts for the absence of scanadf, but I didn't have it before and gscan2pdf worked fine. 

I restored the old (deleted) gscan2pdf configuation file, and I am once again able to scan documents. I have also found that I can manually edit the gscan2pdf window height and width settings in the configuration file, and the gscan2pdf application window is the size I want it. 

BTW, the new (recreated) gscan2pdf configuration file contains the following:

thumb panel = 580
window_height = 600
window_maximize = 0
device = snapscan:libusb:005:005
startup warning = 
cwd = /home/bob
pages to scan = 1
window_width = 800
window_x = 0
window_y = 0

The old gscan2pdf configuration file contains the following:

source = Flatbed
frontend = scanimage
mode = Lineart
month = 11
x = 215.9
author = 
window_maximize = 0
compression = Zip
y = 279.4
keywords = 
cwd = /home/bob/autosave
window_width = 800
day = 10
window_x = 0
window_y = 0
thumb panel = 210
Paper size = Letter
Page range = all
subject = 
window_height = 600
device = snapscan:libusb:005:005
startup warning = 
pages to scan = 1
resolution = 600
title = 
year = 2006

EDIT: I deleted the old configuration file, created a new configuration file by loading gscan2pdf, pasted frontend = scanimage into the new configuration file, and I can now scan with the new configuration file. Unfortunately, the application window size is still not remembered.

---

### Post by JeffreyRatcliffe on 2007-01-20
> **noynac said:**
> The results of the locale command were:

Thanks for that. I'll do some testing.

> **noynac said:**
> I closed gscan2pdf and deleted the gscan2pdf configuration file. I then opened, resized, and closed gscan2pdf. When I next loaded gscan2pdf, the application window size had returned to the default. To make matters worse, I was unable to scan a document and instead got the message: Unknown message: sh: scanadf: not found. I checked and scanimage was selected under edit>frontend.

That's very strange. I'll see if I can reproduce that.

> **noynac said:**
> I restored the old (deleted) gscan2pdf configuation file, and I am once again able to scan documents. I have also found that I can manually edit the gscan2pdf window height and width settings in the configuration file, and the gscan2pdf application window is the size I want it.

So it seems that it reads the config file OK, but doesn't write it properly on your machine?

---

### Post by noynac on 2007-01-20
> **JeffreyRatcliffe said:**
> ...So it seems that it reads the config file OK, but doesn't write it properly on your machine?

That's right! The program reads all settings contained in the configuration file and writes most settings to the configuration file. However, for some reason, it does not write the window width and height settings to the configuration file.

---

### Post by JeffreyRatcliffe on 2007-01-21
> **noynac said:**
> I closed gscan2pdf and deleted the gscan2pdf configuration file. I then opened, resized, and closed gscan2pdf. When I next loaded gscan2pdf, the application window size had returned to the default. To make matters worse, I was unable to scan a document and instead got the message: Unknown message: sh: scanadf: not found. I checked and scanimage was selected under edit>frontend. I do not have sane loaded in this computer, which accounts for the absence of scanadf, but I didn't have it before and gscan2pdf worked fine.

I've now fixed this nasty little bug, which is worth a new release on its own, but I still don't understand why only some of the settings are getting saved on your machine - on mine it all works fine.

Are the window settings not being remembered properly on anyone else's machine?

---

### Post by noynac on 2007-01-22
It appears that this is a problem that is peculiar to my machine. I'm actually content to manually set the window height and width in the config file, as I only have to do this once. Everything else works great.

---

### Post by David Valentine on 2007-01-22
I'm running Kubuntu 6.10 on an AMD64 machine.  You helped me some time back to get gscan2pdf working well, and it has been until now.  The latest version seems to have regressed on my scanner, an HP ScanJet 63x0C.  Here are my symptoms.

1.  When I start to scan, I no longer get any device-dependent options. 

2.  Scanning double sided no longer works correctly--pages simply continue to be numbered sequentially (1, 2, 3, 4,....23, 24, 25) instead of numbering odd pages (facing), then backfilling with even pages (reverse) (1, 3, 5, 7,...8, 6, 4, 2).

3.  When it finishes with the paper in the ADF, it simply starts scanning the empty flatbed until I unplug the usb cable, resulting in an infinite series of "Unknown message:" errors. "scanadf: sane_start: End of file reached".  The error message continues after killing the scanadf process; it keeps me from doing anything in gscan2pdf, and I can't dismiss the error.

My guess is that this resulted from changing to scanadf as the backend, but in any case the situation is serious enough that I'll need to revert to an older version until these issues can be resolved.

Thanks again for developing and maintaining this great tool--I hope my whining does not damper your enthusiasm.

---

### Post by JeffreyRatcliffe on 2007-01-23
> **David Valentine said:**
> 1.  When I start to scan, I no longer get any device-dependent options.

I hope that this is related to the bug described above. In any case, if you don't get ANY device-dependent options, then things are messed up, and its probably not worth trying to scan. Try changing the frontend with Edit/Frontend, and see if you get them back.

> **David Valentine said:**
> 2.  Scanning double sided no longer works correctly--pages simply continue to be numbered sequentially (1, 2, 3, 4,....23, 24, 25) instead of numbering odd pages (facing), then backfilling with even pages (reverse) (1, 3, 5, 7,...8, 6, 4, 2).

The scanadf frontend doesn't allow you to specify page increments, therefore, I have disabled double-sided scanning with scanadf. In this case, use scanimage, which is still available under Edit/Frontend.

---

### Post by David Valentine on 2007-01-23
I downgraded back to 0.8.9, and got my device-dependent options back.  However, the doesn't-know-when-to-quit-scanning bug (#3 above) was still there.  I re-upgraded to 0.9, and lost the device-dependent options again.  I deleted .gscan2pdf from my home directory, which made no difference.  

It turns out that scanimage was already selected under Edit/Frontend, but the errors were being generated by scanadf--as though setting the option really isn't making any difference to which frontend is being used.

---

### Post by noynac on 2007-01-23
David,

Does the hidden gscan2pdf file, which is located in your home directory, contain the line...

frontend = scanimage

I had a problem similar to yours, and it was solved by inserting the above line.

---

### Post by rkh on 2007-01-23
I have cobbled together a little bash script that scans a set number of documents, converts them to ps and then to pdf. It was based upon a few different scripts I found on the web-sorry I can't give credit- with some changes due to the quirks of my scanner -HP laserjet 3020. I haven't gotten it to work perfectly yet-it screws up page order a bit when you scan in more than 10 pages at a time, but it works good enough for me. 

Anyway, I have attached the script. Don't open it in a folder where there are any pnm, ps or pdf files already-it gets confused. 
It uses  sane, imagemagick, zenity, and pdftk to take input in a nifty gtk window on the name of the final pdf, the resolution, and the number of pages to be scanned.
Keep in mind, I am a lawyer, not a programmer. This has worked for me. I hope someone finds it useful.

---

### Post by JeffreyRatcliffe on 2007-01-23
Following the open source edict of "Release early, release often", I have uploaded version 0.9.1 of my utility gscan2pdf to [http://sourceforge.net/projects/gscan2pdf](http://sourceforge.net/projects/gscan2pdf).

I have every intention of developing it into a fully-fledged application, so please as much constructive feedback as you like.

Here's my immediate todo list:

1. Crop & autocrop
2. unpaper support

Have fun!

Changes:
Fixed bug where frontend not properly selected

Just add the following line to your /etc/apt/sources.list:```
deb http://gscan2pdf.sourceforge.net/download/debian binary/
```
If you are you are using Synaptic, then use menu Edit/Reload Package Information, search for gscan2pdf in the package list, and lo and behold, you can install the nice shiny new version automatically.

From the command line:```
sudo apt-get update
sudo apt-get install gscan2pdf
```

The help will require Gtk2::Ex::PodViewer. Rotating requires Imagemagick. The scanadf frontend is in sane. For Email as PDF, you need xdg-utils. OCR requires gocr. Having installed gscan2pdf, locate the gscan2pdf entry in Synaptic, right-click it and you can install them under "Recommends".

If anybody fancies translating gscan2pdf into any other languages, they are welcome to do so on Rosetta ([https://launchpad.net/products/gscan2pdf/trunk/+pots/gscan2pdf](https://launchpad.net/products/gscan2pdf/trunk/+pots/gscan2pdf))

Please let me know what you think/how you get on, particularly with the new OCR support. Is this how you want it handled? Improvements to the GUI?

---

### Post by JeffreyRatcliffe on 2007-01-23
> **David Valentine said:**
> I downgraded back to 0.8.9, and got my device-dependent options back.  However, the doesn't-know-when-to-quit-scanning bug (#3 above) was still there.  I re-upgraded to 0.9, and lost the device-dependent options again.  I deleted .gscan2pdf from my home directory, which made no difference.  

It turns out that scanimage was already selected under Edit/Frontend, but the errors were being generated by scanadf--as though setting the option really isn't making any difference to which frontend is being used.

I hope that the new release fixes both of these problems.

---

### Post by David Valentine on 2007-01-23
Thanks for the help and new release!  Things are much better.  Everything I tried, including page numbering for double-sided scans, now works pretty much as expected, save two things:

1. Even in 0.9.1, gscan2pdf still wants to keep scanning after the ADF is empty, and the only way to stop it was to quit gscan2pdf.  I noticed that although I had selected "ADF" as "Source" in the device-dependent options, "Source" was still listed as "Normal" within .gscan2pdf.  Given that I also had "# pages" set to "all", I guess it would just scan forever...  Is there some way to interrupt it, short of quitting?  Anyhow, I edited .gscan2pdf by hand to change "Normal" to "ADF", and now all is good.

2. Selecting Edit/Frontend to scanadf causes all device-dependent options to disappear.  Selecting scanimage again does not make them re-appear right away, but subsequently restarting gscan2pdf does.

Speaking of which, what are the tradeoffs of using scanadf vs. scanimage?   In my scorebook, scanimage is a couple of points ahead, given that you can do the double-sided numbering correctly with it.

---

### Post by JeffreyRatcliffe on 2007-01-24
> **David Valentine said:**
> 1. Even in 0.9.1, gscan2pdf still wants to keep scanning after the ADF is empty, and the only way to stop it was to quit gscan2pdf.  I noticed that although I had selected "ADF" as "Source" in the device-dependent options, "Source" was still listed as "Normal" within .gscan2pdf.  Given that I also had "# pages" set to "all", I guess it would just scan forever...  Is there some way to interrupt it, short of quitting?  Anyhow, I edited .gscan2pdf by hand to change "Normal" to "ADF", and now all is good.

What sort of scanner do you have?

> **David Valentine said:**
> 2. Selecting Edit/Frontend to scanadf causes all device-dependent options to disappear.  Selecting scanimage again does not make them re-appear right away, but subsequently restarting gscan2pdf does.

This is going to be tricky to bugfix, as I can't think of a way that I can test it from here - it works OK on my OfficeJet 5510. I'll have a think about it and check the code.

> **David Valentine said:**
> Speaking of which, what are the tradeoffs of using scanadf vs. scanimage?   In my scorebook, scanimage is a couple of points ahead, given that you can do the double-sided numbering correctly with it.

I implemented the scanadf support because someone here requested it as the ADF in his Brother scanner wasn't handled properly by scanimage. That would be the only reason for using one over the other, I think.

---

### Post by David Valentine on 2007-01-24
> What sort of scanner do you have?I have a HP ScanJet 6390C (reported as a HP ScanJet 63x0C) with an ADF.

As for the second problem I listed (needing to restart gscan2pdf as well as change frontends in order to get device-dependent options back), I'd consider it a fairly low priority--mostly a matter of polish.

---

### Post by lodp on 2007-01-28
great to see the application develop! any progress getting it into official repositories (ubuntu, debian?)

by the way -- why don't you use the application icon (scanner + pdf logo) as a button for "scan document" as well? surely would look better than the printer with the lightning..

---

### Post by JeffreyRatcliffe on 2007-01-28
> **lodp said:**
> any progress getting it into official repositories (ubuntu, debian?)

I must admit to have been spending all my development time on coding - the next release will have DjVu and unpaper support, and I have a few ideas on how to embed the OCR output as a note (i.e. hidden, but searchable) in the PDF.

> **lodp said:**
> by the way -- why don't you use the application icon (scanner + pdf logo) as a button for "scan document" as well? surely would look better than the printer with the lightning..

I have been thinking about that, too. You hacked the scanner icon from KDE, didn't you? Could you let me have the scanner and PDF icons seperately? I thought I could use the scanner icon for the scan button, and the PDF one for Save as PDF.

---

### Post by JeffreyRatcliffe on 2007-01-31
Following the open source edict of "Release early, release often", I have uploaded version 0.9.2 of my utility gscan2pdf to [http://sourceforge.net/projects/gscan2pdf](http://sourceforge.net/projects/gscan2pdf).

I have every intention of developing it into a fully-fledged application, so please as much constructive feedback as you like.

Here's my immediate todo list:

1. Crop & autocrop

Have fun!

Changes:
+ Update to Czech translation (thanks to Petr Jelínek)
+ Spanish translation (thanks to mecedesjorge)
+ Passes image depth to imagemagick to ensure rotation produces a valid TIFF
+ DjVu support
Fixed bug where device-dependent options disappear if frontend changed whilst scan dialog hidden.
+ Progress bar whilst updating device-dependent options
+ unpaper support
+ Undo/redo

Just add the following line to your /etc/apt/sources.list:```
deb http://gscan2pdf.sourceforge.net/download/debian binary/
```
If you are you are using Synaptic, then use menu Edit/Reload Package Information, search for gscan2pdf in the package list, and lo and behold, you can install the nice shiny new version automatically.

From the command line:```
sudo apt-get update
sudo apt-get install gscan2pdf
```

The help will require Gtk2::Ex::PodViewer. Rotating requires Imagemagick. The scanadf frontend is in sane. For Email as PDF, you need xdg-utils. OCR requires gocr. Having installed gscan2pdf, locate the gscan2pdf entry in Synaptic, right-click it and you can install them under "Recommends".

If anybody fancies translating gscan2pdf into any other languages, they are welcome to do so on Rosetta ([https://launchpad.net/products/gscan2pdf/trunk/+pots/gscan2pdf](https://launchpad.net/products/gscan2pdf/trunk/+pots/gscan2pdf))

Please let me know what you think/how you get on, particularly with the new OCR & unpaper support. Is this how you want it handled? Improvements to the GUI?

---

### Post by noynac on 2007-01-31
Jeff,

I installed the new version and had a question and comment.

I read through your above posting but it is not clear to me what the unpaper support option does. Did I miss an explanation of this option. I see it under the Tools menu, but it's greyed out.

When  I open the "scan document" dialog, I see the new progress bar. At first I thought this created a lag, but the thought occurred to me that the lag has always been there and the progress bar brought it to my attention. Did the progress bar slow things down?

Thanks for the new release.

---

### Post by JeffreyRatcliffe on 2007-02-01
> **noynac said:**
> I read through your above posting but it is not clear to me what the unpaper support option does. Did I miss an explanation of this option. I see it under the Tools menu, but it's greyed out.

Whilst there is a description in the help (and therefore on the website), perhaps I could have explained a bit more:

> unpaper (see [http://unpaper.berlios.de/](http://unpaper.berlios.de/)) is a utility for cleaning up a scan. At the moment, having selected whether the scan has a single or a double page, and which sides to use for the alignment, the scan will be deskewed (rotated) and centred.

unpaper support was a request a couple of weeks ago, and the utility is potentially very useful, when I've figured out how best to support the rest of its features. You will have to install It via Synaptic, apt-get, aptitude, etc before you can use the option in gscan2pdf.

> **noynac said:**
> When  I open the "scan document" dialog, I see the new progress bar. At first I thought this created a lag, but the thought occurred to me that the lag has always been there and the progress bar brought it to my attention. Did the progress bar slow things down?

Previously, the GUI simply blocked until the scanner returned the options. Blocking is bad design, and the progress bar seemed best option. I've been thinking about using them whilst scanning, importing, saving, etc., too.

---

### Post by kafkaian on 2007-02-02
Sorry if this has been answered already but which repository is xdg-utils in?

My synaptic isn't registering it

---

### Post by JeffreyRatcliffe on 2007-02-02
> **kafkaian said:**
> Sorry if this has been answered already but which repository is xdg-utils in?

According to Launchpad, in Edgy it is in universe, and in Feisty it is in main.

---

### Post by kafkaian on 2007-02-02
> **JeffreyRatcliffe said:**
> According to Launchpad, in Edgy it is in universe, and in Feisty it is in main.

Yes I looked up Launchpad but for Dapper, and since I've had very little trouble with it thought I'd stick with it for the time being. Heard a few horror stories regarding Dapper-Edgy upgrades.

In other words; I'm too edgy for Edgy :guitar: :lolflag: 

How have other people got on with the upgrade?

---

### Post by JeffreyRatcliffe on 2007-02-03
> **kafkaian said:**
> How have other people got on with the upgrade?

For my HP OfficeJet 5510, HPLIP in Edgy is broken. I had to do a clean install, rather than an upgrade, to make sure that I had the dependencies right to install the then latest version of HPLIP.

It also temporarily broke my sound, but I fixed that pretty quickly. On the other hand, it originally took me an *AGE* to get sound working with Dapper. Other than that, everything that worked in Dapper, worked in Edgy for me out of the box.

---

### Post by mrojas73 on 2007-02-04
> **JeffreyRatcliffe said:**
> Following the open source edict of "Release early, release often", I have uploaded version 0.9.1 of my utility gscan2pdf to [http://sourceforge.net/projects/gscan2pdf](http://sourceforge.net/projects/gscan2pdf).

I have every intention of developing it into a fully-fledged application, so please as much constructive feedback as you like.

Here's my immediate todo list:

1. Crop & autocrop
2. unpaper support

Have fun!

Changes:
Fixed bug where frontend not properly selected

Just add the following line to your /etc/apt/sources.list:```
deb http://gscan2pdf.sourceforge.net/download/debian binary/
```
If you are you are using Synaptic, then use menu Edit/Reload Package Information, search for gscan2pdf in the package list, and lo and behold, you can install the nice shiny new version automatically.

From the command line:```
sudo apt-get update
sudo apt-get install gscan2pdf
```

The help will require Gtk2::Ex::PodViewer. Rotating requires Imagemagick. The scanadf frontend is in sane. For Email as PDF, you need xdg-utils. OCR requires gocr. Having installed gscan2pdf, locate the gscan2pdf entry in Synaptic, right-click it and you can install them under "Recommends".

If anybody fancies translating gscan2pdf into any other languages, they are welcome to do so on Rosetta ([https://launchpad.net/products/gscan2pdf/trunk/+pots/gscan2pdf](https://launchpad.net/products/gscan2pdf/trunk/+pots/gscan2pdf))

Please let me know what you think/how you get on, particularly with the new OCR support. Is this how you want it handled? Improvements to the GUI?
Jefrey, congratutations on your work!  Your application si fantastic, I just installed it and it is working great on my edgy system with an HP 6350C scanner.  ADF works great too!

Thank you very much!

---

### Post by David Valentine on 2007-02-05
> congratulations on your work!  Your application is fantasticHear, hear!  Moreover, you've been incredibly responsive to feedback.  Thanks for that, too.

---

### Post by JeffreyRatcliffe on 2007-02-05
> **kafkaian said:**
> Yes I looked up Launchpad but for Dapper, and since I've had very little trouble with it thought I'd stick with it for the time being. Heard a few horror stories regarding Dapper-Edgy upgrades.

On the other hand, xdg-utils is just a bunch of bash scripts. You don't need to upgrade to Edgy just for that. Installing them from source really should be easy.

---

### Post by NaGahl on 2007-02-05
Thank you! Thank you, thank you, thank you thank you. I have been looking for a tool just like this for more than a year. I've been using Kooka, Xsane and ImageMagick CLI tools to scan and covert documents to PDF's for almost a year. It was time consuming and annoying. This does exactly what I needed and does it really well and a hell of a lot faster.

:guitar:

---

### Post by noynac on 2007-02-05
> **JeffreyRatcliffe said:**
> ...unpaper support was a request a couple of weeks ago, and the utility is potentially very useful, when I've figured out how best to support the rest of its features. You will have to install It via Synaptic, apt-get, aptitude, etc before you can use the option in gscan2pdf.

I installed unpaper using Synaptic and did a test scan of a document that was skewed a bit. I then selected Tools > unpaper, which brought up the unpaper dialog. After selecting deskew scan direction options, I clicked OK. The preview of the scanned document in the right pane of gscan2pdf disappeared. I tried to save the document as a PDF but no file was created. I saved it as a TIFF, and a file was created, but it only contained 8 bytes. I also tried different unpaper options, but no seemed to work. Am I doing something wrong?

BTW, I looked at the unpaper site and agree that it is and will be a nice feature when fully implemented. Thanks!

---

### Post by JeffreyRatcliffe on 2007-02-06
> **noynac said:**
> I installed unpaper using Synaptic and did a test scan of a document that was skewed a bit. I then selected Tools > unpaper, which brought up the unpaper dialog. After selecting deskew scan direction options, I clicked OK. The preview of the scanned document in the right pane of gscan2pdf disappeared. I tried to save the document as a PDF but no file was created. I saved it as a TIFF, and a file was created, but it only contained 8 bytes. I also tried different unpaper options, but no seemed to work. Am I doing something wrong?

unpaper takes a few seconds to process the image, during which there is a dialog box displayed that should automatically disappear when unpaper has finished. The cleaned-up image should then also be displayed in the detail window. If you don't like the result, there is the undo button - although there is bug in undo where the thumbnail disappears. This will be fixed in the next release.

Would you mind starting gscan2pdf from the command line and telling me if any errors appear there when you do it again?

---

### Post by STREETURCHINE on 2007-02-06
> **JeffreyRatcliffe said:**
> Here is gscan2pdf v0.4, a little tool to ease the scan-to-PDF process.

Changes since v0.3 include thumbnails and an edit menu.

Have fun, and please give me some feedback!

downloaded and it fired up straight away found my scanner,works like a charm thankyou..

---

### Post by noynac on 2007-02-06
> **JeffreyRatcliffe said:**
> unpaper takes a few seconds to process the image, during which there is a dialog box displayed that should automatically disappear when unpaper has finished.... Would you mind starting gscan2pdf from the command line and telling me if any errors appear there when you do it again?
There is no processing dialog after I click OK in the unpaper dialog. I ran gscan2pdf from the command line and received the following error messages:

bob@dell:~$ gscan2pdf
sh: convert: not found
sh: convert: not found
Warning: Image file '/tmp/npKTBVyoIb/LKI8jbiOWs.tif' contains no data at /usr/bin/gscan2pdf line 870.

*** unhandled exception in callback:
***   `0' is not of type Gtk2::Gdk::Pixbuf at /usr/lib/perl5/Gtk2/SimpleList.pm line 256.
***  ignoring at /usr/bin/gscan2pdf line 635.
bob@dell:~$

---

### Post by JeffreyRatcliffe on 2007-02-06
> **noynac said:**
> There is no processing dialog after I click OK in the unpaper dialog. I ran gscan2pdf from the command line and received the following error messages:

bob@dell:~$ gscan2pdf
sh: convert: not found
sh: convert: not found
Warning: Image file '/tmp/npKTBVyoIb/LKI8jbiOWs.tif' contains no data at /usr/bin/gscan2pdf line 870.

*** unhandled exception in callback:
***   `0' is not of type Gtk2::Gdk::Pixbuf at /usr/lib/perl5/Gtk2/SimpleList.pm line 256.
***  ignoring at /usr/bin/gscan2pdf line 635.
bob@dell:~$

Ah! You don't have imagemagick installed. I'll make sure that unpaper is ghosted unless imagemagick is present.

Install imagemagick and try again!

---

### Post by lodp on 2007-02-07
> **JeffreyRatcliffe said:**
> I have been thinking about that, too. You hacked the scanner icon from KDE, didn't you? Could you let me have the scanner and PDF icons seperately? I thought I could use the scanner icon for the scan button, and the PDF one for Save as PDF.

Sorry for the delay. Here you go: [IMG]http://img398.imageshack.us/img398/7910/scannernk3.png[/IMG] [IMG]http://img523.imageshack.us/img523/9114/pdftk3.png[/IMG]

---

### Post by JeffreyRatcliffe on 2007-02-08
> **lodp said:**
> Sorry for the delay. Here you go: [IMG]http://img398.imageshack.us/img398/7910/scannernk3.png[/IMG] [IMG]http://img523.imageshack.us/img523/9114/pdftk3.png[/IMG]

Perfect. Thanks!

---

### Post by JeffreyRatcliffe on 2007-02-08
Following the open source edict of "Release early, release often", I have uploaded version 0.9.3 of my utility gscan2pdf to [http://sourceforge.net/projects/gscan2pdf](http://sourceforge.net/projects/gscan2pdf).

I have every intention of developing it into a fully-fledged application, so please as much constructive feedback as you like.

Here's my immediate todo list:

1. Crop & autocrop

Have fun!

Changes:
Switched the deprecated Gtk2::SimpleList to Gtk2::Ex::Simple::List.
Fixed bug where thumbnail lost after undo/redo
Deleting pages now selects nearest page
+ unpaper --border-align and --border-margin support
+ compression options for save TIFF
+ unpaper ghosted if imagemagick not present
+ updated scan and PDF icons (thanks to lodp)

Just add the following line to your /etc/apt/sources.list:```
deb http://gscan2pdf.sourceforge.net/download/debian binary/
```
If you are you are using Synaptic, then use menu Edit/Reload Package Information, search for gscan2pdf in the package list, and lo and behold, you can install the nice shiny new version automatically.

From the command line:```
sudo apt-get update
sudo apt-get install gscan2pdf
```

The help will require Gtk2::Ex::PodViewer. Rotating requires Imagemagick. The scanadf frontend is in sane. For Email as PDF, you need xdg-utils. OCR requires gocr. Having installed gscan2pdf, locate the gscan2pdf entry in Synaptic, right-click it and you can install them under "Recommends".

If anybody fancies translating gscan2pdf into any other languages, they are welcome to do so on Rosetta ([https://launchpad.net/products/gscan2pdf/trunk/+pots/gscan2pdf](https://launchpad.net/products/gscan2pdf/trunk/+pots/gscan2pdf))

Please let me know what you think/how you get on, particularly with the new OCR & unpaper support. Is this how you want it handled? Improvements to the GUI?

---

### Post by grg3 on 2007-02-08
Great application! Many Thanks!:) 

I recently set up a linux box to use my Brother MFC-6800 multifunction scanner printer.

XSane works fine, ScanADF works fine, Kooka works, but not with  ADF.

gscan2pdf 0.9.3 works with scanadf but not scanimage

I have a question. How can you change the default save to directory for Save to PDF?

Here is the info on scanimage, in case you can use it:

++++++++++++++++++++++++++++++++++++

Scan All with Black and White resolution = 100 ADF
custom size 208 x 279

Scan 2 pages, first page scans and shows image,

second page scans and then gives error below:





unknown message: scanimage: sane_start: invalid argument

"click close"

Unknown message: Scanned page 2. (scanner status =4)

"click close"

only one page appears


=======================================================================================

> scanimage --help
scanimage: rounded value of br-x from 208 to 207.981
scanimage: rounded value of br-y from 297 to 296.973
Usage: scanimage [OPTION]...

Start image acquisition on a scanner device and write PNM image data to
standard output.

-d, --device-name=DEVICE   use a given scanner device (e.g. hp:/dev/scanner)
    --format=pnm|tiff      file format of output file
-i, --icc-profile=PROFILE  include this ICC profile into TIFF file
-L, --list-devices         show available scanner devices
-f, --formatted-device-list=FORMAT similar to -L, but the FORMAT of the output
                           can be specified: %d (device name), %v (vendor),
                           %m (model), %t (type), and %i (index number)
-b, --batch[=FORMAT]       working in batch mode, FORMAT is `out%d.pnm' or
                           `out%d.tif' by default depending on --format
    --batch-start=#        page number to start naming files with
    --batch-count=#        how many pages to scan in batch mode
    --batch-increment=#    increase number in filename by an amount of #
    --batch-double         increment page number by two for 2sided originals
                           being scanned in a single sided scanner
    --batch-prompt         ask for pressing a key before scanning a page
    --accept-md5-only      only accept authorization requests using md5
-p, --progress             print progress messages
-n, --dont-scan            only set options, don't actually scan
-T, --test                 test backend thoroughly
-h, --help                 display this help message and exit
-v, --verbose              give even more status messages
-B, --buffer-size          change default input buffersize
-V, --version              print version information

Options specific to device `brother:bus1;dev1':
  Mode:
    --mode Black & White|Gray[Error Diffusion]|True Gray|24bit Color|24bit Color[Fast] [24bit Color]
        Select the scan mode
    --resolution 100|150|200|300|400|600|1200|2400|4800|9600dpi [200]
        Sets the resolution of the scanned image.
    --source FlatBed|Automatic Document Feeder [Automatic Document Feeder]
        Selects the scan source (such as a document-feeder).
    --brightness -50..50% (in steps of 1) [inactive]
        Controls the brightness of the acquired image.
    --contrast -50..50% (in steps of 1) [inactive]
        Controls the contrast of the acquired image.
  Geometry:
    -l 0..208mm (in steps of 0.0999908) [0]
        Top-left x position of scan area.
    -t 0..355.6mm (in steps of 0.0999908) [0]
        Top-left y position of scan area.
    -x 0..208mm (in steps of 0.0999908) [207.981]
        Width of scan-area.
    -y 0..355.6mm (in steps of 0.0999908) [296.973]
        Height of scan-area.

Type ``scanimage --help -d DEVICE'' to get list of all options for DEVICE.

List of available devices:
    brother:bus1;dev1

---

### Post by noynac on 2007-02-08
The scan-document dialog often opens over the thumbnail panel. You may recall that in my case the gscan2pdf configuration file was not updating for some reason. Is there a setting in the configuration file that I can manually edit to change the location of the scan-document dialog?

Thanks for the update--works great! I like the new PDF icon, which is easily differentiated from the TIFF icon.

---

### Post by JeffreyRatcliffe on 2007-02-09
> **grg3 said:**
> gscan2pdf 0.9.3 works with scanadf but not scanimage

Yeah. That seems to be a problem with Brother scanners and scanimage. If you can report it to the SANE project, then perhaps they might do something about it. This is also the reason I implemented the scanadf support.

> **grg3 said:**
> I have a question. How can you change the default save to directory for Save to PDF?

It should remember the last directory in which you imported or saved something.

> **noynac said:**
> The scan-document dialog often opens over the thumbnail panel. You may recall that in my case the gscan2pdf configuration file was not updating for some reason. Is there a setting in the configuration file that I can manually edit to change the location of the scan-document dialog?

At the moment, all the dialog window positioning is left to the window manager. But you are right, I often find myself moving the scan dialog to see the thumbnails. I'll look at saving the position.

---

### Post by grg3 on 2007-02-09
> **JeffreyRatcliffe said:**
> Yeah. That seems to be a problem with Brother scanners and scanimage. If you can report it to the SANE project, then perhaps they might do something about it. This is also the reason I implemented the scanadf support.

Funny thing is that XSane works fine! I thought that used scanimage, but maybe I am wrong. gscan2pdf seems to act more like kooka, which fails on the adf part.

The scanadf frontend seems to work just fine for me, with two little issues.

The only paper size presented is custom which I set to 208 x279. Every time you scan it gives an error message that it is rounding the size to 207.974 (click close) and rounding size to 278.974 (click close). Just a little annoying but does not affect outcome!

> **JeffreyRatcliffe said:**
> It should remember the last directory in which you imported or saved something.


I can't seem to get it to save in the directory I want by default. Maybe I saved the first test in this one directory or something but that is always the default.

Most importantly, it passed the rigorous "wife test"!

Thanks so much!:)

---

### Post by JeffreyRatcliffe on 2007-02-09
> **grg3 said:**
> Funny thing is that XSane works fine! I thought that used scanimage, but maybe I am wrong. gscan2pdf seems to act more like kooka, which fails on the adf part.

AFAIK, xsane, scanimage, scanadf and kooka all have their own implementations of the SANE library. Any similarilities in results are therefore coincidence. There aren't any Perl bindings for SANE (although I have been thinking about rewriting gscan2pdf in python to use the python bindings), so I use scanimage and scanadf.

> **grg3 said:**
> The only paper size presented is custom which I set to 208 x279. Every time you scan it gives an error message that it is rounding the size to 207.974 (click close) and rounding size to 278.974 (click close).

That I can fix.

> **grg3 said:**
> I can't seem to get it to save in the directory I want by default. Maybe I saved the first test in this one directory or something but that is always the default.

*Sound of penny dropping*

Those people who were having problems with it not remembering the window size, etc. - were you quitting with the close button in the top right hand corner, or with the quit button/menu? It shouldn't make any difference, but I was just trying a few things out, and the settings only seem to be properly saved if you use the quit button/menu.

I will investigate further in a week's time when I get back from a trip.

> **grg3 said:**
> Most importantly, it passed the rigorous "wife test"!

I haven't even tried to get my wife to use the scanner...

---

### Post by noynac on 2007-02-09
> **JeffreyRatcliffe said:**
> ...Those people who were having problems with it not remembering the window size, etc. - were you quitting with the close button in the top right hand corner, or with the quit button/menu? It shouldn't make any difference, but I was just trying a few things out, and the settings only seem to be properly saved if you use the quit button/menu....
I always exit the program by clicking on the close button in the top right hand corner. As a test, I changed the window size of gscan2pdf, and then exited using the "quit button" on the toolbar. The window size was remembered the next time I loaded the program. I checked the config file, and the new window size was reflected. This is the first time ever that the program has remembered the window size.

---

### Post by JeffreyRatcliffe on 2007-02-09
> **noynac said:**
> I always exit the program by clicking on the close button in the top right hand corner. As a test, I changed the window size of gscan2pdf, and then exited using the "quit button" on the toolbar. The window size was remembered the next time I loaded the program. I checked the config file, and the new window size was reflected. This is the first time ever that the program has remembered the window size.

Well, now I've reproduced the problem, I've fixed it. Will be in the next release.

---

### Post by bmt on 2007-02-09
On Dapper, Synaptic reports a problem with Gtk2::Ex::Simple::List being uninstallable (trying to upgrade from gscan2pdf 0.9.2 to 0.9.3).

A search on the package lists suggests that the library is only available for Edgy and Feisty: is this the end of the line for Dapper users? :(

---

### Post by JeffreyRatcliffe on 2007-02-09
> **bmt said:**
> On Dapper, Synaptic reports a problem with Gtk2::Ex::Simple::List being uninstallable (trying to upgrade from gscan2pdf 0.9.2 to 0.9.3).

A search on the package lists suggests that the library is only available for Edgy and Feisty: is this the end of the line for Dapper users? :(

That is irritating. Before I upgraded to Edgy, it was in Dapper. Damn. The stupid thing that Gtk2::Ex::Simple::List and the deprecated Gtk2::SimpleList can coexist quite happily.

So - the options are

a. Packaging Gtk2::Ex::Simple::List myself or convincing somebody at Ubuntu to do it.
b. Switching back to Gtk2::SimpleList although it is deprecated (and won't exist for ever)

I'll look at (a) before the next release as first choice and (b) if I can't do (a).

---

### Post by grg3 on 2007-02-09
I will remember to close out properly and that will take care of the default directory!

I am using Mepis 6.0 on this machine (dapper) I was able to get Gtk2::Ex::Simple::List from Debian unstable and install latest gscan2pdf without any problems.

Thanks again!

---

### Post by JeffreyRatcliffe on 2007-02-10
> **grg3 said:**
> I am using Mepis 6.0 on this machine (dapper) I was able to get Gtk2::Ex::Simple::List from Debian unstable and install latest gscan2pdf without any problems.

For the next release, I'll put a .deb of Gtk2::Ex::Simple::List on Sourceforge so that people don't have to go digging. Don't have time now...

---

### Post by bmt on 2007-02-10
> **grg3 said:**
> I was able to get Gtk2::Ex::Simple::List from Debian unstable and install latest gscan2pdf without any problems.
Thanks for that -- it works nicely.

The Debian unstable package can be found [here]("http://packages.debian.org/unstable/perl/libgtk2-ex-simple-list-perl"), to save others having to search.  Download and install and then gscan2pdf can be updated as normal.

---

### Post by David Valentine on 2007-02-12
Just FYI, this package is really coming along nicely.  I've been enjoying absolutely painless scanning and unpapering--thanks for this great contribution to the community.  :KS

---

### Post by tcornishmn on 2007-02-20
Thanks for a great program - I discovered it over the weekend and as other users have said, eliminates one of my few remaining needs for Windows.

I have a couple of feature requests:

1.  Make entering the PDF metadata optional - Many times the file name is sufficient, and having to get through the first metadata screen slows things down. It would be great if there was a preferences setting that allowed the metadata screen to be turned off so clicking the save PDF icon would bring me directly to the filename and location dialog.

2.  Implement scanned image with text  - The OCR engine seems to work well - it would be great if there were a way to have that applied to the PDF itself, similar to how Acrobat Capture or OmniPage work.  The image is stored without modification, but there is a hidden text layer on top of that.

3.  To make wishlist item #2 more practical, adjust the workflow so that a file name is selected first, then the pages are acquired, then when the save button is pressed, the job goes to a queue where OCRing happens in the background.  This would allow more jobs to be scanned and saved but OCR'd later.



Again, thanks for such a cool program.  I'm going to try to get this nominated for insertion into one of the Ubuntu repositories.

TJ

---

### Post by noynac on 2007-02-20
> **tcornishmn said:**
> ...I have a couple of feature requests:

1.  Make entering the PDF metadata optional - Many times the file name is sufficient, and having to get through the first metadata screen slows things down. It would be great if there was a preferences setting that allowed the metadata screen to be turned off so clicking the save PDF icon would bring me directly to the filename and location dialog....

I also would like this change, as I never enter any information in the first save screen. It's only one extra click, which is not a big deal, but an option to go either way would be neat.

---

### Post by JeffreyRatcliffe on 2007-02-20
> **tcornishmn said:**
> 1.  Make entering the PDF metadata optional - Many times the file name is sufficient, and having to get through the first metadata screen slows things down. It would be great if there was a preferences setting that allowed the metadata screen to be turned off so clicking the save PDF icon would bring me directly to the filename and location dialog. You'd still need the part of the dialog to select which pages to convert - i.e. all, current or selected. Or do people generally only use the "all" option? Personally, I tend to scan a bunch of not necessarily related things, and use the "selected" option when converting to PDF.

> **tcornishmn said:**
> 2.  Implement scanned image with text  - The OCR engine seems to work well - it would be great if there were a way to have that applied to the PDF itself, similar to how Acrobat Capture or OmniPage work.  The image is stored without modification, but there is a hidden text layer on top of that. Absolutely. If there had been a straightforward way of doing this, it would already be there. I do intend to implement this, but it is going to require a bit of rewrite and some thought.

> **tcornishmn said:**
> 3.  To make wishlist item #2 more practical, adjust the workflow so that a file name is selected first, then the pages are acquired, then when the save button is pressed, the job goes to a queue where OCRing happens in the background.  This would allow more jobs to be scanned and saved but OCR'd later. Or the OCR happens automatically during the aquisition phase. But I agree with the general idea that the workflow would need to be optimised.

> **tcornishmn said:**
> I'm going to try to get this nominated for insertion into one of the Ubuntu repositories. Please do. I haven't got around to it up to now.

---

### Post by tcornishmn on 2007-02-20
I generally just use "all" pages - I guess I can see the utility in some situations for wanting to just save a subsection, though too.  How about a second save button?  One for Save All, a second for Save Selection?



As far as OCR during the acquisition phase - my main concern is that I don't want to wait for my computer to perform the OCR before letting me continue on to the next scan job.  The software I use at work, Adobe Acrobat capture lets me name and scan as many jobs as I want, and they get OCR'd and put together in the background.  After I scan in my jobs, I can walk away from the machine and come back later and the jobs are done.  

Thanks again for your work.

TJ

---

### Post by JeffreyRatcliffe on 2007-02-21
> **tcornishmn said:**
> I generally just use "all" pages - I guess I can see the utility in some situations for wanting to just save a subsection, though too.  How about a second save button?  One for Save All, a second for Save Selection?

Except that the first becomes a "Save all as PDF without metadata" button and the second is the standard "Save as PDF". This seems a little clumsy.

---

### Post by tcornishmn on 2007-02-21
I agree, but maybe a solution would be that the metadata/no metadata selection would be in the preferences menu, therefore the save all/save selection buttons would both work whichever way the preference was set.

---

### Post by JeffreyRatcliffe on 2007-02-21
> **tcornishmn said:**
> I agree, but maybe a solution would be that the metadata/no metadata selection would be in the preferences menu, therefore the save all/save selection buttons would both work whichever way the preference was set.

OK. I'll add a metadata on/off preference, and page range preference, and just leave it at one button.

---

### Post by tcornishmn on 2007-02-21
Sounds great!  Thanks again.

---

### Post by noynac on 2007-02-21
> **JeffreyRatcliffe said:**
> OK. I'll add a metadata on/off preference, and page range preference, and just leave it at one button.
Right now when I click on the "Save document" toolbar button, a dialog appears with the title "Save as PDF." This dialog contains three basic settings: metadata, compression, and page range. If I then click on save button, I get a second dialog with the title "PDF filename." 

If I understand correctly, there will now be a preference which will allow us to bypass the "Save as PDF" dialog. So, if that preference is enabled, we will get the "PDF filename" dialog when we click on the "Save document" button. If so, sounds great to me.

---

### Post by moshuptrail on 2007-02-21
Why not put page range on the last print screen (with file name)?  It's not logically part of metadata anyway.

I like to shove a whole stack of documents into the feeder and go away.  When I get back I use the selection option to divide the stack into the original documents, and save them one-by-one.

Other than page range, I leave the rest of meta data blank too.

---

### Post by gtratter on 2007-02-21
I am a Noob and really got excited when I found your program on this forum. I installed the latest version and dependencies. I am using a HP 5610 all in one unit - here is what I get when I type *gscan2pdf* at the command line:

```

 gscan2pdf
scanimage: open of device hpaio:/usb/Officejet_5600_series?serial=CN62ODE4QW04CY failed: Error during device I/O
*** unhandled exception in callback:
***   Can't call method "get_child" on an undefined value at /usr/bin/gscan2pdf line 2734.
***  ignoring at /usr/bin/gscan2pdf line 637.


```

I am able to scan images using Xsane but that is not what I am after - its PDF that I need!!

Any advise based upon the above?
thanks,
G

PS - this is the output for:

```

gt@gt-laptop:~$ scanimage --list-devices
device `hpaio:/usb/Officejet_5600_series?serial=CN62ODE4QW04CY' is a Hewlett-Packard Officejet_5600_series all-in-one
gt@gt-laptop:~$ 

```

---

### Post by JeffreyRatcliffe on 2007-02-21
> **moshuptrail said:**
> Why not put page range on the last print screen (with file name)?  It's not logically part of metadata anyway.

Well there is not just the metadata on that dialog, but the compression options too, as well as the page range. The file chooser dialog is a standard GTK dialog that would be difficult to modify.

> **moshuptrail said:**
> I like to shove a whole stack of documents into the feeder and go away.  When I get back I use the selection option to divide the stack into the original documents, and save them one-by-one.

This is how I work too.

---

### Post by JeffreyRatcliffe on 2007-02-21
> **gtratter said:**
> I am a Noob and really got excited when I found your program on this forum. I installed the latest version and dependencies. I am using a HP 5610 all in one unit - here is what I get when I type *gscan2pdf* at the command line:

It looks as though scanimage is having trouble accessing the device. If you email the output of ```
scanimage --help
``` to ra28145 at users.sf.net, I will take a look at it.

---

### Post by gtratter on 2007-02-22
> **gtratter said:**
> I am a Noob and really got excited when I found your program on this forum. I installed the latest version and dependencies. I am using a HP 5610 all in one unit - here is what I get when I type *gscan2pdf* at the command line:

```

 gscan2pdf
scanimage: open of device hpaio:/usb/Officejet_5600_series?serial=CN62ODE4QW04CY failed: Error during device I/O
*** unhandled exception in callback:
***   Can't call method "get_child" on an undefined value at /usr/bin/gscan2pdf line 2734.
***  ignoring at /usr/bin/gscan2pdf line 637.

```



**for the benefit of those who follow this thread:**
the above error was not caused by gscan2pdf. A reset of the hardware solved the problem.
After talking with Jeffrey I will try and see if I can pinpoint the cause of the error to begin with. If so - I'll report back.
**In the meantime - I have gscan2pdf running beautifully on 6.10 and I am a happy camper!**
Thanks, Jeffrey!

---

### Post by rkh on 2007-02-22
scanimage: open of device hpaio:/usb/Officejet_5600_series?serial=CN62ODE4QW04CY failed: Error during device I/O
*** unhandled exception in callback:
***   Can't call method "get_child" on an undefined value at /usr/bin/gscan2pdf line 2734.
***  ignoring at /usr/bin/gscan2pdf 

What mode were you scanning in? Older versions of hplip -like before the most recent- refuse to cooperate and returned the "Error during device I/O" when scanning in lineart mode. I could scan in lineart when I upgraded to the most version, but I still got that error message. I did find a workaround for command line scanning, but that doesnt help with gscan2pdf.

-RKH

---

### Post by JeffreyRatcliffe on 2007-02-22
> **rkh said:**
> I could scan in lineart when I upgraded to the most version, but I still got that error message. I did find a workaround for command line scanning, but that doesnt help with gscan2pdf.

gscan2pdf uses the command line tools scanimage and scanadf. If you let me know what the workaround was, perhaps I can make gscan2pdf work for you.

---

### Post by gtratter on 2007-02-22
> 
What mode were you scanning in? Older versions of hplip -like before the most recent- refuse to cooperate and returned the "Error during device I/O" when scanning in lineart mode. I could scan in lineart when I upgraded to the most version, but I still got that error message. I did find a workaround for command line scanning, but that doesnt help with gscan2pdf.

-RKH

hplip v 1.7.1
I used scanimage and scanadf - both are working now after a hardware reset..

---

### Post by rkh on 2007-02-23
The hplip list archives contained the suggestion to include the option "--compression=none" when using scanimage to avoid the I/O error. I couldn't find a decent scanning gui tool for documents that worked with my  HP laserjet 3020, so I  cobbled together a script that does what I need it to do. Basically, it scans the pages, converts .pnm to .ps and .ps to .pdf. Finally it joins all of the pages into one big document. It works good enough for scanning large piles of paper. I would say perfectly, but it has the habit of joining the pages slightly out of order when scanning more than ten pages.  Obviously, I would prefer that this not happen. But, since I am using it mainly to archive piles of paper that otherwise clutter up my life, good enough has been good enough so far.

---

### Post by JeffreyRatcliffe on 2007-02-24
> **rkh said:**
> The hplip list archives contained the suggestion to include the option "--compression=none" when using scanimage to avoid the I/O error. I couldn't find a decent scanning gui tool for documents that worked with my  HP laserjet 3020, so I  cobbled together a script that does what I need it to do. Basically, it scans the pages, converts .pnm to .ps and .ps to .pdf. Finally it joins all of the pages into one big document. It works good enough for scanning large piles of paper. I would say perfectly, but it has the habit of joining the pages slightly out of order when scanning more than ten pages.  Obviously, I would prefer that this not happen. But, since I am using it mainly to archive piles of paper that otherwise clutter up my life, good enough has been good enough so far.

If you convert .pnm to .tiff, you and import tiffs into gscan2pdf and play with the ordering, etc with the current version.

I have an HP OfficeJet, which also gives the --compression option, and which I was amazed to see defaults to JPEG, as I don't think that JPEG can work with lineart images. I can include the compression option in the next version. I hope that will sort out your problem.

---

### Post by JeffreyRatcliffe on 2007-02-24
Somebody (anon) has posted a feature request on the website ([https://sourceforge.net/tracker/?func=detail&atid=868101&aid=1667755&group_id=174140)](https://sourceforge.net/tracker/?func=detail&atid=868101&aid=1667755&group_id=174140)), suggesting that the front/back drop down list be changed to a radio button.

I think that as the single sided/double sided option is also a radio button, it would look slightly cluttered and confusing with a second, nested pair of buttons.

Anybody else care to comment (preferably on the tracker to keep the subject together, but obviously I'll read anything here as well)?

---

### Post by rkh on 2007-02-24
f you convert .pnm to .tiff, you and import tiffs into gscan2pdf and play with the ordering, etc with the current version.

For some reason, when I convert from .pnm to .tiff, rather than .pnm to .ps, the file comes out a lot bigger. The same thing happens if I convert directly to .pdf.  

I have no idea why this is- I'm a lawyer not a programmer.

---

### Post by JeffreyRatcliffe on 2007-02-24
> **rkh said:**
> For some reason, when I convert from .pnm to .tiff, rather than .pnm to .ps, the file comes out a lot bigger. The same thing happens if I convert directly to .pdf.

scanimage lets you scan directly to tiff.

When you convert to PDF, are you setting any compression? The Zip compression that tiff2pdf offers (and gscan2pdf can make use of) normally does pretty well.

---

### Post by rkh on 2007-02-24
> **JeffreyRatcliffe said:**
> scanimage lets you scan directly to tiff.

When you convert to PDF, are you setting any compression? The Zip compression that tiff2pdf offers (and gscan2pdf can make use of) normally does pretty well.

No-I am not setting any compression. I'll look into it when I have more free time. Thanks for the suggestions.

---

### Post by JeffreyRatcliffe on 2007-02-25
Following the open source edict of "Release early, release often", I have uploaded version 0.9.4 of my utility gscan2pdf to [http://sourceforge.net/projects/gscan2pdf](http://sourceforge.net/projects/gscan2pdf).

I have every intention of developing it into a fully-fledged application, so please as much constructive feedback as you like.

Here's my immediate todo list:

1. Crop & autocrop

Have fun!

Changes:
Using the top right hand close button to quit now saves the settings properly.
+ enable PDF options toggle
+ compression scan option
+ fixed bug 1656900 where hup condition not recognised under FreeBSD.
+ update to Czech translation (thanks to Petr Jelínek)
+ update to German translation (thanks to Florian)
+ update to Russian translation (thanks to Alexandre Prokoudine)

Just add the following line to your /etc/apt/sources.list:```
deb http://gscan2pdf.sourceforge.net/download/debian binary/
```
If you are you are using Synaptic, then use menu Edit/Reload Package Information, search for gscan2pdf in the package list, and lo and behold, you can install the nice shiny new version automatically.

From the command line:```
sudo apt-get update
sudo apt-get install gscan2pdf
```

The help will require Gtk2::Ex::PodViewer. Rotating requires Imagemagick. The scanadf frontend is in sane. For Email as PDF, you need xdg-utils. OCR requires gocr. Having installed gscan2pdf, locate the gscan2pdf entry in Synaptic, right-click it and you can install them under "Recommends".

If anybody fancies translating gscan2pdf into any other languages, they are welcome to do so on Rosetta ([https://launchpad.net/products/gscan2pdf/trunk/+pots/gscan2pdf](https://launchpad.net/products/gscan2pdf/trunk/+pots/gscan2pdf))

Please let me know what you think/how you get on, particularly with the new OCR & unpaper support. Is this how you want it handled? Improvements to the GUI?

---

### Post by noynac on 2007-02-25
Thanks for the new version. I checked and the close-button fix and save-PDF toggle both work great on my machine.

I was curious about one issue. The "enable options" preference only affects the save-PDF and not the save-TIFF functions. Did you consider including both in this preference? I never set any of the options (pages and compression) on the first save-TIFF dialog and personally would prefer to skip it. 

Thanks again.

---

### Post by JeffreyRatcliffe on 2007-02-26
> **noynac said:**
> I was curious about one issue. The "enable options" preference only affects the save-PDF and not the save-TIFF functions. Did you consider including both in this preference? I never set any of the options (pages and compression) on the first save-TIFF dialog and personally would prefer to skip it.

Compression is worth setting, as can greatly reduce the size of the resulting file. The most recently used settings are assumed if you disable settings.

I will make the enable options preference apply to save TIFF as well, I just wanted to make sure that it worked how everyone wanted before I did both.

---

### Post by rkh on 2007-03-02
After installing the latest HPLIP (1.7.2) I gave gscan2pdf another try. It scanned the stack of papers I fed into my HP 3020 quite well but refused to save either as a pdf or as a tiff. When I ran it again from the terminal I got this:

Use of uninitialized value in string eq at /usr/bin/gscan2pdf line 1082.
Use of uninitialized value in string eq at /usr/bin/gscan2pdf line 1082.
Use of uninitialized value in string eq at /usr/bin/gscan2pdf line 1082.
Use of uninitialized value in numeric gt (>) at /usr/bin/gscan2pdf line 1356.
Use of uninitialized value in concatenation (.) or string at /usr/bin/gscan2pdf line 1362.
tiff2pdf: No input file specified.
LIBTIFF, Version 3.8.2
Copyright (c) 1988-1996 Sam Leffler
Copyright (c) 1991-1996 Silicon Graphics, Inc.

usage:  tiff2pdf [options] input.tiff
options:
   [blah, blah, blah]
Use of uninitialized value in string eq at /usr/bin/gscan2pdf line 1082.
Use of uninitialized value in string eq at /usr/bin/gscan2pdf line 1082.
Use of uninitialized value in string eq at /usr/bin/gscan2pdf line 1082.
Use of uninitialized value in concatenation (.) or string at /usr/bin/gscan2pdf line 1541.
LIBTIFF, Version 3.8.2
Copyright (c) 1988-1996 Sam Leffler
Copyright (c) 1991-1996 Silicon Graphics, Inc.

usage: tiffcp [options] input... output
where options are:
  [blah, blah, blah]



Any thoughts?

-RHK

---

### Post by lodp on 2007-03-02
thanks for the work on the new version!

i'm having 2 issues, though:

- i don't get a full-page preview of the pages anymore -- it's only the numbered list with icon-size previews. how come? am i overlooking something?

- the mail-as-pdf function doesn't work for me -- it opens a new mail in thunderbird, but there's no attachment. is this because i'm on kubuntu?

---

### Post by JeffreyRatcliffe on 2007-03-02
> **rkh said:**
> After installing the latest HPLIP (1.7.2) I gave gscan2pdf another try. It scanned the stack of papers I fed into my HP 3020 quite well but refused to save either as a pdf or as a tiff.

Did you (ever) set the page range (all, current, selected)? If so, to what?

> i don't get a full-page preview of the pages anymore -- it's only the numbered list with icon-size previews. how come? am i overlooking something?

Has the detail window completely disappeared (i.e. are the thumbnails in the middle of the window, or on the left where they should be)? If you start gscan2pdf from the command line, do you get any error messages.

> the mail-as-pdf function doesn't work for me -- it opens a new mail in thunderbird, but there's no attachment. is this because i'm on kubuntu?

Current versions (1.5) of Thunderbird are not able to automatically add attachments to e-mail messages. Unless you can find a way to do it?

---

### Post by rkh on 2007-03-03
After installing the latest HPLIP (1.7.2) I gave gscan2pdf another try. It scanned the stack of papers I fed into my HP 3020 quite well but refused to save either as a pdf or as a tiff.

Did you (ever) set the page range (all, current, selected)? If so, to what?

Mea Culpa. Its working fine-I did go into synaptic and add all of the suggested dependencies but it wouldn't be out of character for me to forget to check an option. 

Although I  must say that you can't make an application that it truly idiot-proof unless you get some idiots to test if for you. I'm glad I could help.

-RKH

---

### Post by JeffreyRatcliffe on 2007-03-03
> **rkh said:**
> Mea Culpa. Its working fine-I did go into synaptic and add all of the suggested dependencies but it wouldn't be out of character for me to forget to check an option.

Not your fault. It wasn't a missing dependency. It was (I think) the new enable PDF option not checking whether the page range setting had ever been set. i.e. it was working for existing, but not new users. I'll make sure that is what it was and fix it.

Reporting these things really improves the software. Everyone has their own way of working and it can be sometimes quite tricky reproducing a bug, but that doesn't mean that it isn't worthwhile doing so.

---

### Post by jkzubu on 2007-03-03
Jeffrey -

First let me thank you for the framework of an outstanding (and much needed) package.  I just discovered this thread, installed the program and got it up and running with ease.  After running the program a few times (first runs) I am noticing some areas where deficiencies are apparent or fixes may be needed.

My goal is to scan a 25-page document and to save it as .pdf.  FYI I am running Edgy and my scan/fax/print multi is a HP G85xi with an adf.  (gscan2pdf v0.9.4)

Apparent issues:
1.  The adf loads the first page and repeat scans the first page despite my selection of all pages or # of pages to be scanned. This results in the first page being scanned multiple times and the subsequent pages remain in the adf tray without being circulated through the scan process.  I have ADF selected in the "Scan Document" preferences.  I also have Batch Scan = Yes.

2. From Main Menu - File - Frontend <scanimage or scanadf> the only available option is scanimage and scan adf is grayed out (Dependency needed??).

3.  On my test scans where the first page was scanned multiple times, I was unable to save the file as a .pdf to my desktop as targeted.  I was able to navigate to the desktop, type a file name and execute the command, but the file was not saved.

4.  Help menu attempts result in:  "The help viewer requires module Gtk2::Ex::PodViewer
Alternatively, try: gscan2pdf --help"  I tried to resolve using synaptic but could not.

5.  After pressing "Cancel Scan" the scanner continues to repeat scan the first page.  I am finding it necessary to press the cancel button on the scanner itself.  



Thank you.

-JK

---

### Post by JeffreyRatcliffe on 2007-03-04
> **jkzubu said:**
> 1.  The adf loads the first page and repeat scans the first page despite my selection of all pages or # of pages to be scanned. This results in the first page being scanned multiple times and the subsequent pages remain in the adf tray without being circulated through the scan process.  I have ADF selected in the "Scan Document" preferences.  I also have Batch Scan = Yes.

I also had this problem with my HP OfficeJet 5510. For me, the solution was to uninstall HPLIP and install the latest version from source. It may be worth trying the scanadf frontend first.

> **jkzubu said:**
> 2. From Main Menu - File - Frontend <scanimage or scanadf> the only available option is scanimage and scan adf is grayed out (Dependency needed??).

4.  Help menu attempts result in:  "The help viewer requires module Gtk2::Ex::PodViewer
Alternatively, try: gscan2pdf --help"  I tried to resolve using synaptic but could not.


To get all the optional dependencies, start Synaptic, search for gscan2pdf, right click on it, and use "Mark recommended for Installation". This will give you the scanadf frontend, OCR, rotating, help, etc.

> **jkzubu said:**
> 3.  On my test scans where the first page was scanned multiple times, I was unable to save the file as a .pdf to my desktop as targeted.  I was able to navigate to the desktop, type a file name and execute the command, but the file was not saved.

This sounds like a bug I managed to introduce in 0.9.4 that occurs if you don't actively set the page range. The first time ever, you have to set the page range, even if the default setting is what you want. Thereafter, your setting will be remembered and you don't have to reset it. If this doesn't fix things, start gscan2pdf from the command line and tell me know what the error messages are.

> **jkzubu said:**
> 5.  After pressing "Cancel Scan" the scanner continues to repeat scan the first page.  I am finding it necessary to press the cancel button on the scanner itself.  

This is a known bug! As far as I know, it is only a minor annoyance, so I have been spending time on other areas of the program. The best way to bump up its priority is to report it on gscan2pdf's bug-tracker on sourceforge.

---

### Post by grg3 on 2007-03-04
Just loaded and tried 0.9.4 and it still seems to work OK for me.

These two issues are still there but do not affect functionality:


Quote:
Originally Posted by grg3 View Post
The only paper size presented is custom which I set to 208 x279. Every time you scan it gives an error message that it is rounding the size to 207.974 (click close) and rounding size to 278.974 (click close).
That I can fix.

Quote:
Originally Posted by grg3 View Post
I can't seem to get it to save in the directory I want by default. Maybe I saved the first test in this one directory or something but that is always the default.
*Sound of penny dropping*

Those people who were having problems with it not remembering the window size, etc. - were you quitting with the close button in the top right hand corner, or with the quit button/menu? It shouldn't make any difference, but I was just trying a few things out, and the settings only seem to be properly saved if you use the quit button/menu.

Just thought I'd let you know. Thanks!

Rick

---

### Post by JeffreyRatcliffe on 2007-03-04
> **grg3 said:**
> The only paper size presented is custom which I set to 208 x279. Every time you scan it gives an error message that it is rounding the size to 207.974 (click close) and rounding size to 278.974 (click close).

I haven't fixed this yet. It is on the todo list, though.

> **grg3 said:**
> I can't seem to get it to save in the directory I want by default. Maybe I saved the first test in this one directory or something but that is always the default.

It should, by default, save/load from the last directory in which was saved/loaded. This is not happening? If you start gscan2pdf from the command line, do you get any error messages in the terminal window?

---

### Post by lodp on 2007-03-05
> **JeffreyRatcliffe said:**
> Has the detail window completely disappeared (i.e. are the thumbnails in the middle of the window, or on the left where they should be)? If you start gscan2pdf from the command line, do you get any error messages.

exactly, the thumbnails are in the middle of the window, there's no details window at all.  i don't get any error messages in the command line, except for those that i seem to get for EVERY application that i launch from commandline (but never seemed to be associated with any problems of that kind):

> X Error: BadDevice, invalid or uninitialized input device 155
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 155
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device



> **JeffreyRatcliffe said:**
> Current versions (1.5) of Thunderbird are not able to automatically add attachments to e-mail messages. Unless you can find a way to do it?

that's too bad. maybe i can find out something (though i'm not too savvy regarding these things).

---

### Post by JeffreyRatcliffe on 2007-03-05
> **lodp said:**
> exactly, the thumbnails are in the middle of the window, there's no details window at all.

You have managed to drag the pane divider right into the window border. If you can't find it to drag it back, quit gscan2pdf, delete the ~/.gscan2pdf file, and restart gscan2pdf, and you are back to default settings.

---

### Post by JeffreyRatcliffe on 2007-03-06
> **grg3 said:**
> The only paper size presented is custom which I set to 208 x279. Every time you scan it gives an error message that it is rounding the size to 207.974 (click close) and rounding size to 278.974 (click close).

I did put code in to fix that, but it evidently not working. Please run scanimage --batch from the command line and send the output that appears in the terminal window to ra28145 at users.sf.net, as well as the output from scanimage --help.

Or do you use scanadf as your frontend?

---

### Post by lodp on 2007-03-06
> **JeffreyRatcliffe said:**
> You have managed to drag the pane divider right into the window border. If you can't find it to drag it back, quit gscan2pdf, delete the ~/.gscan2pdf file, and restart gscan2pdf, and you are back to default settings.

i could have thought of that myself, sorry. it's working now,

i ran into a more serious issue now, though. i tried scanning and converting to pdf in color for the first time. the pdf looked fine in kpdf and evince, but when you view it in acrobat, the background is all red:

[IMG]http://img83.imageshack.us/img83/6079/details8ly5.png[/IMG]

it's also like that in the file icon preview on the KDE desktop and konqueror.

---

### Post by JeffreyRatcliffe on 2007-03-06
> **lodp said:**
> i ran into a more serious issue now, though. i tried scanning and converting to pdf in color for the first time. the pdf looked fine in kpdf and evince, but when you view it in acrobat, the background is all red:

Can you reproduce it having started gscan2pdf from the command line? Do you get any messages in the terminal window?

PDF creation is handled by tiff2pdf. Can you save the tiff and see what that looks like?

---

### Post by bmt on 2007-03-06
> **lodp said:**
> X error: BadDevice ...
These launch arrors are caused by entries in xorg.conf referencing devices that don't exist or aren't attached.  Certainly in Dapper, xorg.conf contains entries for a Wacom tablet by default.  If any of the Wacom devices are missing (even if there is a Wacom tablet attached, but it doesn't have all the devices), then these errors appear.  They are not critical and seem to have no effect on the way an application runs.  Comment out the lines in xorg.conf to get rid of the errors.

---

### Post by lodp on 2007-03-06
i did a new scan and saved as tiff. if it's encoded JPG, G3, or G4, the results are all black images, and i get the following errors:

JPG:
> JPEGSetupEncode: RowsPerStrip must be multiple of 16 for JPEG.
/home/martin/Desktop/jpgtest: Error, can't write strip 0.

G3
> 
/home/martin/Desktop/g3test: Bits/sample must be 1 for Group 3/4 encoding/decoding.
/home/martin/Desktop/g3test: Error, can't write strip 0.

G4
> /home/martin/Desktop/g4test: Bits/sample must be 1 for Group 3/4 encoding/decoding.
/home/martin/Desktop/g4test: Error, can't write strip 0.

when i save as pdf and select JPG, i don't get any errors in the command line, but the background is red (which doesn't happen when i select zip, or no encoding)

thanks for the tip with xorg.conf, bmt...

---

### Post by JeffreyRatcliffe on 2007-03-06
> **lodp said:**
> when i save as pdf and select JPG, i don't get any errors in the command line, but the background is red (which doesn't happen when i select zip, or no encoding)

I suppose the answer is to use ZIP encoding. JPEG is really best for photo-type images, due to the compression algorithm, so I wouldn't have used it for a close to black and white scan anyway. Sorry I can't be more helpful.

---

### Post by lodp on 2007-03-06
so.. is this a bug is tiff2pdf?

thing is with zip compression the file that i tested is about 20x the filesize, compared to jpg.. but i don't need color pdfs that much, so it's no biggie, actually.

---

### Post by JeffreyRatcliffe on 2007-03-07
> **lodp said:**
> so.. is this a bug is tiff2pdf?

It must be. Try reporting it.

---

### Post by gurgle on 2007-03-08
will a Fujitsu scansnap work with this program? Or what is teh best document scanner to use?

---

### Post by gtratter on 2007-03-08
Jeffrey,
I had to do a reinstall and didn't pay enough attention when the splash screen in gscan2pdf told me about missing dependencies. When I start gscan2pdf now, that splash screen no longer shows - what is the best way for me to find the dependencies missing?

---

### Post by JeffreyRatcliffe on 2007-03-08
> **gurgle said:**
> will a Fujitsu scansnap work with this program? Or what is teh best document scanner to use?

Should do. Basically anything that SANE supports will do. If you do a lot of scanning, you'll probably find it easier with an Automatic Document Feeder.

---

### Post by JeffreyRatcliffe on 2007-03-08
> **gtratter said:**
> I had to do a reinstall and didn't pay enough attention when the splash screen in gscan2pdf told me about missing dependencies. When I start gscan2pdf now, that splash screen no longer shows - what is the best way for me to find the dependencies missing?

Start Synaptic and search for gscan2pdf. Right click on it, and the recommended dependencies will be in the list.

---

### Post by JeffreyRatcliffe on 2007-03-09
Following the open source edict of "Release early, release often", I have uploaded version 0.9.5 of my utility gscan2pdf to [http://sourceforge.net/projects/gscan2pdf](http://sourceforge.net/projects/gscan2pdf).

I have every intention of developing it into a fully-fledged application, so please as much constructive feedback as you like.

Here's my immediate todo list:

1. Crop & autocrop

Have fun!

Changes:
Fixed bug where nothing saved if no default for page rage
Seperated pdf, tiff and scan compression defaults
+ Save TIFF and DjVu now respects enable options toggle
cancel on scan dialog now sends ctrl-c to scanimage
+ update to Czech translation (thanks to Petr Jelínek)

Just add the following line to your /etc/apt/sources.list:```
deb http://gscan2pdf.sourceforge.net/download/debian binary/
```
If you are you are using Synaptic, then use menu Edit/Reload Package Information, search for gscan2pdf in the package list, and lo and behold, you can install the nice shiny new version automatically.

From the command line:```
sudo apt-get update
sudo apt-get install gscan2pdf
```

The help will require Gtk2::Ex::PodViewer. Rotating requires Imagemagick. The scanadf frontend is in sane. For Email as PDF, you need xdg-utils. OCR requires gocr. Having installed gscan2pdf, locate the gscan2pdf entry in Synaptic, right-click it and you can install them under "Recommends".

If anybody fancies translating gscan2pdf into any other languages, they are welcome to do so on Rosetta ([https://launchpad.net/products/gscan2pdf/trunk/+pots/gscan2pdf](https://launchpad.net/products/gscan2pdf/trunk/+pots/gscan2pdf))

Please let me know what you think/how you get on, particularly with the OCR & unpaper support. Is this how you want it handled? Improvements to the GUI?

---

### Post by noynac on 2007-03-09
I downloaded the latest version and decided to see if cancel works. I began a scan and about half way through the scan, I clicked on the cancel button. The scan stopped, but I got the following error message: Unknown message: scanimage: sane_start: Error during device I/O. I tried this a second time with the same result. Everything else works great. 

My scanner is an Epson 3490, and I'm running Ubuntu 6.10.

Thanks for the update.

---

### Post by JeffreyRatcliffe on 2007-03-10
> **noynac said:**
> I downloaded the latest version and decided to see if cancel works. I began a scan and about half way through the scan, I clicked on the cancel button. The scan stopped, but I got the following error message: Unknown message: scanimage: sane_start: Error during device I/O. I tried this a second time with the same result. Everything else works great.

At least the scan stops now (which it doesn't on my OfficeJet - behaviour is definitely scanner-specific). I'll look at suppressing the error message, but I don't get it on mine, so I won't be able to test the code.

---

### Post by tcornishmn on 2007-03-10
I just got a chance to try the new version with the option to disable saving PDF metadata.  Thanks!  This is exactly what I was hoping for and it works perfectly.

One suggestion I would have is to change the text from Enable Options to something less generic, such as Enable Saving PDF Metadata or something like that.



Thanks again!

---

### Post by JeffreyRatcliffe on 2007-03-10
> **tcornishmn said:**
> One suggestion I would have is to change the text from Enable Options to something less generic, such as Enable Saving PDF Metadata or something like that.

Except that it now not only enable the metadata/page range/compression options on the save PDF dialog, but also for save TIFF and DjVu.

How about "Enable Save Options"?

---

### Post by tcornishmn on 2007-03-11
Sounds good to me - I like it.

Sorry if this has been discussed before, but it seems that zooming on the preview page is not working.  Has anyone else experienced this?

---

### Post by tcornishmn on 2007-03-11
Never mind - I had the line between the multi-page preview and the main preview all the way to the right.  I'm not sure how that happened.


I really think the way the page ordering and editing functionality works is very cool.  Would you ever consider opening this functionality up for existing PDFs?  It would be cool to be able to reorder pages, change orientation, etc for stuff I've scanned before I started using gscan2pdf.

Thanks again!

---

### Post by JeffreyRatcliffe on 2007-03-12
> **tcornishmn said:**
> I really think the way the page ordering and editing functionality works is very cool.  Would you ever consider opening this functionality up for existing PDFs?  It would be cool to be able to reorder pages, change orientation, etc for stuff I've scanned before I started using gscan2pdf.

It is an oft-suggested feature. The trouble is that it isn't very easy to do well. The easy method would be to use, say, imagemagick, to convert the PDF to TIFF first. However, I don't think that imagemagick can detect the resolution of any embedded images.

Better would be to extract the image straight. But I don't know how to do this, yet.

---

### Post by noynac on 2007-03-19
I wondered if anyone has successfully run gscan2pdf under Feisty Ubuntu. I tried it and had various problems including software locking up; scanner locking up; unable to find scanner; and so on. I posted a message on the Feisty forum about this but haven't gotten any response. I have the same problem with XSane under Feisty. Everything works great under Edgy.

---

### Post by JeffreyRatcliffe on 2007-03-20
> **noynac said:**
> I wondered if anyone has successfully run gscan2pdf under Feisty Ubuntu. I tried it and had various problems including software locking up; scanner locking up; unable to find scanner; and so on. I posted a message on the Feisty forum about this but haven't gotten any response. I have the same problem with XSane under Feisty. Everything works great under Edgy.

Sounds as though SANE or the backend (i.e. if HP, then HPLIP) is somehow broken. Best way to try and debug it is with scanimage on the command line. If it is reproducable there, you can report it as a bug in Launchpad.

I will probably upgrade soon after release day.

---

### Post by tcornishmn on 2007-03-20
I have been running on Feisty pretty much the whole time I've been using gscan2pdf.  My scanner is a Xerox Documate 252 and it has always worked flawlessly.

---

### Post by noynac on 2007-03-20
Thanks Jeffrey and tcornishmn for the responses. A posting just appeared in the Feisty forum, and other people are having the same problem as me. A link to a bug report is at:

[http://tinyurl.com/yrzw6g](http://tinyurl.com/yrzw6g)

I use my scanner a lot, so I'll just stick with Edgy for now.

---

### Post by noynac on 2007-03-26
I just noticed a small issue with version 0.9.5. 

If I have a check mark next to "enable options" and if I save a scan as a PDF file, the "PDF Filename" dialog disappears when I click on the save button. 

If I have a check mark next to "enable options" and if I save a scan as a TIFF file, the "TIFF Filename" dialog does not disappear when I click on the save button. However, the file is in fact saved, so this is a cosmetic issue only.

Thanks!

---

### Post by JeffreyRatcliffe on 2007-03-27
> **noynac said:**
> I just noticed a small issue with version 0.9.5.

Thanks for the bug report. I can't reproduce it with the development version, but I've changed things a bit under the hood for the next version, so perhaps it got fixed on the way...

---

### Post by noynac on 2007-03-27
I apologize but my posting was in error. The second and third paragraphs should begin:

If I DO NOT have a check mark next to "enable options"....

Everything works fine if I have a check mark next to "enable options." Sorry for the mistake.

---

### Post by JeffreyRatcliffe on 2007-03-28
> **noynac said:**
> If I DO NOT have a check mark next to "enable options"....

That bug was still in the development version, and I have just fixed it. Thanks for the report.

---

### Post by spivak.d on 2007-03-28
I LOVE your program. I've dropped even xsane as this so much better suited for document scanning.

Any plans to enable a feature that does OCR and then places the OCR text under the graphic itself? This happens under MODI in Windows and means you see the original page, but can also search it. 

Also, any reason that the files I get out of this are so large at the same DPI as I use when using Windows XP? A TIFF there is typically under 100kb but about 1.5mb here.

-Dima

---

### Post by JeffreyRatcliffe on 2007-03-29
> **spivak.d said:**
> Any plans to enable a feature that does OCR and then places the OCR text under the graphic itself? This happens under MODI in Windows and means you see the original page, but can also search it.

This very feature will be in the next release - the text being embedded as an annotation (in Acrobat they are called pop-up notes). However, I was disappointed with the fact that Beagle (via pdftotext) doesn't search them. I opened a feature request with Beagle ([http://bugzilla.gnome.org/show_bug.cgi?id=417984](http://bugzilla.gnome.org/show_bug.cgi?id=417984)) and Poppler ([https://bugs.freedesktop.org/show_bug.cgi?id=10300)](https://bugs.freedesktop.org/show_bug.cgi?id=10300)), but I don't see much changing soon.

I'm not aware of MODI. How does this program do the embedding?

If someone can show me a better/additional way to embed the OCR output, then I'll consider it.

> **spivak.d said:**
> Also, any reason that the files I get out of this are so large at the same DPI as I use when using Windows XP? A TIFF there is typically under 100kb but about 1.5mb here.

That rather depends upon the compression you use. Can you quote your resolution and compression settings?

---

### Post by spivak.d on 2007-03-29
Using 300 resolution along with ZIP compression in PDF as a grayscale scan, I get file sizes over 1.2 mb when putting through a single piece of paper. Perhaps there's a way to have a preset created for the purpose of optimizing the crispness of document scanning while not preserving the extraneous bits of scanned images (e.g. gradients due to folds in paper)?

---

### Post by JeffreyRatcliffe on 2007-03-29
> **spivak.d said:**
> Using 300 resolution along with ZIP compression in PDF as a grayscale scan, I get file sizes over 1.2 mb when putting through a single piece of paper. Perhaps there's a way to have a preset created for the purpose of optimizing the crispness of document scanning while not preserving the extraneous bits of scanned images (e.g. gradients due to folds in paper)?

There are features in unpaper that will deal with things like gradients due to folds. Not that I've implemented them in gscan2pdf, though.

Mostly, I find lineart (binary) gives me good enough quality at 300 dpi, and the PDF with ZIP compression comes in at around 20-30kb.

---

### Post by spivak.d on 2007-03-29
Ah ha! That was it. If I can make a suggestion, maybe change the name of the scanning present from "Lineart" to something more intuitive like "Document B/W". As a student, I just assumed "Gray" meant much less quality, small filesize, etc...

---

### Post by spence686 on 2007-03-29
Kudos Jeffrey; gscan2pdf and this thread truly are beacons in the opensource world.  I am using a Brother MFC-5460CN with gscan2pdf, which is working very well.  The only thing I cant seem to do at this time is scan large double-sided documents easily. (The double sided options are ghosted in the scan document pane)  Would I be correct in assuming that this is a shortcoming of scanadf?

---

### Post by JeffreyRatcliffe on 2007-03-30
> **spivak.d said:**
> Ah ha! That was it. If I can make a suggestion, maybe change the name of the scanning present from "Lineart" to something more intuitive like "Document B/W". As a student, I just assumed "Gray" meant much less quality, small filesize, etc...

It's a bit tricky, that. I just pass on whatever the backend calls it. With HPs it is lineart, Brother gives you Black & White, the Canon example I have doesn't even have a binary mode, Epson calls it binary. Personally, I think Black & White makes the most sense.

> **spence686 said:**
> Kudos Jeffrey; gscan2pdf and this thread truly are beacons in the opensource world.  I am using a Brother MFC-5460CN with gscan2pdf, which is working very well.  The only thing I cant seem to do at this time is scan large double-sided documents easily. (The double sided options are ghosted in the scan document pane)  Would I be correct in assuming that this is a shortcoming of scanadf?

In scanimage, you can increment the page number by 2 or -2 (or anything else). scanadf doesn't allow this. Therefore, to get double-sided scanning working with scanadf, I would have to redesign the way gscan2pdf decides which page the scan is. Not impossible - would just need to throw some time at it.

The best way to encourage me would be to file a feature request on the website on Sourceforge.

---

### Post by JeffreyRatcliffe on 2007-03-31
Following the open source edict of "Release early, release often", I have uploaded version 0.9.6 of my utility gscan2pdf to [http://sourceforge.net/projects/gscan2pdf](http://sourceforge.net/projects/gscan2pdf).

I have every intention of developing it into a fully-fledged application, so please as much constructive feedback as you like.

Here's my immediate todo list:

1. Crop & autocrop

Have fun!

Changes:
"Enable Options" now "Enable Save Options"
+ After cancelling scan, I/O error ignored.
+ tiff2pdf replaced with PDF::API2,
  fixing character encoding bug in metadata
+ OCR result buffer now embedded as annotation in PDF
+ PDF import
+ Now loads modules when needed, rather than at start to speed up start-up.
+ Can import any format that imagemagick recognises
+ Makes use of new_from_file_at_scale (speedup)
+ OptionMenus swapped for ComboBoxes (+EventBoxes to wrap ToolTips)
+ Fixed bug caused by trying to hide save_TIFF dialog although not created
+ SpinButtons to adjust top left corner of scan area
+ Now ghosts save options when no pages to save
+ Italian translation (thanks to Alberto Boiti)
+ Update to Dutch translation (thanks to Eric Spierings)

Just add the following line to your /etc/apt/sources.list:```
deb http://gscan2pdf.sourceforge.net/download/debian binary/
```
If you are you are using Synaptic, then use menu Edit/Reload Package Information, search for gscan2pdf in the package list, and lo and behold, you can install the nice shiny new version automatically.

From the command line:```
sudo apt-get update
sudo apt-get install gscan2pdf
```

There are two new dependencies - perlmagick and libpdf-api2-perl, as well as the old ones - libgtk2-perl (>= 1:1.043-1), libgtk2-ex-simple-list-perl, libglib-perl (>= 1.100-1), liblocale-gettext-perl (>= 1.05), libsane, sane-utils, libtiff-tools.

The help will require Gtk2::Ex::PodViewer. Rotating requires Imagemagick. The scanadf frontend is in sane. For Email as PDF, you need xdg-utils. OCR requires gocr. Having installed gscan2pdf, locate the gscan2pdf entry in Synaptic, right-click it and you can install them under "Recommends".

If anybody fancies translating gscan2pdf into any other languages, they are welcome to do so on Rosetta ([https://launchpad.net/products/gscan2pdf/trunk/+pots/gscan2pdf](https://launchpad.net/products/gscan2pdf/trunk/+pots/gscan2pdf))

Please let me know what you think/how you get on, particularly with the OCR & unpaper support. Is this how you want it handled? Improvements to the GUI? Better ideas on how to embed the OCR output in the PDF?

---

### Post by noynac on 2007-03-31
Jeffrey,

Thanks for the new release. There are a lot of neat, new features. 

I have encountered two issues with this release. 

First, all imported PDF files are shown in gscan2pdf in reverse video. This happens when:

1) I scan a page of text at 300 dpi in lineart mode; 

2) save this scan as a PDF file;

3) exit then reload gscan2pdf; and

4) import the PDF file created in steps 1 and 2 above.

Second, I occasionally receive the following error message after I click on the scan button: "Unknown message: scanimage: option `--=' is ambiguous."

A screenshot illustrating the above can be found at:

[Link Deleted]

My scanner is an Epson 3490, and my OS is Ubuntu 6.10. I checked synaptic and all dependencies appear to be installed. 

I really appreciate the option to import PDF files; I will use this often. 

modred

---

### Post by JeffreyRatcliffe on 2007-04-01
> **noynac said:**
> First, all imported PDF files are shown in gscan2pdf in reverse video.

Yeah. I noticed this too. The problem seems to be with imagemagick. I use the pdfimages utility from xpdf or poppler. This extracts the images from the PDF to ppm files. These seem to be OK. I use imagemagick to convert from ppm to tiff.

It also depends on which program created the PDF. PDFs created with an older version of gscan2pdf, which used tiff2pdf, seem to import OK.

> **noynac said:**
> Second, I occasionally receive the following error message after I click on the scan button: "Unknown message: scanimage: option `--=' is ambiguous."

I think I have that nailed. A bit more testing will tell. I will definitely have a bugfix release out in a couple of days.

---

### Post by spence686 on 2007-04-01
I've been testing 0.9.6 and have found a few issues:

1.  Unable to import pdf's.  I have tried gscan2pdf 0.9.5 .pdf's and others as well, the import image dialog box closes, and nothing happens, not even any terminal output.  The program does not crash or hang.  Tiff's and jpegs open ok, but I do get the the following output when opening a tiff:

Exception 350: /home/spencer/school/Math3032-PDE/Assignment3.tif: unknown field with tag 37680 (0x9330) encountered. `TIFFReadDirectory' at /usr/bin/gscan2pdf line 1038.
TIFFReadDirectory: Warning, /home/spencer/school/Math3032-PDE/Assignment3.tif: unknown field with tag 37680 (0x9330) encountered.[/COLOR]

2.  When scanning from the adf, i get error message popups and terminal output (the scanning then proceeds normally after i click ok):

Unknown message: scanadf: rounded value of br-x from 215.9 to 215.88
Unknown message: scanadf: rounded value of br-y from 279.4 to 279.374

3.  I am a bit unclear on unpaper.  Is this supposed to be working?  It is ghosted on my tools menu.

I am running Dapper, and I have a Brother MFC-5460CN, connected via LAN
Thanks for the excellent program!

---

### Post by JeffreyRatcliffe on 2007-04-02
> **spence686 said:**
> 1.  Unable to import pdf's.  I have tried gscan2pdf 0.9.5 .pdf's and others as well, the import image dialog box closes, and nothing happens, not even any terminal output.  The program does not crash or hang.

You are starting gscan2pdf from a terminal and get no error message? Strange. You need the pdfimages utility that is part of xpdf or poppler. Launchpad is down at the moment, so I can't check what the package is called. Also this will only import the embedded images, so with a PDF that is not a scan or an image, you won't get anything.

> **spence686 said:**
> Tiff's and jpegs open ok, but I do get the the following output when opening a tiff:

Do you get the error message on opening the TIFF, or when you create the PDF? It looks as though gtk+ or PDF::API2 doesn't like the image.

> **spence686 said:**
> 2.  When scanning from the adf, i get error message popups and terminal output (the scanning then proceeds normally after i click ok):

Unknown message: scanadf: rounded value of br-x from 215.9 to 215.88

OK. Those I can suppress.

> **spence686 said:**
> 3.  I am a bit unclear on unpaper.  Is this supposed to be working?  It is ghosted on my tools menu.

You need to install the unpaper package first. Search in Synaptic.

---

### Post by spence686 on 2007-04-02
> You are starting gscan2pdf from a terminal and get no error message? Strange. You need the pdfimages utility that is part of xpdf or poppler. Launchpad is down at the moment, so I can't check what the package is called. Also this will only import the embedded images, so with a PDF that is not a scan or an image, you won't get anything.

I have pdfimages installed as part of poppler-utils

> Do you get the error message on opening the TIFF, or when you create the PDF? It looks as though gtk+ or PDF::API2 doesn't like the image.


The message was output from the terminal when opening a TIFF

> You need to install the unpaper package first. Search in Synaptic.

I must not have that repo.  Can you tell me the sources.list entry?  I googled a bit, no luck.

Thanks again.

---

### Post by JeffreyRatcliffe on 2007-04-02
> **spence686 said:**
> I have pdfimages installed as part of poppler-utils

If you send me the PDF (ra28145 at users dot sf dot net), I'll take a look.

> **spence686 said:**
> The message was output from the terminal when opening a TIFF

It looks as though GTK+ doesn't like it, but again, if you send me the TIFF, I'll take a look.

> **spence686 said:**
> I must not have that repo.  Can you tell me the sources.list entry?  I googled a bit, no luck.

Launchpad is back up and says that it is in universe. I'm using the German repository for Edgy. Edit as necessary:
```

deb http://de.archive.ubuntu.com/ubuntu/ edgy universe
deb-src http://de.archive.ubuntu.com/ubuntu/ edgy universe
```

---

### Post by spence686 on 2007-04-03
> 
Quote:
You are starting gscan2pdf from a terminal and get no error message? Strange. You need the pdfimages utility that is part of xpdf or poppler. Launchpad is down at the moment, so I can't check what the package is called. Also this will only import the embedded images, so with a PDF that is not a scan or an image, you won't get anything.

[QUOTE]I have pdfimages installed as part of poppler-utils

[/QUOTE]

I was able to get the pdf and tiff import working.  I uninstalled poppler-utils and installed xpdf, which seemed to do the trick.

---

### Post by Mongoose on 2007-04-04
Kind of related... 

USB scanners that only work with those 300MB Windows 'drivers' -- for example the HP ScanJet 2400 -- can be used via a vmware Windows guest.   Just make a Windows vmware image, and install the drivers.  You can scan to SMB mounts to make it easier to manage from Linux.  Unfortunely this is a work around I'm using until I can get a better scanner.  I think it's the only HP scanner that's not supported.  =/

---

### Post by JeffreyRatcliffe on 2007-04-04
> **spence686 said:**
> I was able to get the pdf and tiff import working.  I uninstalled poppler-utils and installed xpdf, which seemed to do the trick.

I'm glad you got it working, but it is a shame that poppler was causing the trouble, as poppler, whilst a fork of xpdf, is in open development.

Thanks for sending me the files.

The TIFF error is produced by Imagemagick which I use to check the format of the image before trying to import it. You can safely ignore it.

I'll test the PDF with Poppler tonight. xpdf extracted the images correctly, but imagemagick reversed the colours, so they come into gscan2pdf white on black instead of the other way around. I've seen this too with my own scans. I guess this is better than no PDF import, so I'll leave it as it is while I work out a solution.

---

### Post by pneaveill on 2007-04-04
Been a part of the thread for a while now and wanted to download this to a different computer but was unable to do so.  It needs libgtk2-ex-simple-list-perl. Where do I get this dependency?  I ran a search on synaptic and could not find it. Please advise.

---

### Post by JeffreyRatcliffe on 2007-04-04
> **pneaveill said:**
> It needs libgtk2-ex-simple-list-perl. Where do I get this dependency?  I ran a search on synaptic and could not find it. Please advise.

libgtk2-ex-simple-list-perl is available in the Edgy repositories. Or you can take the .deb from the gscan2pdf website, which I put there when Dapper users were having trouble.

---

### Post by JeffreyRatcliffe on 2007-04-04
> **JeffreyRatcliffe said:**
> I'll test the PDF with Poppler tonight. xpdf extracted the images correctly, but imagemagick reversed the colours, so they come into gscan2pdf white on black instead of the other way around. I've seen this too with my own scans. I guess this is better than no PDF import, so I'll leave it as it is while I work out a solution.

Bizarrely, with the standard version of Poppler and Imagemagick on my Edgy box, your PDF imports completely correctly, with no colour reversal.

---

### Post by rkh on 2007-04-05
I downloaded and installed version 9.6 and have run into some problems. When I click on scan, the regular window pops up. Under Device-dependent options a bar bounces back and forth for a second while displaying the message "updating options." It then displays a lot of options. The problem is that the scan button is now off pushed off of the visible area of the screen and the window refuses to let me resize it vertically. 

I tried to change the fronted from scaniage to scanadf. That resulted in me having the more limited options that I had with previous versions of gscan2pdf and access to the scan button. But when I tried to scan I got the following error message:

Unknown message: scanadf: setting of option --compression failed (Invalid argument) 

Still- all in all, this is a terrific tool. Thanks for all of your hard work.

Oh yeah: HP laserjet 3020 on Edgy.

RKH

---

### Post by JeffreyRatcliffe on 2007-04-05
> **rkh said:**
> I downloaded and installed version 9.6 and have run into some problems. When I click on scan, the regular window pops up. Under Device-dependent options a bar bounces back and forth for a second while displaying the message "updating options." It then displays a lot of options. The problem is that the scan button is now off pushed off of the visible area of the screen and the window refuses to let me resize it vertically.

I managed to introduce a bug in the updating options routine in 0.9.6. I'm about to release 0.9.7, so perhaps you can tell me whether that fixes your problem.

---

### Post by JeffreyRatcliffe on 2007-04-05
Following the open source edict of "Release early, release often", I have uploaded version 0.9.7 of my utility gscan2pdf to [http://sourceforge.net/projects/gscan2pdf](http://sourceforge.net/projects/gscan2pdf).

I have every intention of developing it into a fully-fledged application, so please as much constructive feedback as you like.

Here's my immediate todo list:

1. Crop & autocrop

Have fun!

Changes:
+ Fixed bug calling help
+ Fixed error message caused by update_options sub being called twice.
+ Streamlined image creation (speedup)
+ Adjusted widget justification in scan dialog
+ Suppressed rounded messages from scanadf frontend
+ Remembers scan area
+ Ghosts zoom and rotate buttons if no page selected
+ Fixed bug where custom scan area not hidden when A4 or Letter selected
+ Help update

Just add the following line to your /etc/apt/sources.list:```
deb http://gscan2pdf.sourceforge.net/download/debian binary/
```
If you are you are using Synaptic, then use menu Edit/Reload Package Information, search for gscan2pdf in the package list, and lo and behold, you can install the nice shiny new version automatically.

From the command line:```
sudo apt-get update
sudo apt-get install gscan2pdf
```

There are two new dependencies - perlmagick and libpdf-api2-perl, as well as the old ones - libgtk2-perl (>= 1:1.043-1), libgtk2-ex-simple-list-perl, libglib-perl (>= 1.100-1), liblocale-gettext-perl (>= 1.05), libsane, sane-utils, libtiff-tools.

The help will require Gtk2::Ex::PodViewer. Rotating requires Imagemagick. The scanadf frontend is in sane. For Email as PDF, you need xdg-utils. OCR requires gocr. Having installed gscan2pdf, locate the gscan2pdf entry in Synaptic, right-click it and you can install them under "Recommends".

If anybody fancies translating gscan2pdf into any other languages, they are welcome to do so on Rosetta ([https://launchpad.net/products/gscan2pdf/trunk/+pots/gscan2pdf](https://launchpad.net/products/gscan2pdf/trunk/+pots/gscan2pdf))

Please let me know what you think/how you get on, particularly with the OCR & unpaper support. Is this how you want it handled? Improvements to the GUI? Better ideas on how to embed the OCR output in the PDF?

---

### Post by rkh on 2007-04-05
I just installed 9.7. The scan button is back, but now I get the following error message with either frontend:

Unknown message: scanimage: setting of option --compression failed (Invalid argument)

-RKH

---

### Post by JeffreyRatcliffe on 2007-04-05
> **rkh said:**
> I just installed 9.7. The scan button is back, but now I get the following error message with either frontend:

Unknown message: scanimage: setting of option --compression failed (Invalid argument)

Please send the output from ```
scanimage --help
``` to ra28145 at users dot sf dot net

---

### Post by noynac on 2007-04-05
The list of changes does not mention the bug that caused imported PDF lineart files to appear in gscan2pdf as reverse video. Was this fixed? Thanks!

---

### Post by JeffreyRatcliffe on 2007-04-06
> **noynac said:**
> The list of changes does not mention the bug that caused imported PDF lineart files to appear in gscan2pdf as reverse video. Was this fixed?

No. I haven't figured out what exactly is causing it. It doesn't always happen. I fear I might have to just add a button to reverse a b/w image as a workaround.

---

### Post by JeffreyRatcliffe on 2007-04-06
> **rkh said:**
> I just installed 9.7. The scan button is back, but now I get the following error message with either frontend:

Unknown message: scanimage: setting of option --compression failed (Invalid argument)

Thanks for the output.

Are you leaving the compression option to the default JPEG? Have you tried setting it to none? JPEG compression and lineart don't mix. This is a problem with the HP backend, and coincidentally, somebody else has had the same problem and the same workaround: [https://sourceforge.net/tracker/?func=detail&atid=868098&aid=1695281&group_id=174140](https://sourceforge.net/tracker/?func=detail&atid=868098&aid=1695281&group_id=174140)

---

### Post by tcornishmn on 2007-04-09
Thanks so much for your continued work on this program.  I upgraded to .97 and did a little scanning trying to figure out the saving of OCR data to the PDF metadata.  How does this work?  Do I run the scan, then click OCR and let it run, and then cancel at the dialog box that lists the OCR output, since that dialog mostly relates to saving it to a text file, or do I have to save it somehow?


Here are a couple of additional feature requests.  Perhaps others may find some of these things useful as well:

1.  Create some batch mechanism that allows OCR to run in the background so that scanning input can continue

I realize that there are times that the user may want to edit the OCR data before it is saved in the PDF, but I mainly use the program for creating digital paper and speed is more important than accuracy.  Some of the other programs (OmniPage Pro, Adobe Acrobat Capture), have a workflow that allows scanning to happen independently of the OCR process.  It would be great if the other function that takes a lot of processing time -unpaper- could be imported into this batch flow as well.  The workflow that would be most useful to me would be:
Scan -> prompt for file details such as name, metadata and save location -> unpaper for deskewing/optional other proccessing -> OCR embedding to PDF-> Save in location specified earlier.

Program control would return to the user after the prompt for file details step.


2.  Be able to adjust the lineart/B&W threshhold

I've found that if I have a document that has, for example, black printed text, and blue ballpoint pen writing on it, of for that matter other situations where some of the writing/printing is darker than others, that lineart mode won't capture some of the lighter text.  This forces me to grayscale, which eats up much more space than is really necessary.  Do you know if the lineart threshhold is scanner specific, or fixed in some way, or would it be possible to say set it to 40% black instead of 50%, like the lightness/darkness control of a copier?

For the record, I have a Xerox Documate 252 sheetfed scanner and an Epson 3590 flatbed scanner.  Both work great with gScan2PDF.

3.  Have more control of unpaper/OCR

I haven't been able to reliably use unpaper for a similar reason to wishlist item number 2 - it seems to eat some of the data I want.  An example would be scanning a form such as an invoice, which has lines separating the various columns.  I would like to use the deskewing part of unpaper, but not have it eat all of the content it doesn't understand, like the row and column lines.  


Again, thank you for your work on this program.  This was one of the main things that I was still doing in Windows.  Now, other than the OCR issue, your program actually works better than my Windows software, especially in its error handling capability if the scanner gets hosed with a paper jam or other issue.

---

### Post by JeffreyRatcliffe on 2007-04-09
> **tcornishmn said:**
> I upgraded to .97 and did a little scanning trying to figure out the saving of OCR data to the PDF metadata.  How does this work?  Do I run the scan, then click OCR and let it run, and then cancel at the dialog box that lists the OCR output, since that dialog mostly relates to saving it to a text file, or do I have to save it somehow?

Having run the OCR, the buffer is automatically stored with the page (each page has its own buffer), and when you save it as a PDF, the contents of each buffer is saved with the appropriate page as an annotation. If you open the PDF in Acrobat Reader, you will see the notes.

I had hoped that Beagle would then index the annotations, but unfortunately this is not the case. It relies on pdftotext, which at the moment doesn't read them. I have logged a feature request.

I agree that the current GUI design for the OCR integration isn't very good, but until either pdftotext starts reading the annotations, or I figure out a better way of embedding the OCR output in the PDF, I'm not sure how useful it is.

> **tcornishmn said:**
> 1.  Create some batch mechanism that allows OCR to run in the background so that scanning input can continue

Absolutely. I am open to things like this as soon as the OCR output is properly useful.

> **tcornishmn said:**
> 2.  Be able to adjust the lineart/B&W threshhold

This is complete dependent upon the backend. If you send the output of scanimage --help to ra28145 at users dot sf dot net, I'll look at if it is possible for your scanner(s).

> **tcornishmn said:**
> 3.  Have more control of unpaper/OCR

The OCR and unpaper dialogs are just (at the moment very limited) ways of collected options passed to the gocr and unpaper command line tools respectively. If you have a look at the documentation for those tools and want a particular option added, I will be glad to do so.

I will upgrade to Feisty soon after it is released and will then work on also supporting tesseract, which is Google's open source OCR offering and supposed to be very good.

---

### Post by tcornishmn on 2007-04-09
I've looked briefly at the unpaper usage and I'm not entirely sure which function has been eating my content, so perhaps you or someone else may have a better list of relevant options.  Acutally, it would be interesting to see what options you have chosen for comparison.

In any case, here are the options that I think would be nice to be able to adjust:

**--no-mask-scan** - I suspect this is the one that is eating my cell borders.
**--no-deskew ** - Personally this is the most useful feature to me, but since it is a major funtion of unpaper, maybe it deserves it's own toggle in case someone doesn't want it.

The following list may be interesting, but I guess I don't entirely understand what they do or how useful they may be.  Any comments on these?

--no-blackfilter
--no-noisefilter
--no-blurfilter
--no-border-scan
-w --white-threshold
-b --black-threshold

---

### Post by JeffreyRatcliffe on 2007-04-10
> **tcornishmn said:**
> Acutally, it would be interesting to see what options you have chosen for comparison.

--layout is self-evident, I hope.
--deskew-scan-direction seemed also to me to be the most useful.
--border-align I put in because having deskewed my scan, it was getting centred when sometimes I didn't want it to be.

> **tcornishmn said:**
> In any case, here are the options that I think would be nice to be able to adjust:

**--no-mask-scan** - I suspect this is the one that is eating my cell borders.
**--no-deskew ** - Personally this is the most useful feature to me, but since it is a major funtion of unpaper, maybe it deserves it's own toggle in case someone doesn't want it.

OK. I'll add these as I find time.

> **tcornishmn said:**
> --no-blackfilter
--no-noisefilter
--no-blurfilter
--no-border-scan
-w --white-threshold
-b --black-threshold

I wouldn't be able to do more than repeat the documentation on the unpaper website. I can add the options, though.

---

### Post by spence686 on 2007-04-10
I have noticed some problems when using unpaper.  When unpapering multiple page documents, my system will slow down dramatically.  I tried to unpaper a 30 page document, and ended up having to hit the reset button, as my system became totally unresposive.  I have noticed that there will be an unpaper tab on the taskbar for every page that is in the document.  This leads me to believe that each page is being worked on simultaneously.  If each page was unpapered in succession, would this make for a more reasonable load on my system?  Thanks again for your hard work, its really helping me out.

---

### Post by JeffreyRatcliffe on 2007-04-10
> **spence686 said:**
> I have noticed some problems when using unpaper.  When unpapering multiple page documents, my system will slow down dramatically.  I tried to unpaper a 30 page document, and ended up having to hit the reset button, as my system became totally unresposive.  I have noticed that there will be an unpaper tab on the taskbar for every page that is in the document.  This leads me to believe that each page is being worked on simultaneously.  If each page was unpapered in succession, would this make for a more reasonable load on my system?

I have to admit as never to have tried using unpaper on more than one page at once. I'll investigate.

---

### Post by JeffreyRatcliffe on 2007-04-11
> **spence686 said:**
> I have noticed some problems when using unpaper.  When unpapering multiple page documents, my system will slow down dramatically.

You are right, and the solution had me scratching my head for a bit - but it will be fixed in the next version.

---

### Post by [eXr] on 2007-04-13
Hi everyone,

I think this could be useful for you:
[http://www.megginson.com/blogs/quoderat/2006/01/26/scanning-to-pdf-in-linux/](http://www.megginson.com/blogs/quoderat/2006/01/26/scanning-to-pdf-in-linux/)

Have a nice day! =)

---

### Post by mtn on 2007-04-18
I have been struggling for about 20mins to get my Canon CanoScan LiDE 25 working with Feisty Fawn beta. XSane doesn't seem to work (seems to be a bug) but [gscan2pdf]("http://gscan2pdf.sourceforge.net/") worked straight away, and beyond my wildest dreams. Fantastic, thanks.

---

### Post by JeffreyRatcliffe on 2007-04-28
Following the open source edict of "Release early, release often", I have uploaded version 0.9.8 of my utility gscan2pdf to [http://sourceforge.net/projects/gscan2pdf](http://sourceforge.net/projects/gscan2pdf).

I have every intention of developing it into a fully-fledged application, so please as much constructive feedback as you like.

Here's my immediate todo list:

1. Crop & autocrop

Have fun!

Changes:
- compression option from scan dialog.
+ Explicitly sets compression=None if mode=Lineart
+ Check for PDF::API2
+ Forces startup check on new version
+ Runs unpaper sequencially on pages instead of in parallel
+ Enabled double sided scanning for scanadf frontend
+ no-deskew, no-border-scan, no-border-align, no-mask-scan, no-blackfilter no-noisefilter, no-blurfilter, black-threshold, white-threshold options to unpaper
+ Stock icon for about
+ Scrolls thumb list to selected page
+ Embeds OCR output in white on white hidden behind scan. pdftotext can extract contents, and can be indexed by Beagle.
+ Update to Spanish translation (thanks to Th3n3k)
+ Moved OCR buffer to main window
+ Patch from John Goerzen to adjust brightness and add negative support for SpinBoxes
+ Patches from John Goerzen to add .tif and .djvu endings if necessary, plus fixed bug adding .pdf ending.
+ Separated perlmagick and imagemagick dependencies
+ Updated French translation (thanks to Mathieu Goeminne)

Just add the following line to your /etc/apt/sources.list:```
deb http://gscan2pdf.sourceforge.net/download/debian binary/
```
If you are you are using Synaptic, then use menu Edit/Reload Package Information, search for gscan2pdf in the package list, and lo and behold, you can install the nice shiny new version automatically.

From the command line:```
sudo apt-get update
sudo apt-get install gscan2pdf
```

The dependencies are libgtk2-perl (>= 1:1.043-1), libgtk2-ex-simple-list-perl, perlmagick, libpdf-api2-perl, liblocale-gettext-perl (>= 1.05), libsane, sane-utils, libtiff-tools.

The help will require Gtk2::Ex::PodViewer. Rotating requires Imagemagick. The scanadf frontend is in sane. For Email as PDF, you need xdg-utils. OCR requires gocr. Having installed gscan2pdf, locate the gscan2pdf entry in Synaptic, right-click it and you can install them under "Recommends".

If anybody fancies translating gscan2pdf into any other languages, they are welcome to do so on Rosetta ([https://launchpad.net/products/gscan2pdf/trunk/+pots/gscan2pdf](https://launchpad.net/products/gscan2pdf/trunk/+pots/gscan2pdf))

Please let me know what you think/how you get on, particularly with the OCR & unpaper support. Is this how you want it handled? Improvements to the GUI?

---

### Post by noynac on 2007-04-28
Jeffrey,

Thanks for the new version. 

I tried a few test scans on my Epson 3490 scanner. When scanning in lineart mode, I get a dialog with the message:

Unknown message: scanimage: unrecognized option `--compression=None'

A screenshot of this is at:

[http://home.socal.rr.com/grandcanyon/gscan2pdf.png](http://home.socal.rr.com/grandcanyon/gscan2pdf.png)

I started gscan2pdf from a terminal window and after attempting to scan in lineart mode, the following is shown in the terminal window:

Unknown message: scanimage: unrecognized option `--compression=None'
sh: gocr: not found
sh: gocr: not found

I was able to scan in grayscale mode but after the scan, a dialog appears with the message:

Running OCR...

I don't use gscan2pdf for OCR and am not sure why this dialog appears.

I tried some scans with xsane and did not encounter any problems.

Thanks

Bob Anderson

---

### Post by mrojas73 on 2007-04-29
> **noynac said:**
> Jeffrey,

Thanks for the new version. 

I tried a few test scans on my Epson 3490 scanner. When scanning in lineart mode, I get a dialog with the message:

Unknown message: scanimage: unrecognized option `--compression=None'

A screenshot of this is at:

[http://home.socal.rr.com/grandcanyon/gscan2pdf.png](http://home.socal.rr.com/grandcanyon/gscan2pdf.png)

I started gscan2pdf from a terminal window and after attempting to scan in lineart mode, the following is shown in the terminal window:

Unknown message: scanimage: unrecognized option `--compression=None'
sh: gocr: not found
sh: gocr: not found

I was able to scan in grayscale mode but after the scan, a dialog appears with the message:

Running OCR...

I don't use gscan2pdf for OCR and am not sure why this dialog appears.

I tried some scans with xsane and did not encounter any problems.

Thanks

Bob Anderson

I have an HP ScanJet 6350C and I get the same error when I select lineart. No problems in any other mode.  

I want to thank Jeffrey for his wonderful work, thanks to his work I was able to finally dump Windows.  

Jeffrey, do you have a Paypal account, I would love to make a little donation to your project.

---

### Post by JeffreyRatcliffe on 2007-04-29
> **noynac said:**
> I tried a few test scans on my Epson 3490 scanner. When scanning in lineart mode, I get a dialog with the message:

Unknown message: scanimage: unrecognized option `--compression=None'

Yes. This is a problem for several people. I'll get a bug fix out ASAP.

> **noynac said:**
> sh: gocr: not found
sh: gocr: not found

I was able to scan in grayscale mode but after the scan, a dialog appears with the message:

Running OCR...

I don't use gscan2pdf for OCR and am not sure why this dialog appears.

I seem not to have properly turned off the OCR stack when gocr is not installed. I'll fix this ASAP too.

---

### Post by JeffreyRatcliffe on 2007-04-29
> **mrojas73 said:**
> thanks to his work I was able to finally dump Windows.

That alone makes it worthwhile!  

> **mrojas73 said:**
> Jeffrey, do you have a Paypal account, I would love to make a little donation to your project.

There is a donate button on the website, and also on the project page on Sourceforge. Thanks!

---

### Post by Whoopie on 2007-04-29
Hi Jeffrey,

I found the following on your side:
> 
Why doesn't Email to PDF work with Thunderbird?

Because Thunderbird doesn't support creating new emails with attachments.


This is not quite correct. Thunderbird is able to create new mails with attachments.

Here an example:
mozilla-thunderbird -compose to=test@test.com,"attachment='file:///tmp/test.txt'"


Best regards,
Whoopie

---

### Post by mrojas73 on 2007-04-29
> **JeffreyRatcliffe said:**
> That alone makes it worthwhile!  



There is a donate button on the website, and also on the project page on Sourceforge. Thanks!

Done, I can't tell you how much I appreciate your work.  Please keep it up!

I updated my system to Feisty today and Gscan2pdf works great...I just can't scan on linearart but that's an issue I already had in Edgy after the last release of the software.

Thank you again.

---

### Post by JeffreyRatcliffe on 2007-04-30
> **Whoopie said:**
> I found the following on your side:

This is not quite correct. Thunderbird is able to create new mails with attachments.

Here an example:
mozilla-thunderbird -compose to=test@test.com,"attachment='file:///tmp/test.txt'"

I have tried to keep gscan2pdf desktop-agnostic. Therefore, when the ability to create a PDF and attach it to an email, I picked xdg-utils (xdg-email in this case) to do the attaching for me.

xdg-email checks which desktop is being used, and uses gnome-open, kde-open or exo-open. Unfortunately, it seems that none of these will create a new mail in Thunderbird with an attachment (see [http://lists.freedesktop.org/archives/portland/2006-November/000871.html)](http://lists.freedesktop.org/archives/portland/2006-November/000871.html)).

If you can show me how to check whether Thunderbird is the default mail client, I can use the code you posted.

---

### Post by JeffreyRatcliffe on 2007-04-30
Following the open source edict of "Release early, release often", I have uploaded version 0.9.9 of my utility gscan2pdf to [http://sourceforge.net/projects/gscan2pdf](http://sourceforge.net/projects/gscan2pdf).

I have every intention of developing it into a fully-fledged application, so please as much constructive feedback as you like.

Here's my immediate todo list:

1. Crop & autocrop

Have fun!

Changes:
+ Fixed Fixed bug 1709377 ("Unknwn msg: scanimage: unrec'd option --compression=None'")
+ Fixed bug where attempt to run gocr after scanning despite not being installed
+ Replaced about MessageDialog with AboutDialog
+ Update to Russian translation (thanks to Alexandre Prokoudine)
+ Update to Czech translation (thanks to Petr Jelínek)
+ Update to Dutch translation (thanks to Eric Spierings)
+ Packed unpaper options into Gtk2::Notebook to make dialog shorter, fixed bug 1709379 ("unpaper-0.2 dialog too tall for 1024x768")

Just add the following line to your /etc/apt/sources.list:```
deb http://gscan2pdf.sourceforge.net/download/debian binary/
```
If you are you are using Synaptic, then use menu Edit/Reload Package Information, search for gscan2pdf in the package list, and lo and behold, you can install the nice shiny new version automatically.

From the command line:```
sudo apt-get update
sudo apt-get install gscan2pdf
```

The dependencies are libgtk2-perl (>= 1:1.043-1), libgtk2-ex-simple-list-perl, perlmagick, libpdf-api2-perl, liblocale-gettext-perl (>= 1.05), libsane, sane-utils, libtiff-tools.

The help will require Gtk2::Ex::PodViewer. Rotating requires Imagemagick. The scanadf frontend is in sane. For Email as PDF, you need xdg-utils. OCR requires gocr. Having installed gscan2pdf, locate the gscan2pdf entry in Synaptic, right-click it and you can install them under "Recommends".

If anybody fancies translating gscan2pdf into any other languages, they are welcome to do so on Rosetta ([https://launchpad.net/products/gscan2pdf/trunk/+pots/gscan2pdf](https://launchpad.net/products/gscan2pdf/trunk/+pots/gscan2pdf))

Please let me know what you think/how you get on, particularly with the OCR & unpaper support. Is this how you want it handled? Improvements to the GUI?

---

### Post by mrojas73 on 2007-04-30
Just updated to 0.9.9 and it is working great for me, 0 errors.  Now I can scan on lineart.

---

### Post by noynac on 2007-04-30
Thanks for the quick fix. The problems I cited above are all taken care of.

As an aside, I noticed that the new brightness setting has no impact on lineart. Is this intentional? On occasion, I scan colored items (such as handwriting with a blue pen) in lineart mode and it comes out too light. A brightness setting that affects this would be very helpful.

Thanks again!

---

### Post by JeffreyRatcliffe on 2007-05-01
> **noynac said:**
> As an aside, I noticed that the new brightness setting has no impact on lineart. Is this intentional? On occasion, I scan colored items (such as handwriting with a blue pen) in lineart mode and it comes out too light. A brightness setting that affects this would be very helpful.

scanimage/scanadf and the backend that your scanner uses are responsible for the scan quality. ```
scanimage --help
``` will give you the options that your backend supports (these differ from scanner to scanner). Perhaps contrast or something similar is the option you need. Try playing with the options on the command line and looking at the result (gscan2pdf will import the scan from a file). If you find you want an extra option, tell me and I'll include it in gscan2pdf.

---

### Post by noynac on 2007-05-01
Jeffrey,

I ran scanimage --help but my knowledge of this topic was not sufficient to make any sense of it. So, I instead decided to run some tests with Xsane in lineart mode. My test document contained printed black text plus text handwritten with a blue pen. A screen shot of Xsane at the time of the test is:

[http://home.socal.rr.com/grandcanyon/screen.png](http://home.socal.rr.com/grandcanyon/screen.png)

I first scanned the test document with halftoning unchecked and the threshold set at 50% then 25% and 75%. The scanned documents in PDF format are:

[http://home.socal.rr.com/grandcanyon/TH-50.pdf](http://home.socal.rr.com/grandcanyon/TH-50.pdf)

[http://home.socal.rr.com/grandcanyon/TH-25.pdf](http://home.socal.rr.com/grandcanyon/TH-25.pdf)

[http://home.socal.rr.com/grandcanyon/TH-75.pdf](http://home.socal.rr.com/grandcanyon/TH-75.pdf)

As you can see, the threshold setting made a significant different. At the default setting of 50%, the blue text is light but visible and is pretty much how the document looks when scanned in gscan2pdf. With a little experimentation, I found that 60% yielded a document that was pretty accurate to the original and is the setting I would probably use for this type of document. 

I then put a checkmark next to halftoning and ran numerous tests with various gamma, brightness, and contrast settings. They all had no impact on the scanned document.

So, threshold seems to be the important setting in lineart mode. Can this be incorporated in gscan2pdf?

BTW, my scanner is an Epson Perfection 3490 and I'm running Ubutnu 6.10. Gscan2pdf is set to use scanimage. 

Thanks

---

### Post by JeffreyRatcliffe on 2007-05-01
> **noynac said:**
> I ran scanimage --help but my knowledge of this topic was not sufficient to make any sense of it.

If I recall, you have sent me your --help output before. This seems to be the relevant part:

```
    --threshold 0..100% (in steps of 1) [inactive]
        Select minimum-brightness to get a white point
    --brightness -400..400% (in steps of 1) [0]
        Controls the brightness of the acquired image.
    --contrast -100..400% (in steps of 1) [0]
        Controls the contrast of the acquired image.
```

The strange thing is that the --threshold option is inactive. I'll add that and --contrast to the next release.

---

### Post by noynac on 2007-05-01
> **JeffreyRatcliffe said:**
> If I recall, you have sent me your --help output before....

I checked and that's correct. I just emailed you a new output from scanimage --help. Thanks!

---

### Post by unconquerable on 2007-05-04
My oh my my thread has grown, I haven't been around for a while, but if anyone wants to PM me a summary of with links of the thread so far, I will place it in my first post.  If not I will make one when I get the time.

---

### Post by snobel on 2007-05-10
Hi Jeffrey,

First, thanks for providing this program. I was afraid that ubuntu's support for my fujitsu scansnap ADF scanner would be very basic. Not so!

I'd like to second the [request]("http://sourceforge.net/tracker/index.php?func=detail&aid=1708036&group_id=174140&atid=868101")   (well it's your own suggestion actually) for the ability to convert pages to jpegs before storing them in a pdf. This is how the original scansnap software does it, and it is very convenient for scanning e.g. magazines where the image quality is not essential. 

As a generalisation, would it be possible to add a way to run a user defined command or script on each page, before storing it in the pdf? That would be very powerful...

I have made a translation to Danish based on the 0.9.6 template. Should I upload the .po file on the rosetta site, or will an updated template become available?

Lastly, a call for help. Somewhat OT, but I think there may be a doctor in the audience... I upgraded from edgy to feisty, and now my scansnap fi-5110eox2 turns itself off about 10 seconds after being turned on. :confused: If I hit the scan button in gscan2pdf at the same moment I turn it on, then it is 'there' just long enough to be recognised. It still works as before if I boot on the edgy kernel, but I am counting on the new virtualisation features to help me leave the dark side, so it's quite a drawback. 
Did any other scansnap owners out there have similar problems with feisty?

---

### Post by JeffreyRatcliffe on 2007-05-10
> **snobel said:**
> As a generalisation, would it be possible to add a way to run a user defined command or script on each page, before storing it in the pdf? That would be very powerful...

If you give me an example script, I'll have a look at it.

> **snobel said:**
> I have made a translation to Danish based on the 0.9.6 template. Should I upload the .po file on the rosetta site, or will an updated template become available?

Thanks! I don't know why Rosetta has stopped importing my templates. I've attached my current one. Please upload the translation to Rosetta. Incidentally, I find it easier to do the translations directly on Rosetta because of the examples you get from other packages.

---

### Post by snobel on 2007-05-10
> **JeffreyRatcliffe said:**
> If you give me an example script, I'll have a look at it.
The only thing I need is conversion to jpeg (for jpegs-in-pdf) so if you are going to support that in-program, then I'm fine. :) The script idea was more of a 'future expansion' thing, in case you need the gimp or a lot of imagemagick.

> **JeffreyRatcliffe said:**
> Please upload the translation to Rosetta. Incidentally, I find it easier to do the translations directly on Rosetta because of the examples you get from other packages.
I couldn't upload, so the .po file is attached. Is it possible to do the editing on the site? A short how-to for translator-wannabes would be good...

---

### Post by JeffreyRatcliffe on 2007-05-11
> **snobel said:**
> The only thing I need is conversion to jpeg (for jpegs-in-pdf) so if you are going to support that in-program, then I'm fine. :) The script idea was more of a 'future expansion' thing, in case you need the gimp or a lot of imagemagick.

It's a good idea. I'll look at adding it.

> **snobel said:**
> I couldn't upload, so the .po file is attached. Is it possible to do the editing on the site? A short how-to for translator-wannabes would be good...

I've uploaded the .po. You should be able to see it as soon as it has gone through the import queue.

To edit on Rosetta
[LIST=1]
[*]obviously, you'll need a Launchpad user first.
[*]you should set up your preferred languages in your user settings.
[*]go to the list of translations [https://launchpad.net/gscan2pdf/+translations](https://launchpad.net/gscan2pdf/+translations)
[*]click on the language you want to translate, and Bob's your uncle!
[/LIST]

---

### Post by snobel on 2007-05-11
> **JeffreyRatcliffe said:**
> To edit on Rosetta
[LIST=1]
[*]obviously, you'll need a Launchpad user first.
[*]you should set up your preferred languages in your user settings.
[*]go to the list of translations [https://launchpad.net/gscan2pdf/+translations](https://launchpad.net/gscan2pdf/+translations)
[*]click on the language you want to translate, and Bob's your uncle!
[/LIST]
I just tried it out. You're right, that is much easier.

---

### Post by JeffreyRatcliffe on 2007-06-05
Following the open source edict of "Release early, release often", I have uploaded version 0.9.10 of my utility gscan2pdf to [http://sourceforge.net/projects/gscan2pdf](http://sourceforge.net/projects/gscan2pdf).

I have every intention of developing it into a fully-fledged application, so please as much constructive feedback as you like.

Changes:
+ patch credits
+ Switched rotate icons from Crystal (KDE) to those stolen from Eye of Gnome
+ Closed bug 1712967
  (long lines in ocr output resized document display off screen)
+ contrast and threshold controls
+ handle PNG, JPEG, GIF, PNM natively,
   closing feature request 1708448 (JPG to PDF)
   and bugs 1714874 (import b/w pdf problem)
   and 1669413 (Problem with "callback")
+ PDF compression options (JPEG, PNG), closing feature request 1708036
+ --speed option (Epson 1200)
+ ProgressBar for PDF save, closing feature request 1712964
+ Portuguese translation (thanks to Hugo Pereira)
+ Danish translation (thanks to Jacob Nielsen)
+ Update to Czech translation (thanks to Petr Jelínek)
+ Update to Dutch translation (thanks to Eric Spierings)
+ Update to French translation (thanks to codL)
+ remembers OCR on scan setting
+ unpaper on scan
+ calibration-cache option for Canon LiDE25
+ roadmap to website/help

Just add the following line to your /etc/apt/sources.list:```
deb http://gscan2pdf.sourceforge.net/download/debian binary/
```
If you are you are using Synaptic, then use menu Edit/Reload Package Information, search for gscan2pdf in the package list, and lo and behold, you can install the nice shiny new version automatically.

From the command line:```
sudo apt-get update
sudo apt-get install gscan2pdf
```

The dependencies are libgtk2-perl (>= 1:1.043-1), libgtk2-ex-simple-list-perl, perlmagick, libpdf-api2-perl, liblocale-gettext-perl (>= 1.05), libsane, sane-utils, libtiff-tools.

The help will require Gtk2::Ex::PodViewer. Rotating requires Imagemagick. The scanadf frontend is in sane. For Email as PDF, you need xdg-utils. OCR requires gocr. Having installed gscan2pdf, locate the gscan2pdf entry in Synaptic, right-click it and you can install them under "Recommends".

If anybody fancies translating gscan2pdf into any other languages, they are welcome to do so on Rosetta ([https://launchpad.net/products/gscan2pdf/trunk/+pots/gscan2pdf](https://launchpad.net/products/gscan2pdf/trunk/+pots/gscan2pdf))

---

### Post by noynac on 2007-06-05
I installed the new version, and I get the following message whenever I try to scan something in lineart mode: 
"Unknown message: scanimage: attempted to set inactive option contrast." This occurs even if I have not changed the brightness or contrast (both are set at 0). When I scan in color mode, everything works fine, and the brightness and contrast controls work as I would expect.

I'm running Ubuntu 6.10 with an Epson 3490 scanner. 

BTW, based on the version history, I was expecting to see a threshold control. Am I missing something?

---

### Post by JeffreyRatcliffe on 2007-06-06
> **noynac said:**
> I installed the new version, and I get the following message whenever I try to scan something in lineart mode: 
"Unknown message: scanimage: attempted to set inactive option contrast." This occurs even if I have not changed the brightness or contrast (both are set at 0). When I scan in color mode, everything works fine, and the brightness and contrast controls work as I would expect.

Oh dear. It looks as though the contrast option depends on the mode. The option isn't available on my OfficeJet, so I couldn't test it. The tricky thing is that there is nothing in the --help output to indicate when the option can be used.

Does anybody have a contrast option that works with lineart?

If not, I could disable the combination, i.e. if lineart is selected, then contrast is greyed out. Otherwise, I'll could add a checkbox for each option to manually disable them individually.

> **noynac said:**
> BTW, based on the version history, I was expecting to see a threshold control. Am I missing something?

Your scanimage --help lists the threshold option for your scanner as inactive, so gscan2pdf doesn't use it:

```
    --threshold 0..100% (in steps of 1) [inactive]
        Select minimum-brightness to get a white point
```

---

### Post by snobel on 2007-06-06
> **JeffreyRatcliffe said:**
> Does anybody have a contrast option that works with lineart?
It works with my HP scanjet 5300c. (scanimage --help output attached, just in case.)

---

### Post by JeffreyRatcliffe on 2007-06-06
> **snobel said:**
> It works with my HP scanjet 5300c. (scanimage --help output attached, just in case.)

Thanks for that.

> **noynac said:**
> "Unknown message: scanimage: attempted to set inactive option contrast."

Does it still carry out the scan?

---

### Post by noynac on 2007-06-06
> **JeffreyRatcliffe said:**
> ...Does it still carry out the scan?

No it doesn't. I am unable to scan the document, and I have to exit gscan2pdf.

---

### Post by noynac on 2007-06-06
> **JeffreyRatcliffe said:**
> ...Your scanimage --help lists the threshold option for your scanner as inactive, so gscan2pdf doesn't use it:
```
    --threshold 0..100% (in steps of 1) [inactive]
        Select minimum-brightness to get a white point
```

I ran "scanimage --help" and then "scanimage --mode=Lineart --help." This shows the differing enhancement options available in color and lineart modes.

~~~

bob@dell:~$ scanimage --help
Usage: scanimage [OPTION]...

Start image acquisition on a scanner device and write PNM image data to
standard output.

<snip>

Options specific to device `snapscan:libusb:005:004':
  Scan Mode:
    --resolution auto||50|150|200|240|266|300|350|360|400|600|720|800|1200|1600|3200dpi [300]
        Sets the resolution of the scanned image.
    --preview[=(auto|yes|no)] [no]
        Request a preview-quality scan.
    --mode auto|Color|Gray|Lineart [Color]
        Selects the scan mode (e.g., lineart, monochrome, or color).
    --preview-mode auto|Auto|Color|Gray|Lineart [Auto]
        Select the mode for previews. Greyscale previews usually give the best
        combination of speed and detail.
    --high-quality[=(auto|yes|no)] [no]
        Highest quality but lower speed
    --source auto|Flatbed|Transparency Adapter [Flatbed]
        Selects the scan source (such as a document-feeder).

<snip> 

  Enhancement:
    --depth 8|16bit [8]
        Number of bits per sample, typical values are 1 for "line-art" and 8
        for multibit scans.
    --quality-cal[=(yes|no)] [yes]
        Do a quality white-calibration
    --halftoning[=(yes|no)] [inactive]
        Selects whether the acquired image should be halftoned (dithered).
    --halftone-pattern DispersedDot8x8|DispersedDot16x16 [inactive]
        Defines the halftoning (dithering) pattern for scanning halftoned
        images.
    --custom-gamma[=(yes|no)] [no]
        Determines whether a builtin or a custom gamma-table should be used.
    --analog-gamma-bind[=(yes|no)] [no]
        In RGB-mode use same values for each color
    --analog-gamma 0..4 [inactive]
        Analog gamma-correction
    --analog-gamma-r 0..4 [1.79999]
        Analog gamma-correction for red
    --analog-gamma-g 0..4 [1.79999]
        Analog gamma-correction for green
    --analog-gamma-b 0..4 [1.79999]
        Analog gamma-correction for blue
    --gamma-table 0..65535,... (in steps of 1) [inactive]
        Gamma-correction table.  In color mode this option equally affects the
        red, green, and blue channels simultaneously (i.e., it is an intensity
        gamma table).
    --red-gamma-table 0..65535,... (in steps of 1) [inactive]
        Gamma-correction table for the red band.
    --green-gamma-table 0..65535,... (in steps of 1) [inactive]
        Gamma-correction table for the green band.
    --blue-gamma-table 0..65535,... (in steps of 1) [inactive]
        Gamma-correction table for the blue band.
    --negative[=(auto|yes|no)] [inactive]
        Swap black and white
    --threshold 0..100% (in steps of 1) [inactive]
        Select minimum-brightness to get a white point
    --brightness -400..400% (in steps of 1) [0]
        Controls the brightness of the acquired image.
    --contrast -100..400% (in steps of 1) [0]
        Controls the contrast of the acquired image.
<snip> 

~~~

bob@dell:~$ scanimage --mode=Lineart --help
Usage: scanimage [OPTION]...

Start image acquisition on a scanner device and write PNM image data to
standard output.

<snip> 

Options specific to device `snapscan:libusb:005:004':
  Scan Mode:
    --resolution auto||50|150|200|240|266|300|350|360|400|600|720|800|1200|1600|3200dpi [300]
        Sets the resolution of the scanned image.
    --preview[=(auto|yes|no)] [no]
        Request a preview-quality scan.
    --mode auto|Color|Gray|Lineart [Lineart]
        Selects the scan mode (e.g., lineart, monochrome, or color).
    --preview-mode auto|Auto|Color|Gray|Lineart [Auto]
        Select the mode for previews. Greyscale previews usually give the best
        combination of speed and detail.
    --high-quality[=(auto|yes|no)] [no]
        Highest quality but lower speed
    --source auto|Flatbed|Transparency Adapter [Flatbed]
        Selects the scan source (such as a document-feeder).

<snip> 

  Enhancement:
    --depth 8|16bit [inactive]
        Number of bits per sample, typical values are 1 for "line-art" and 8
        for multibit scans.
    --quality-cal[=(yes|no)] [yes]
        Do a quality white-calibration
    --halftoning[=(yes|no)] [no]
        Selects whether the acquired image should be halftoned (dithered).
    --halftone-pattern DispersedDot8x8|DispersedDot16x16 [inactive]
        Defines the halftoning (dithering) pattern for scanning halftoned
        images.
    --custom-gamma[=(yes|no)] [inactive]
        Determines whether a builtin or a custom gamma-table should be used.
    --analog-gamma-bind[=(yes|no)] [inactive]
        In RGB-mode use same values for each color
    --analog-gamma 0..4 [inactive]
        Analog gamma-correction
    --analog-gamma-r 0..4 [inactive]
        Analog gamma-correction for red
    --analog-gamma-g 0..4 [inactive]
        Analog gamma-correction for green
    --analog-gamma-b 0..4 [inactive]
        Analog gamma-correction for blue
    --gamma-table 0..65535,... (in steps of 1) [inactive]
        Gamma-correction table.  In color mode this option equally affects the
        red, green, and blue channels simultaneously (i.e., it is an intensity
        gamma table).
    --red-gamma-table 0..65535,... (in steps of 1) [inactive]
        Gamma-correction table for the red band.
    --green-gamma-table 0..65535,... (in steps of 1) [inactive]
        Gamma-correction table for the green band.
    --blue-gamma-table 0..65535,... (in steps of 1) [inactive]
        Gamma-correction table for the blue band.
    --negative[=(auto|yes|no)] [no]
        Swap black and white
    --threshold 0..100% (in steps of 1) [50]
        Select minimum-brightness to get a white point
    --brightness -400..400% (in steps of 1) [inactive]
        Controls the brightness of the acquired image.
    --contrast -100..400% (in steps of 1) [inactive]
        Controls the contrast of the acquired image.

<snip>

---

### Post by SneakPeak on 2007-06-06
Hi I followed your instructions but I get the following error:

Failed to fetch [http://gscan2pdf.sourceforge.net/download/debain/binary/Packages.gz](http://gscan2pdf.sourceforge.net/download/debain/binary/Packages.gz)  404 Not Found

Any suggestions?

SneakPeak

---

### Post by SneakPeak on 2007-06-06
Ok so I am a noob,

I managed to download gscan2 pdf.  I can't get it to install becuase it is now complaining that it needs libgtk2-ex-simple-list and I can't get that to install either.

Help Please I really want to use this utility!!!

Adrian

---

### Post by JeffreyRatcliffe on 2007-06-06
> **noynac said:**
> I ran "scanimage --help" and then "scanimage --mode=Lineart --help." This shows the differing enhancement options available in color and lineart modes.

I'd not thought of trying that. OK. I'll have to update the device-dependent options so that they are mode-, as well as device-dependent.

Thanks for pointing me in the right direction.

Jeff

---

### Post by JeffreyRatcliffe on 2007-06-06
> **SneakPeak said:**
> I managed to download gscan2 pdf.  I can't get it to install becuase it is now complaining that it needs libgtk2-ex-simple-list and I can't get that to install either.

If you are using Edgy or Feisty, then it is available straight from Synaptic. If you are on Dapper, then you can download it from the website ([http://sourceforge.net/project/showfiles.php?group_id=174140](http://sourceforge.net/project/showfiles.php?group_id=174140))

---

### Post by SneakPeak on 2007-06-07
> **rkh said:**
> I have cobbled together a little bash script that scans a set number of documents, converts them to ps and then to pdf. It was based upon a few different scripts I found on the web-sorry I can't give credit- with some changes due to the quirks of my scanner -HP laserjet 3020. I haven't gotten it to work perfectly yet-it screws up page order a bit when you scan in more than 10 pages at a time, but it works good enough for me. 

Anyway, I have attached the script. Don't open it in a folder where there are any pnm, ps or pdf files already-it gets confused. 
It uses  sane, imagemagick, zenity, and pdftk to take input in a nifty gtk window on the name of the final pdf, the resolution, and the number of pages to be scanned.
Keep in mind, I am a lawyer, not a programmer. This has worked for me. I hope someone finds it useful.

Howdy rkh,

I found it very useful. Thank you.  The reason it gets confused beyond 9 pages is that according to pdftk 10 comes before 2.  If that makes any sense.  So for example if you have 13 pages pdftk will order them 1,10,11,12,13,2,3,4-9.  I noticed this using pdftk on a windows system at work.  To fix it one would have to fix the way the files are named when they are scanned.  Can't think of a solution straight off.  If I come up with one I'll post it.

Thanks again

Adrian

---

### Post by SneakPeak on 2007-06-07
> **JeffreyRatcliffe said:**
> If you are using Edgy or Feisty, then it is available straight from Synaptic. If you are on Dapper, then you can download it from the website ([http://sourceforge.net/project/showfiles.php?group_id=174140](http://sourceforge.net/project/showfiles.php?group_id=174140))

Thansk Jeffrey,

I now have gscan2pdf installed.  It runs and scans pages as required but unfortunately hangs when I try to save as pdf.  In the terminal window in which I start gscan2pdf from I get the following message:

Exception 395: unable to open module file `/usr/local/lib/ImageMagick-6.3.4/modu les-Q16/coders/png.la': No such file or directory at /usr/bin/gscan2pdf line 149 2.
*** unhandled exception in callback:
***   Can't call method "val" on an undefined value at /usr/share/perl5/PDF/API2 /Resource/XObject/Image.pm line 105.
***  ignoring at /usr/bin/gscan2pdf line 700.
The program 'gscan2pdf' received an X Window System error.
This probably reflects a bug in the program.
The error was 'RenderBadPicture (invalid Picture parameter)'.
  (Details: serial 33156 error_code 180 request_code 154 minor_code 7)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

By the way it is definitely the png.la file that is missing the rest of the directory structure is there.  I see from a quick google search that I am not the only one with this problem but I can't find a solution so far.

Any ideas?

Thanks 

SneakPeak

---

### Post by JeffreyRatcliffe on 2007-06-08
> **SneakPeak said:**
> I now have gscan2pdf installed.  It runs and scans pages as required but unfortunately hangs when I try to save as pdf.  In the terminal window in which I start gscan2pdf from I get the following message:

Exception 395: unable to open module file `/usr/local/lib/ImageMagick-6.3.4/modu les-Q16/coders/png.la': No such file or directory at /usr/bin/gscan2pdf line 149 2.

This is a problem with ImageMagick. The scans come in as PNM and ImageMagick is used to convert them to PNG, which are embedded in the PDF. When you create the PDF, try setting the compression to "none", and confirm that you get a working (if very big) PDF. Can you also tell me which distro you are using. Do you get the error just with lineart, or also colour scans?

> **SneakPeak said:**
> *** unhandled exception in callback:
***   Can't call method "val" on an undefined value at /usr/share/perl5/PDF/API2 /Resource/XObject/Image.pm line 105.
***  ignoring at /usr/bin/gscan2pdf line 700.

This is the PDF API complaining that the PNG is invalid. I should trap the first error so that this second one doesn't happen.

> **SneakPeak said:**
> The program 'gscan2pdf' received an X Window System error.
This probably reflects a bug in the program.
The error was 'RenderBadPicture (invalid Picture parameter)'.
  (Details: serial 33156 error_code 180 request_code 154 minor_code 7)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

This is X windows complaining that the forked process creating the PDF has created an error.

> **SneakPeak said:**
> By the way it is definitely the png.la file that is missing the rest of the directory structure is there.  I see from a quick google search that I am not the only one with this problem but I can't find a solution so far.

This is missing from ImageMagick, not gscan2pdf.

---

### Post by mifi on 2007-06-08
> **knathraak said:**
> Hi,

One of the critical applications I have to boot to windows for is my scanner software's ability to scan directly to single or multi page PDF. I'm using an epson perfection 1670.

Is there a utility to do this for Ubuntu or for linux in general? If not, does anyone know of a utility that works well in wine that can do this?

Thanks in advance.Xsane does this really well for me. Look in Applications/Graphics/XSane. You can tell it to save pdf's.
I have an Epson Perfection 3200. XSane is using it better than the software I got with it for XP.

mifi

---

### Post by SneakPeak on 2007-06-08
> **JeffreyRatcliffe said:**
> This is a problem with ImageMagick. The scans come in as PNM and ImageMagick is used to convert them to PNG, which are embedded in the PDF. When you create the PDF, try setting the compression to "none", and confirm that you get a working (if very big) PDF. Can you also tell me which distro you are using. Do you get the error just with lineart, or also colour scans? 

Using "none" doesn't work the PDF is blank.  Using JPG does work and appears to give a pdf file, not a JPG file.  In terms of gscan2pdf I am using the latest one of sourcefoge.  In terms of Ubuntu I am using 6.06 with all the latest updates recommended by the "automatic update software" can't remember what it is called.  I have not tried colour scans only gray and line art.  If gray is colour then yes I get the same error with gray as with line art.



> This is the PDF API complaining that the PNG is invalid. I should trap the first error so that this second one doesn't happen.



This is X windows complaining that the forked process creating the PDF has created an error.



This is missing from ImageMagick, not gscan2pdf.

Yip I know it's an ImageMagick problem.  I am trying to find a way to fix it.  At first I compiled ImageMagick from source but then I noticed it is listed in the package manager so I tried to install it that way.  I am too much of a noob to understand which version of ImageMagick is now installed.

---

### Post by JeffreyRatcliffe on 2007-06-08
> **SneakPeak said:**
> Using "none" doesn't work the PDF is blank.

Do you get an error message if you do this after starting gscan2pdf from the command line?

> **SneakPeak said:**
> Using JPG does work and appears to give a pdf file, not a JPG file.

That's right. You get a PDF with the images embedded as JPGs.

> **SneakPeak said:**
> Yip I know it's an ImageMagick problem.  I am trying to find a way to fix it.  At first I compiled ImageMagick from source but then I noticed it is listed in the package manager so I tried to install it that way.  I am too much of a noob to understand which version of ImageMagick is now installed.

OK. Now I understand. It is picking up the version that you installed from source - installed to /usr/local - whereas the package manager would install it to /usr. I have a stock Feisty machine and my /usr/local has only empty directories. Once you have installed the ImageMagick version that is in /usr/local, the packaged one should be working.

---

### Post by rkh on 2007-06-11
> **SneakPeak said:**
> Howdy rkh,

I found it very useful. Thank you.  The reason it gets confused beyond 9 pages is that according to pdftk 10 comes before 2.  If that makes any sense.  So for example if you have 13 pages pdftk will order them 1,10,11,12,13,2,3,4-9.  I noticed this using pdftk on a windows system at work.  To fix it one would have to fix the way the files are named when they are scanned.  Can't think of a solution straight off.  If I come up with one I'll post it.

Thanks again

Adrian

I'm glad that you have found it useful.  I tend to use it when I am only scanning a few pages. For longer projects I use gscan2pdf. However, since I upgraded to 9.10 I can't save. I click on the pdf button and the program crashes. Running it from the command line gives me the following:

*** unhandled exception in callback:
***   Wrong TIFF Id '57599' (should be 42). at /usr/share/perl5/PDF/API2/Resource/XObject/Image/TIFF.pm line 407.
***  ignoring at /usr/bin/gscan2pdf line 700.
The program 'gscan2pdf' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadIDChoice (invalid resource ID chosen for this connection)'.
  (Details: serial 60430 error_code 14 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
The program 'gscan2pdf' received an X Window System error.
This probably reflects a bug in the program.
The error was 'RenderBadPicture (invalid Picture parameter)'.
  (Details: serial 60587 error_code 180 request_code 153 minor_code 10)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

Help! I love gscan2pdf! It fills-or mostly fills- a big gap in linux scanning. Most software seems focussed on images. This program does text really well.

---

### Post by JeffreyRatcliffe on 2007-06-11
> **rkh said:**
> However, since I upgraded to 9.10 I can't save. I click on the pdf button and the program crashes. Running it from the command line gives me the following:

*** unhandled exception in callback:
***   Wrong TIFF Id '57599' (should be 42). at /usr/share/perl5/PDF/API2/Resource/XObject/Image/TIFF.pm line 407.
***  ignoring at /usr/bin/gscan2pdf line 700.

Can you email the TIFF that caused this to ra28145 at users.sf.net, please? I'm not seeing this and I'd like to be able to reproduce it so I can sort out the bug.

---

### Post by SneakPeak on 2007-06-11
> **JeffreyRatcliffe said:**
> Do you get an error message if you do this after starting gscan2pdf from the command line?

Yes, I always start gscan2pdf from the command line.  I don't know how to start it otherwise.

---

### Post by JeffreyRatcliffe on 2007-06-11
> **SneakPeak said:**
> Yes, I always start gscan2pdf from the command line.  I don't know how to start it otherwise.

So saving a PDF with compression=none gives you an empty PDF and no error message?

gscan2pdf creates a randomly named temporary directory, probably in /tmp. If all you have done is scanned in 1 page and tried to save a PDF with compression=none, then there should just be 1 file in this temporary directory. If you email it to ra28145 at users.sf.net, then I'll take a look at why it is producing a blank PDF.

If you are using Gnome, then installing gscan2pdf from the .deb or from Synaptic gives you a menu item in Applications/Graphics.

---

### Post by BathroomNinja on 2007-06-12
YES! Thank you so much for writing this.  This program is a life saver.  Works FLAWLESSLY on my HP Officeject 7210 All In One.  This includes actually using my ADF without a hitch.  I've never before been able to use my ADF in linux without issues.  Thank you for your efforts.

-BN

---

### Post by JeffreyRatcliffe on 2007-06-12
> **JeffreyRatcliffe said:**
> I'd not thought of trying that. OK. I'll have to update the device-dependent options so that they are mode-, as well as device-dependent.

I've now done this, but as options in lineart, grey and colour modes are the same on my scanner, I can only do limited testing.

I'm looking for a couple of brave souls to test this before it release it properly. Download the attachment and install it with:

```
sudo dpkg -i gscan2pdf-0.9.11rc1_all.deb
```

Thanks for any feedback.

---

### Post by noynac on 2007-06-12
I installed the test version, but I've encountered the same problems as before, except now the scanner will not work in color mode either. The following are screenshots of the error messages I receive first in lineart then color mode:

[http://home.socal.rr.com/grandcanyon/gscan-lineart.png](http://home.socal.rr.com/grandcanyon/gscan-lineart.png)

[http://home.socal.rr.com/grandcanyon/gscan-color.png](http://home.socal.rr.com/grandcanyon/gscan-color.png)

BTW, if I close the error-message dialog, the scan is not completed. 

BTW (2), when I first installed the test version with the mode set at lineart, the contrast and brightness settings were grayed out. With subsequent scans, this was no longer the case, as you can see from the screenshots. 

I'm running Ubuntu 6.10, and my scanner is an Epson 3490.

---

### Post by mrojas73 on 2007-06-12
> **BathroomNinja said:**
> YES! Thank you so much for writing this.  This program is a life saver.  Works FLAWLESSLY on my HP Officeject 7210 All In One.  This includes actually using my ADF without a hitch.  I've never before been able to use my ADF in linux without issues.  Thank you for your efforts.

-BN

I feel the same way, lets not forget to help Jeffrey out with some donations.  Lets not just love the free, lets love the freedom!

---

### Post by JeffreyRatcliffe on 2007-06-13
> **noynac said:**
> BTW (2), when I first installed the test version with the mode set at lineart, the contrast and brightness settings were grayed out. With subsequent scans, this was no longer the case, as you can see from the screenshots.

I think I've nailed it now. I'll upload another test release tonight.

---

### Post by JeffreyRatcliffe on 2007-06-13
> **noynac said:**
> I installed the test version, but I've encountered the same problems as before, except now the scanner will not work in color mode either.

OK. Try this:

```
sudo dpkg -i gscan2pdf-0.9.11rc2_all.deb
```

Thanks for any feedback.

---

### Post by noynac on 2007-06-13
> **JeffreyRatcliffe said:**
> OK. Try this:

```
sudo dpkg -i gscan2pdf-0.9.11rc2_all.deb
```

Thanks for any feedback.
Last night, I upgraded to Feisty, which broke many items including the reliable functioning of my scanner. I think I have that fixed now, but I have other issues to resolve. I'll give the new version of gscan2pdf a try tomorrow and report back. Thanks for the great work--I look forward to getting everything working correctly.

---

### Post by SneakPeak on 2007-06-14
> **JeffreyRatcliffe said:**
> So saving a PDF with compression=none gives you an empty PDF and no error message?

gscan2pdf creates a randomly named temporary directory, probably in /tmp. If all you have done is scanned in 1 page and tried to save a PDF with compression=none, then there should just be 1 file in this temporary directory. If you email it to ra28145 at users.sf.net, then I'll take a look at why it is producing a blank PDF.

If you are using Gnome, then installing gscan2pdf from the .deb or from Synaptic gives you a menu item in Applications/Graphics.

Hi Jeffery

Yes saving as PDF with compression=none does give a blank pdf.  I have emailed the details through to you.

I found gscan2pdf in the Gnome menu, Thanks

SneakPeak

---

### Post by kry10 on 2007-06-14
Hello Jeffery, et.al.

I just discovered gscan2pdf, and it looks fantastic! I've been looking for a Linux tool to scan paper documents, OCR them, and save them as "searchable" PDFs, and this works almost perfectly.

However, I'm wondering if there's a way to control the compression level that gscan2pdf uses when saving a PDF. For example, I used gscan2pdf to scan a letter size document, OCR it, and save as a PDF using JPEG compression. That file was about 3.4 MB in size. Then, I took the document to my Windows machine at work, and optimized it using PDF Optimizer. The new file was only 183.1 KB in size.

From what I can figure out, it looks like Adobe's PDF Optimizer reduced the dpi from the original 300 to 150, and used a "low" quality setting for the JPEG compression. No, the quality isn't as good as the original, but it's very close, certainly good enough for archival purposes. It also kept the searchable meta data. Being able to compress the file size that much (almost 19x by my calculations) would be very advantageous!

So what do you think? Is this even possible in gscan2pdf? Thanks!

Mark

---

### Post by JeffreyRatcliffe on 2007-06-14
> **kry10 said:**
> However, I'm wondering if there's a way to control the compression level that gscan2pdf uses when saving a PDF. For example, I used gscan2pdf to scan a letter size document, OCR it, and save as a PDF using JPEG compression. That file was about 3.4 MB in size. Then, I took the document to my Windows machine at work, and optimized it using PDF Optimizer. The new file was only 183.1 KB in size.

I've just implemented a quality/compression setting for embedded JPEGs. Somebody else has also asked for a downsampling option, and this I will do soon.

Thanks for the donation!

---

### Post by noynac on 2007-06-14
I tried the new test version and still have some issues. 

Gscan gives an error message when mode is set to lineart, as shown in the following screenshot. 

[http://home.socal.rr.com/grandcanyon/gscan1.png](http://home.socal.rr.com/grandcanyon/gscan1.png)

I switched gscan to color mode and tried to scan. I got an error message as shown in the following screen shot. Note that the threshold setting is not grayed out. 

[http://home.socal.rr.com/grandcanyon/gscan2.png](http://home.socal.rr.com/grandcanyon/gscan2.png)

I switched mode to lineart (or perhaps grayscale) mode and then back to color, and I was able to do scans. The brightness and contrast adjustments both worked. Note that threshold is now grayed out. 

[http://home.socal.rr.com/grandcanyon/gscan3.png](http://home.socal.rr.com/grandcanyon/gscan3.png)

Thanks.

---

### Post by kry10 on 2007-06-14
> **JeffreyRatcliffe said:**
> I've just implemented a quality/compression setting for embedded JPEGs. Somebody else has also asked for a downsampling option, and this I will do soon.

Fantastic - thanks!

[QUOTE]Thanks for the donation![QUOTE]

Hey, great products should be supported - I just wish I could give more :)

---

### Post by JeffreyRatcliffe on 2007-06-15
> **noynac said:**
> Gscan gives an error message when mode is set to lineart, as shown in the following screenshot.

This looks to me like a problem with scanimage or the backend. Can you try switching frontend to scanadf in gscan2pdf? Also from the command line:

```
scanimage --mode=Lineart --threshold=50
```

and

```
scanadf --mode=Lineart --threshold=50
```

> **noynac said:**
> I switched gscan to color mode and tried to scan. I got an error message as shown in the following screen shot. Note that the threshold setting is not grayed out.

That's a bug. I'll look into it.

---

### Post by noynac on 2007-06-15
I changed the frontend to scanadf and tried a lineart scan. I received the same error message as before. Color scans worked fine. I did a screenshot if that would be helpful.

I entered the follwing command in a terminal window:

scanimage --mode=Lineart --threshold=50

I received the following text followed by pages of undecipherable characters in the terminal window, and the scanner then scanned the document:

# SANE data follows 
2544 3507

I then entered the following commmand

scanadf --mode=Lineart --threshold=50

The terminal window showed the following text and the scanner continued scanning the document until I exited the terminal window:

Scanned document image-0001
Scanned document image-0002

---

### Post by JeffreyRatcliffe on 2007-06-15
> **noynac said:**
> scanimage --mode=Lineart --threshold=50

I received the following text followed by pages of undecipherable characters in the terminal window, and the scanner then scanned the document:

So the backend doesn't like something about the options that gscan2pdf is feeding it, but --threshold in itself is OK. Please start gscan2pdf from the command line:

```
gscan2pdf --debug
```

and try to scan something with lineart. In the terminal window, you will see, amongst a load of other output, the scanimage command that gscan2pdf is using, something like:

```
scanimage --device-name='dev' --batch-count=1 --source='Flatbed' -l 0 -y 297 --threshold='50' --mode='Lineart' --resolution='150' -x 210 -t 0 --batch
```

Note it - copy it to a text editor or something, quit gscan2pdf and check that that command really does produce an error when you enter it in the command line.

Assuming it does, please try it again without all the inverted commas:

```
scanimage --batch-count=1 --source=Flatbed -l 0 -y 297 --threshold=50 --mode=Lineart --resolution=150 -x 210 -t 0 --batch
```

Sorry to have to get you to do the debugging remotely, but I can't reproduce it here...

---

### Post by noynac on 2007-06-15
The following is the text that appeared in the terminal window after starting gscan with the debug option:

scanimage --device-name='snapscan:libusb:005:003' --batch-count=1 --source='Flatbed' -l 0 -y 279.4 --threshold='50' --mode='Lineart' --resolution='300' -x 215.9 -t 0 --batch
Forked PID 14826
Unknown message: scanimage: attempted to set inactive option threshold

I entered the scanimage commmand (ending with --batch) in a terminal window and received the following:

bob@dell:~$ scanimage --device-name='snapscan:libusb:005:003' --batch-count=1 --source='Flatbed' -l 0 -y 279.4 --threshold='50' --mode='Lineart' --resolution='300' -x 215.9 -t 0 --batch
scanimage: attempted to set inactive option threshold

I then deleted all of the inverted commas and entered the following in a terminal window:

bob@dell:~$ scanimage --device-name=snapscan:libusb:005:003 --batch-count=1 --source=Flatbed -l 0 -y 279.4 --threshold=50 --mode=Lineart --resolution=300 -x 215.9 -t 0 --batch

I received the following:

scanimage: attempted to set inactive option threshold

---

### Post by JeffreyRatcliffe on 2007-06-15
> **noynac said:**
> bob@dell:~$ scanimage --batch-count=1 --source=Flatbed -l 0 -y 279.4 --threshold=50 --mode=Lineart --resolution=300 -x 215.9 -t 0 --batch

Perhaps the option order is important. Try:

```
scanimage --device-name=snapscan:libusb:005:003  --mode=Lineart --batch-count=1 --source=Flatbed -l 0 -y 279.4 --threshold=50 --resolution=300 -x 215.9 -t 0 --batch
```

---

### Post by noynac on 2007-06-15
I entered the following:

scanimage --device-name=snapscan:libusb:005:003  --mode=Lineart --batch-count=1 --source=Flatbed -l 0 -y 279.4 --threshold=50 --resolution=300 -x 215.9 -t 0 --batch

I received:

scanimage: open of device snapscan:libusb:005:003 failed: Invalid argument

I played around a bit and entered:

scanimage --mode=Lineart --batch-count=1 --source=Flatbed -l 0 -y 279.4 --threshold=50 --resolution=300 -x 215.9 -t 0 --batch

The scanner scanned and I received:

Scanning 1 pages, incrementing by 1, numbering from 1
Scanning page 1
Scanned page 1. (scanner status = 5)

I don't know what all this means.

---

### Post by JeffreyRatcliffe on 2007-06-15
> **noynac said:**
> scanimage --mode=Lineart --batch-count=1 --source=Flatbed -l 0 -y 279.4 --threshold=50 --resolution=300 -x 215.9 -t 0 --batch

It looks like it is the option order. Just to be certain, please try:

```
scanimage --mode=Lineart  --threshold=50 --batch
```

and then

```
scanimage --threshold=50 --mode=Lineart  --batch
```

---

### Post by noynac on 2007-06-15
The command...

bob@dell:~$ scanimage --mode=Lineart  --threshold=50 --batch

resulted in...

Scanning -1 pages, incrementing by 1, numbering from 1
Scanning page 1
Scanned page 1. (scanner status = 5)
Scanning page 2
Scanned page 2. (scanner status = 5)
Scanning page 3...

The command...

bob@dell:~$ scanimage --threshold=50 --mode=Lineart  --batch

resulted in...

scanimage: attempted to set inactive option threshold

Looking good :D

---

### Post by JeffreyRatcliffe on 2007-06-15
> **noynac said:**
> scanimage --threshold=50 --mode=Lineart  --batch

resulted in...

scanimage: attempted to set inactive option threshold

I've reported this as a bug with SANE and I will post another test release as soon as I have it ready.

---

### Post by noynac on 2007-06-15
--deleted posting--

---

### Post by JeffreyRatcliffe on 2007-06-18
> **noynac said:**
> $ scanimage --mode=Lineart  --threshold=50 --batch

Here is my next attempt.

---

### Post by noynac on 2007-06-18
I installed the new version. Gscan opened in lineart mode, and I was able to do lineart scans without any problem. The threshold control worked fine.

I then changed from lineart to color mode and noticed that threshold was not grayed out as expected. I clicked on the scan button and received the following error message:

Unknown message: scanimage: attempted to set inactive option threshold

I exited and restarted gscan. It opened in color mode and the threshold settings was grayed out. I did a scan, and it worked fine. I tried out the brightness/contrast settings, and they also seemed to work fine.

I then switched to gray mode and did a scan. Everything worked fine.

I then switched to lineart mode and threshold was grayed out. I was able to scan with difficulty. 

Later, after restarting my computer, I loaded gscan and tried to do a lineart scan. I got the following error message:

Unknown message: scanimage: open of device snapscan:libusb:005:002 failed: Invalid argument

~~~

Addition:

With the new version, all of my lineart scans are saved in reverse video. For example, see:

[http://home.socal.rr.com/grandcanyon/test.pdf](http://home.socal.rr.com/grandcanyon/test.pdf)

Color scans saved in PDF format are fine. Gray scans saved in PDF format are blank white pages.

I have been using version 0.9.4, so I don't know if this is a new or old problem.

---

### Post by JeffreyRatcliffe on 2007-06-19
> **noynac said:**
> Unknown message: scanimage: attempted to set inactive option threshold

I don't have your scanner, and in test mode, I can't reproduce this. Please start gscan2pdf with:

```
gscan2pdf --debug
```

and when you get this error, please email me (ra28145 at users.sf.net) the contents of the terminal window where you started gscan2pdf.

> **noynac said:**
> Later, after restarting my computer, I loaded gscan and tried to do a lineart scan. I got the following error message:

Unknown message: scanimage: open of device snapscan:libusb:005:002 failed: Invalid argument

I occassionally have problems like this, and it usually fixed by restarting the scanner.

> **noynac said:**
> With the new version, all of my lineart scans are saved in reverse video. For example, see:

[http://home.socal.rr.com/grandcanyon/test.pdf](http://home.socal.rr.com/grandcanyon/test.pdf)

Color scans saved in PDF format are fine. Gray scans saved in PDF format are blank white pages.

I have been using version 0.9.4, so I don't know if this is a new or old problem.

Before 0.9.10, all images were held as TIFFs. Now they are held in their native formats and only converted when necessary.

I assume that the scan looks OK in gscan2pdf? There is a known bug in the libperl-PDF-API2 library that means that for some scanners, if you use compression=none when making the PDF, the PDF comes out reversed. If you are using compression=PNG or JPEG, please find the offending .PNM file from your /tmp directory and email it to me: in this case it is a bug in imagemagick.

---

### Post by JeffreyRatcliffe on 2007-06-19
Following the open source edict of "Release early, release often", I have uploaded version 0.9.12 of my utility gscan2pdf to [http://sourceforge.net/projects/gscan2pdf](http://sourceforge.net/projects/gscan2pdf).

I have every intention of developing it into a fully-fledged application, so please as much constructive feedback as you like.

Changes:
+ no-grayfilter option
+ check for mode-dependent options.
+ note resolution info so that the resulting PDF has the correct paper size.
  Closes bug 1736036 (page size is somehow a ratio of resolution)
  and Debian bug 426525 (after unpaper, saving PDF causes magnified page)
+ quality setting for JPG compression in save as PDF.
  Closes feature request 1736043 (Compression setting)
  and bug 1736582 (PDFs with embedded JPEGS are large)
+ save image functionality supporting TIFF, PNG, JPEG, PNM & GIF.
  Closes feature request 1709380 (Support PNG output equivalent to TIFF)
+ save default dates as offset from current, closing bug 1736037
  (pdf file->save dialog should automatically set the date to the current day)
+ Update to Czech translation (thanks to Petr Jelínek)
+ update to German translation (thanks to Florian)
+ update to Portuguese translation (thanks to Hugo Pereira)
+ Update to Spanish translation (thanks to Raúl González Duque)

Just add the following line to your /etc/apt/sources.list:```
deb http://gscan2pdf.sourceforge.net/download/debian binary/
```
If you are you are using Synaptic, then use menu Edit/Reload Package Information, search for gscan2pdf in the package list, and lo and behold, you can install the nice shiny new version automatically.

From the command line:```
sudo apt-get update
sudo apt-get install gscan2pdf
```

The dependencies are libgtk2-perl (>= 1:1.043-1), libgtk2-ex-simple-list-perl, perlmagick, libpdf-api2-perl, liblocale-gettext-perl (>= 1.05), libsane, sane-utils, libtiff-tools.

The help will require Gtk2::Ex::PodViewer. Rotating requires Imagemagick. The scanadf frontend is in sane. For Email as PDF, you need xdg-utils. OCR requires gocr. Having installed gscan2pdf, locate the gscan2pdf entry in Synaptic, right-click it and you can install them under "Recommends".

If anybody fancies translating gscan2pdf into any other languages, they are welcome to do so on Rosetta ([https://launchpad.net/products/gscan2pdf/trunk/+pots/gscan2pdf](https://launchpad.net/products/gscan2pdf/trunk/+pots/gscan2pdf))

---

### Post by tcornishmn on 2007-06-23
I seem to be having a problem saving files.  Scanning appears to be fine, and when I click the save pdf icon I can choose a file location, but the application closes at that point.

Here's the debug output:

tj@Laptop:~$ gscan2pdf --debug
scanimage --help --device-name='avision:libusb:004:003' --mode Lineart
Forked PID 7325
Waiting to reap process at /usr/bin/gscan2pdf line 3111.
Reaped PID -1
Usage: scanimage [OPTION]...

Start image acquisition on a scanner device and write PNM image data to
standard output.

-d, --device-name=DEVICE   use a given scanner device (e.g. hp:/dev/scanner)
    --format=pnm|tiff      file format of output file
-i, --icc-profile=PROFILE  include this ICC profile into TIFF file
-L, --list-devices         show available scanner devices
-f, --formatted-device-list=FORMAT similar to -L, but the FORMAT of the output
                           can be specified: %d (device name), %v (vendor),
                           %m (model), %t (type), and %i (index number)
-b, --batch[=FORMAT]       working in batch mode, FORMAT is `out%d.pnm' or
                           `out%d.tif' by default depending on --format
    --batch-start=#        page number to start naming files with
    --batch-count=#        how many pages to scan in batch mode
    --batch-increment=#    increase number in filename by an amount of #
    --batch-double         increment page number by two for 2sided originals
                           being scanned in a single sided scanner
    --batch-prompt         ask for pressing a key before scanning a page
    --accept-md5-only      only accept authorization requests using md5
-p, --progress             print progress messages
-n, --dont-scan            only set options, don't actually scan
-T, --test                 test backend thoroughly
-h, --help                 display this help message and exit
-v, --verbose              give even more status messages
-B, --buffer-size          change default input buffersize
-V, --version              print version information

Options specific to device `avision:libusb:004:003':
  Scan mode:
    --mode Lineart|Dithered|Gray|Color [Lineart]
        Selects the scan mode (e.g., lineart, monochrome, or color).
    --resolution 50..600dpi (in steps of 5) [150]
        Sets the resolution of the scanned image.
    --speed 0..4 (in steps of 1) [inactive]
        Determines the speed at which the scan proceeds.
    --preview[=(yes|no)] [no]
        Request a preview-quality scan.
    --source ADF|ADF Rear|ADF Duplex [ADF]
        Selects the scan source (such as a document-feeder).
  Geometry:
    -l 0..216mm [0]
        Top-left x position of scan area.
    -t 0..362mm [0]
        Top-left y position of scan area.
    -x 0..216mm [216]
        Width of scan-area.
    -y 0..362mm [362]
        Height of scan-area.
  Enhancement:
    --brightness -100..100% (in steps of 1) [0]
        Controls the brightness of the acquired image.
    --contrast -100..100% (in steps of 1) [0]
        Controls the contrast of the acquired image.
    --quality-scan[=(yes|no)] [yes]
        Turn on quality scanning (slower but better).
    --quality-cal[=(yes|no)] [yes]
        Do a quality white-calibration
    --gamma-table 0..255,...
        Gamma-correction table.  In color mode this option equally affects the
        red, green, and blue channels simultaneously (i.e., it is an intensity
        gamma table).
    --red-gamma-table 0..255,... [inactive]
        Gamma-correction table for the red band.
    --green-gamma-table 0..255,... [inactive]
        Gamma-correction table for the green band.
    --blue-gamma-table 0..255,... [inactive]
        Gamma-correction table for the blue band.
    --frame 0..0 [inactive]
        Selects the number of the frame to scan
    --power-save-time <int> [15]
        Allows control of the scanner's power save timer, dimming or turning
        off the light.
    --nvram-values <string> [Vendor: XEROX   
Model: DocuMate252     
Firmware: 0.12
Manufacturing date: 0-0-0
First scan date: 2004-4-15
ADF simplex scans: 1976]
        Allows access obtaining the scanner's NVRAM values as pretty printed
        text.

Type ``scanimage --help -d DEVICE'' to get list of all options for DEVICE.

List of available devices:
    avision:libusb:004:003
scanimage --device-name='avision:libusb:004:003' --mode='Lineart' --source='ADF Duplex' --contrast='0' -x 215.9 -y 279.4 -l 0 --brightness='-18' --resolution='300' -t 0 --batch 
Forked PID 7378
scanimage: rounded value of brightness from -18 to -18
Waiting to reap process at /usr/bin/gscan2pdf line 2686.
Reaped PID 7378
Forked PID 7450
Exception 395: unable to open module file `/usr/lib/ImageMagick-6.2.4/modules-Q16/coders/zip.la': No such file or directory at /usr/bin/gscan2pdf line 1517.
*** unhandled exception in callback:
***   Wrong TIFF Id '8970' (should be 42). at /usr/share/perl5/PDF/API2/Resource/XObject/Image/TIFF.pm line 407.
***  ignoring at /usr/bin/gscan2pdf line 712.
The program 'gscan2pdf' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadIDChoice (invalid resource ID chosen for this connection)'.
  (Details: serial 29619 error_code 14 request_code 1 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
tj@Laptop:~$ The program 'gscan2pdf' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadIDChoice (invalid resource ID chosen for this connection)'.
  (Details: serial 29687 error_code 14 request_code 1 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
tj@Laptop:~$ 


Any ideas?  

Thanks,
TJ

---

### Post by JeffreyRatcliffe on 2007-06-24
> **tcornishmn said:**
> I seem to be having a problem saving files.  Scanning appears to be fine, and when I click the save pdf icon I can choose a file location, but the application closes at that point.

Exception 395: unable to open module file `/usr/lib/ImageMagick-6.2.4/modules-Q16/coders/zip.la': No such file or directory at /usr/bin/gscan2pdf line 1517.

Looks as though imagemagick is missing a module. Which distro are you running on what hardware? Also, please find the scan in a randomly-named directory in the the /tmp directory and email it to ra28145 at users.sf.net.

> **tcornishmn said:**
> *** unhandled exception in callback:
***   Wrong TIFF Id '8970' (should be 42). at /usr/share/perl5/PDF/API2/Resource/XObject/Image/TIFF.pm line 407.

But gscan2pdf should really make a better effort at spotting the error and not just fall over.

---

### Post by tcornishmn on 2007-06-24
Ubuntu Feisty, fully patched on x86 (HP laptop).  I tried my other machine also running Feisty (HP desktop), and it seems to have the same problem.  In both cases the scanner was a Xerox Documate 252 running scanadf.

 I looked in Synaptic and it seems that ImageMagick is installed.  The Imagemagick version is listed as 7:6.2.4.5.dfsg-0.14.  I'm running the latest gscan2pdf as well.  It's been a little while since I've used your program - I'm not sure how long this has been a problem.


I tried to find the /usr/lib/ImageMagick-6.2.4/modules-Q16/coders/zip.la' file, and the only thing I have under /usr/lib/ImageMagick-6.2.4 is a folder called config with a few XML files in it.  

I can't seem to find the file zip.la anywhere in the filesystem.  Should I try to reinstall ImageMagick?

Thanks for your help,
TJ

---

### Post by JeffreyRatcliffe on 2007-06-24
> **tcornishmn said:**
> Ubuntu Feisty, fully patched on x86 (HP laptop).  I tried my other machine also running Feisty (HP desktop), and it seems to have the same problem.  In both cases the scanner was a Xerox Documate 252 running scanadf.

Please try the scanimage frontend. Also, please find the scan causing the problem in a randomly-named directory in the the /tmp directory and email it to ra28145 at users.sf.net.

> **tcornishmn said:**
> I can't seem to find the file zip.la anywhere in the filesystem.  Should I try to reinstall ImageMagick?

No. Given that I also have an x86 machine running Feisty, I assume that the difference must be something about your scanner output that either ImageMagick or PDF::API2 doesn't like.

If you can find the scan as described above (it will have a .pnm extension) and email it to me, I'll do some further checks.

---

### Post by betty on 2007-06-24
Hi JeffreyRadcliffe,

I'm eager to use this program - but after installing the program as well as all the dependencies, when I hit "scan" I get:

"Unknown Error:  Segmentation Fault (Core dumped)

I have a Samsung SCX-4100 MFP... scanner works using XSANE Image scanner, run as root.  gscan2pdf will not work unless I run it as root as well, but I still get that error.  Do you have a solution?

Many thanks,
betty

---

### Post by JeffreyRatcliffe on 2007-06-24
> **betty said:**
> I'm eager to use this program - but after installing the program as well as all the dependencies, when I hit "scan" I get:

"Unknown Error:  Segmentation Fault (Core dumped)

I have a Samsung SCX-4100 MFP... scanner works using XSANE Image scanner, run as root.  gscan2pdf will not work unless I run it as root as well, but I still get that error.  Do you have a solution?

There is something seriously wrong with with your SANE backend if you have to have to be root to use it. I would report that as a bug in Launchpad. Aside that - the error message you are getting is passed to gscan2pdf from the frontend. The default frontend is scanimage. Try the scanadf frontend in the Edit menu.

---

### Post by tcornishmn on 2007-06-24
Hi Jeffrey - I was mistaken, I was actually using scanimage.  When I tried scanadf, the behavior is slightly different - instead of the program closing, it hangs at the saving pdf dialog box.  Under the hood, the symptoms seem to be the same - the pnms in the temp folder seem fine, and there is one that is renamed to .zip, but not converted.  

I sent you a compressed version of the pnm you requested to  your email.

Thanks!

---

### Post by noynac on 2007-06-25
I need to convert PNM or TIFF output from my scanner into a PDF file. The scans are done in lineart mode utilizing the scanimage utility. Options that I have either tried or considered are:

1) Use the convert program from Imagemagick to convert TIFF scanner output directly to PDF. This worked but created extremely large file sizes.

2) Use the tiff2pdf program to convert TIFF scanner output directly to a PDF file. This seems to work well. 

3) Use the pnm2tiff program to convert the PNM scanner output to a temporary TIFF file and then use the tiff2pdf program to convert the TIFF file to a PDF file. This was recommended in some postings that I found while doing Google research on this issue, although I'm not sure why this approach is preferred, unless it has to do with the advantage of using PNM scanner output.

4) Finally, use the tiff2ps program to convert the TIFF scanner output to a PS file and then send this file to a previously created Cups-PDF printer. This worked but seems clumsy.

I have tentatively decided on option 2, as it seems to work well and the file sizes are quite reasonable. I wondered and my specific question is whether there might be some other command-line conversion utility that would work better. 

BTW, I am doing this because I want to get the scanbutton utility working with my scanner, and I want to have the ability to scan a single-page document to a PDF file with only one button press on my scanner. For most scanning, I will continue to use gscan2pdf and (rarely) Xsane.

Thanks!

---

### Post by JeffreyRatcliffe on 2007-06-26
> **noynac said:**
> I need to convert PNM or TIFF output from my scanner into a PDF file. The scans are done in lineart mode utilizing the scanimage utility. Options that I have either tried or considered are:

How about  importing the scanned images in gscan2pdf using File/Import (you can multi-select) and writing the PDF from there?

I'm also wondering how best to offer support for scanbutton.d in gscan2pdf.

---

### Post by ihristov on 2007-06-26
Jeffrey, thanks for an excellent application.

I have been using gscan2pdf for more than a year with no problems. I just found this thread and added the
```
deb http://gscan2pdf.sourceforge.net/download/debian binary/
```
repository via Synaptic / Settings / Repositories

I have several questions:

1) It would be nice if this could go in the standard Universe repository so it does not require changing sources. Are there any plans on doing so?

2) Where do I get your public GPG key to import it into Synaptic? Right now it's complaining that it can't verify the signature.

3) After I added the sourceforge repo, the auto-update application tells me there is an update, but it's not able to display the change list. I noticed that when I opened the repo URL [http://gscan2pdf.sourceforge.net/download/debian/binary/](http://gscan2pdf.sourceforge.net/download/debian/binary/) directly in a browser I see there are some "changes" files - for example "gscan2pdf_0.9.12_i386.changes". I wonder why it has an architecture in the file name? I am running AMD64 version of Ubuntu 7.04, so maybe this is a reason it does not display the change log.


When I tried to display the changes directly from Synaptic it told me that it can't retrieve the file

[http://changelogs.ubuntu.com/changelogs/pool/main/g/gscan2pdf/gscan2pdf_0.9.12/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/g/gscan2pdf/gscan2pdf_0.9.12/changelog)

In other words for some reason it assumes that the change log is at changelogs.ubuntu.com, instead of at the original repository URL

---

### Post by noynac on 2007-06-26
> **JeffreyRatcliffe said:**
> How about  importing the scanned images in gscan2pdf using File/Import (you can multi-select) and writing the PDF from there?

I'm also wondering how best to offer support for scanbutton.d in gscan2pdf.

My immediate goal with scanbutton was to be able to do a one-button scan. In other words, I want to be able to create a PDF scan of a one-page document (e.g. a receipt) by placing the document on the scanner and pushing a button on the scanner. I want this to be automatic so that I don't have to do anything with software.

My scanner has four buttons, so there would be available buttons for gscan2pdf. On first thought, the easiest implementation would be to have the scanner button perform the same function as as the "scan" button in gscan2pdf. In other words, the process with a flatbed scanner would be:

1) The user calls up gscan2pdf on his computer and sets all options for mode, contrast, threshold, resolution, etc.

2) The user places the document on the scanner and pushes the scanner button to begin the scan.

3) When the first document is scanned, the user places the second document on the scanner and pushes the scanner button.

4) After all documents are scanned, the user returns to his computer and saves the document in gscan2pdf.

As mentioned, the above is very simple but would probably be most helpful to me. An enhancement might involve loading gscan2pdf if it is not already running when the scanner button is first pressed. I rarely change the gscan2pdf settings, so the process for me would be:

1) Place the document on the scanner.

2) Press the scanner button to load gscan2pdf.

3) Press the scanner button a second time to begin the scan, and so on...

---

### Post by JeffreyRatcliffe on 2007-06-26
> **ihristov said:**
> 1) It would be nice if this could go in the standard Universe repository so it does not require changing sources. Are there any plans on doing so?

[https://bugs.launchpad.net/ubuntu/+bug/113784](https://bugs.launchpad.net/ubuntu/+bug/113784) already asks for this, but as v0.9.10 is in Debian Unstable, it should be imported automatically, and therefore be in Gutsy. Of course, you then won't get an update until Gutsy+1.

gscan2pdf has suddenly become popular - Fedora and Mandriva have also started packaging it.

> **ihristov said:**
> 2) Where do I get your public GPG key to import it into Synaptic? Right now it's complaining that it can't verify the signature.

Yeah, I know. Even I get this at the mo. I'll upload it to Sourceforge.

> **ihristov said:**
> 3) After I added the sourceforge repo, the auto-update application tells me there is an update, but it's not able to display the change list. I noticed that when I opened the repo URL [http://gscan2pdf.sourceforge.net/download/debian/binary/](http://gscan2pdf.sourceforge.net/download/debian/binary/) directly in a browser I see there are some "changes" files - for example "gscan2pdf_0.9.12_i386.changes". I wonder why it has an architecture in the file name? I am running AMD64 version of Ubuntu 7.04, so maybe this is a reason it does not display the change log.

That is very strange. I'll look into it.

---

### Post by JeffreyRatcliffe on 2007-06-26
> **noynac said:**
> My immediate goal with scanbutton was to be able to do a one-button scan. In other words, I want to be able to create a PDF scan of a one-page document (e.g. a receipt) by placing the document on the scanner and pushing a button on the scanner. I want this to be automatic so that I don't have to do anything with software.

SANE has  a wait-for-button option for some scanners, and gscan2pdf supports this. Unforunately, neither yours nor mine is one of said scanners.

It is going to take some thought and research for me to work out how to do this. Thanks for your ideas.

---

### Post by priegog on 2007-06-27
Jeffrey, thanks so much for this app... this is just exactly what I had been looking for all over the place!
In it's current state I have no complaints about the program (yet). 
Anyways, just wanted to say you made my life much much easier, and you made the linux community a BIG favor. Actually, have you thought about talking to someone at ubuntu to have it included in the official repos? I really think this app is ready to be used widely.
Anyways, thanks again mate!

Cheers!

---

### Post by JeffreyRatcliffe on 2007-06-27
> **priegog said:**
> Jeffrey, thanks so much for this app... this is just exactly what I had been looking for all over the place!

I'm glad it's useful.

> **priegog said:**
> Actually, have you thought about talking to someone at ubuntu to have it included in the official repos?

Already done. It looks as though it will be in Gutsy.

---

### Post by priegog on 2007-06-27
> **JeffreyRatcliffe said:**
> 
Already done. It looks as though it will be in Gutsy.

I'm glad. Gutsy seems to be becoming a strong release.. just what we need before the next LTS

---

### Post by helliewm on 2007-06-27
Thank you so much, this is brilliant. I have spent ages looking for something like this. I get then edit the PDF with PDFEdit  that can be obtained as deb file from [www.getdeb.net](www.getdeb.net).

Helen

---

### Post by expatCM on 2007-06-28
This appears to be exactly what I have been looking for.

Installation (from the sourceforge download) was easy but I did need to additionally install djvulibre-bin, xdg-email and unpaper but that is no problem.

The program does not run for me but I think this is not a problem with the program itself, it is that there is a problem (certainly for me) with the latest kernel upgrade and xsane.  Xsane will run when booted to the earlier kernel and the scanner will work in the present release when using kooka.  The message I get from gscan is "Unknown message: scanimage: sane_start: Invalid argument" but xsane dies with "invalid pointer: 0x083f3e48" so ....   when they release the xsane patch I will continue to march ahead :)

However, thanks for the program .... it really does fit a need.

---

### Post by JeffreyRatcliffe on 2007-06-28
> **expatCM said:**
> The program does not run for me but I think this is not a problem with the program itself, it is that there is a problem (certainly for me) with the latest kernel upgrade and xsane.  Xsane will run when booted to the earlier kernel and the scanner will work in the present release when using kooka.  The message I get from gscan is "Unknown message: scanimage: sane_start: Invalid argument" but xsane dies with "invalid pointer: 0x083f3e48" so ....   when they release the xsane patch I will continue to march ahead :)

Important for gscan2pdf is either scanimage or scanadf. If you can get one of these command line tools to scan for you, you can use gscan2pdf. It has nothing to do with Xsane, and indeed, when the Feisty upgrade broke Xsane for Canoscan users a month or so ago, scanimage, and therefore gscan2pdf still worked.

---

### Post by expatCM on 2007-06-28
Ah ...  yet another place in Ubuntu where I get lost .... one day I might get it ...

From the command line  scanimage returns 
P5
# SANE data follows
0 0
255

and scanadf
scanadf: setting of option --br-x failed (Invalid argument)

So I guess I need to focus on the sane message from gscan "Unknown message: scanimage: sane_start: Invalid argument" to get things running.

---

### Post by JeffreyRatcliffe on 2007-06-28
> **expatCM said:**
> From the command line  scanimage returns 
P5
# SANE data follows
0 0
255

If you start gscan2pdf with

gscan2pdf --debug

try to scan, and send the output from the terminal window to ra28145 at users.sf.net, then I'll take a look.

---

### Post by expatCM on 2007-06-28
Thank you Jeffrey,  I have sent you an email with the command line output.

---

### Post by GerryB on 2007-06-28
> **drtpw said:**
> I'm a newbie.  Let's get that out of the way.  I'm learning my way around Ubuntu and I love it.  I read the forums, have 2 books .....
Here is a way that works for me without sending my stuff to a website for conversion (that makes me nervous):

Open OpenOffice writer, click on Insert, Picture, Scan, Select Source.  A scanner box opens.  Click on Create Preview.  A message comes up stating "Device does not offer preview, etc.".  Click on OK, the box closes and your document will be scanned.  Click on OK and the scanner box closes.

In OpenOffice writer, again click on Insert, Picture, Scan, and now on Request.  A new box opens and choose "Export Directly to PDF".  Name your file, highlight PDF, and Save.  The only down side is that you have to initially save the PDF to your home directory.  You can move it later.

I hope that this helps some people.  I have gotten much help from what everyone has done and written I this is my first reply to the forums.  Thank you for all your work.

Great suggestion. It's just what I need since I have to make about one PDF document per month. Thank you.

---

### Post by JeffreyRatcliffe on 2007-07-08
Following the open source edict of "Release early, release often", I have uploaded version 0.9.13 of my utility gscan2pdf to [http://sourceforge.net/projects/gscan2pdf](http://sourceforge.net/projects/gscan2pdf).

I have every intention of developing it into a fully-fledged application, so please as much constructive feedback as you like.

Changes:
+ Select all or Ctrl-A works properly in thumbnails or OCR buffer, depending on
  focus. Closes bug 1740131 (Ctrl-A (select all) in OCR window does not work).
+ Tesseract support. Closes feature request 1725818 (tesseract for OCR?)
+ unset mode if changing device.
  Closes bug 1741598 (2 scanners with differing mode options).
+ ghost scan all pages RadioButton if Flatbed selected.
  Closes bug 1743059 (Endless scanning loop)
+ trap device busy error. Closes bug 1744451 (handle busy device)
+ Modify PDF metadata date format to conform to ISO-8601
  Closes feature request 1744458 (change dates to ISO-8601)
+ Fixed double scan bug with scanadf frontend
+ Fixed bug where Custom paper size not set from default
+ Update to Danish translation (thanks to Jacob Nielsen)
+ Update to French translation (thanks to Pierre Slamich)
+ Update to Polish translation (thanks to Piotr Strebski)
+ Fixed blocking whilst setting up/updating scan dialog
+ US Legal paper.
  Closes feature request 1748679 (RFE: add legal paper size as an option)

Just add the following line to your /etc/apt/sources.list:```
deb http://gscan2pdf.sourceforge.net/download/debian binary/
```
If you are you are using Synaptic, then use menu Edit/Reload Package Information, search for gscan2pdf in the package list, and lo and behold, you can install the nice shiny new version automatically.

From the command line:```
sudo apt-get update
sudo apt-get install gscan2pdf
```

If you add my key to your list of trusted keys, then you will no longer get
the "not authenticated" warnings:```
gpg --keyserver www.keyserver.net --recv-keys 4DD7CC93
gpg --export --armor 4DD7CC93 | sudo apt-key add -
```

The dependencies are libgtk2-perl (>= 1:1.043-1), libgtk2-ex-simple-list-perl, perlmagick, libpdf-api2-perl, liblocale-gettext-perl (>= 1.05), libsane, sane-utils, libtiff-tools.

The help will require Gtk2::Ex::PodViewer. Rotating requires Imagemagick. The scanadf frontend is in sane. For Email as PDF, you need xdg-utils. OCR requires gocr. Having installed gscan2pdf, locate the gscan2pdf entry in Synaptic, right-click it and you can install them under "Recommends".

If anybody fancies translating gscan2pdf into any other languages, they are welcome to do so on Rosetta ([https://launchpad.net/products/gscan2pdf/trunk/+pots/gscan2pdf](https://launchpad.net/products/gscan2pdf/trunk/+pots/gscan2pdf))

---

### Post by mrojas73 on 2007-07-08
I keep getting this error when trying to update:

> W: Failed to fetch [http://gscan2pdf.sourceforge.net/download/debian/./gscan2pdf_0.9.13_all.deb](http://gscan2pdf.sourceforge.net/download/debian/./gscan2pdf_0.9.13_all.deb)
  404 Not Found

Edit:  I was able to download the file and install it manually.

---

### Post by JeffreyRatcliffe on 2007-07-08
> **mrojas73 said:**
> I keep getting this error when trying to update:

Thanks for the report. It took me such a long time to get rid of the "not authorised" problems, that I didn't properly test the repository when I had finished. I think I have fixed things, but Sourceforge have blocked ssh connections, and I can't upload the fix until it is working again.

---

### Post by JeffreyRatcliffe on 2007-07-08
The repository should now be working.

---

### Post by bsawler on 2007-07-11
Hi Jeffery, 

I downloaded and the interface is very nice.  The only issue is that I have some scanned documents that when I rescan I have to select "grey" cause lineart will not work.  So when I use xsane the pdf size is 500kB.  When I save to tiff it is 60kB.  

When I use gscan2pdf and create a pdf with "grey", the size is the same at about 500kB.  So I would like to save to tiff but when I do, I get an error:
```
/tmp/Foipg/7All/tVLXXPWSBY.tif. Cannot read TIFF Header
```

Is there something else that needs to be installed? 

Regards,
Bradley

---

### Post by JeffreyRatcliffe on 2007-07-11
> **bsawler said:**
> When I use gscan2pdf and create a pdf with "grey", the size is the same at about 500kB.

When you save the PDF, have you tried the different (none, PNG, JPEG) compression options? I am surprised that with, for instance, PNG, the file comes out that large.

Why will lineart not work? What happen when you try?

> **bsawler said:**
> So I would like to save to tiff but when I do, I get an error:
```
/tmp/Foipg/7All/tVLXXPWSBY.tif. Cannot read TIFF Header
```

Please start gscan2pdf with ```
gscan2pdf --debug
``` and send the output from the terminal window to ra28145 at users.sf.net.

---

### Post by bsawler on 2007-07-11
> When you save the PDF, have you tried the different (none, PNG, JPEG) compression options? I am surprised that with, for instance, PNG, the file comes out that large.

Same file, scanned at A4, Mode Gray, res: 75 dpi save with compression:
PNG = 345 kB
JPEG = 91 kB - Now this is acceptable. 

> 
Why will lineart not work? What happen when you try?


Lineart does not work for this page only, cause it is a full page form with many boxes to enter your name, etc, and it has first been scanned before being sent to me.  I print it in black in white and it comes out with gray and while.  I filled out the form in pen, and when I scan in "Black and White" with my brother scanner and win xp, it comes out fine.  If I scan this file with xsane or kooka or gscan, it is completely illegible at even 300dpi.  If I scan a letter that I signed in lineart mode, it comes out fine.  

Output sent to your email.  With the JPEG compression, the program is now perfect for my use. 
Thanks,

---

### Post by JeffreyRatcliffe on 2007-07-11
Following the open source edict of "Release early, release often", I have uploaded version 0.9.14 of my utility gscan2pdf to [http://sourceforge.net/projects/gscan2pdf](http://sourceforge.net/projects/gscan2pdf).

I have every intention of developing it into a fully-fledged application, so please as much constructive feedback as you like.

Changes:
+ Fixed bug parsing device-dependent options.
  Closes bug 1751125 (Some device-dependent options have gone)
+ Update to French translation (thanks to Nicolas Stransky)
+ Update to Italian translation (thanks to Andrea (pikkio))
+ Update to Portugese translation (thanks to Hugo Pereira)
+ Update to Russian translation (thanks to Alexandre Prokoudine)

Just add the following line to your /etc/apt/sources.list:```
deb http://gscan2pdf.sourceforge.net/download/debian binary/
```
If you are you are using Synaptic, then use menu Edit/Reload Package Information, search for gscan2pdf in the package list, and lo and behold, you can install the nice shiny new version automatically.

From the command line:```
sudo apt-get update
sudo apt-get install gscan2pdf
```

If you add my key to your list of trusted keys, then you will no longer get
the "not authenticated" warnings:```
gpg --keyserver www.keyserver.net --recv-keys 4DD7CC93
gpg --export --armor 4DD7CC93 | sudo apt-key add -
```

The dependencies are libgtk2-perl (>= 1:1.043-1), libgtk2-ex-simple-list-perl, perlmagick, libpdf-api2-perl, liblocale-gettext-perl (>= 1.05), libsane, sane-utils, libtiff-tools.

The help will require Gtk2::Ex::PodViewer. Rotating requires Imagemagick. The scanadf frontend is in sane. For Email as PDF, you need xdg-utils. OCR requires gocr. Having installed gscan2pdf, locate the gscan2pdf entry in Synaptic, right-click it and you can install them under "Recommends".

If anybody fancies translating gscan2pdf into any other languages, they are welcome to do so on Rosetta ([https://launchpad.net/products/gscan2pdf/trunk/+pots/gscan2pdf](https://launchpad.net/products/gscan2pdf/trunk/+pots/gscan2pdf))

---

### Post by ihristov on 2007-07-12
If I might add. For the "visually" inclined here are the same instructions of adding the repository using GUI tools.

1. Open a terminal and in it execute
```
wget -O "~/Desktop/Jeffrey Ratcliffe.gpg.key" "http://pgp.mit.edu:11371/pks/lookup?op=get&search=0x4DD7CC93"
```
2. Open Synaptic. Provide your password when asked.
3. Select the Settings / Repositories menu
4. Click on the "Third party software" tab. Click on the "Add ..." button
5. Paste the text below in the dialog that opens
   **deb http://gscan2pdf.sourceforge.net/download/debian binary/**
6. Click on the "Authentication" tab. Click on "Import Key File..."
7. Browse to your Desktop folder and select the file "**Jeffrey Ratcliffe.gpg.key**". A new entry for "Jeffrey Ratcliffe" will show up in the list
8. Hit the "Close" button to close the "Repositories" dialog
9. Hit the "Reload" button (or press Ctrl+R)
10. Hit the "Search" button (or press Ctrl+F). type **gscan2pdf** and hit OK
11. The search result list should now show the gscan2pdf package. Right-click on it and select it for installation
12. Hit the "Apply" button (or press Ctrl+P) to install

---

### Post by bsawler on 2007-07-12
Hello Jeffrey, 

I just installed a second scanner the Brother MFC-7420.  I followed this tread: 
[http://ubuntuforums.org/showthread.php?t=105703&highlight=mfc-210c](http://ubuntuforums.org/showthread.php?t=105703&highlight=mfc-210c)

and in the "Scanner Setup" section  Step 3 says: 

Step 3: Installing XSane

To use the scanner requires that Ubuntu's scanner software be installed. Copy the following code into the Terminal:
```
sudo aptitude install sane xsane libsane sane-utils
```

So when I use Xsame Image, I can choose everything, B&W, Color etc. etc.  

No when I fire up gscan2pdf and click the scan button the window comes up and it the scanner selected and Pages, and Source Document, but there are NO options below "Device-Dependant options".  If you Scan, it will scan in colour at maximum resolution.  There is nowhere to change the settings now.  

Is there something that I should do so that I can get gscan to work, cause I really like the GUI compared to Xsane. 

Thanks,
Bradley

---

### Post by JeffreyRatcliffe on 2007-07-12
> **bsawler said:**
> No when I fire up gscan2pdf and click the scan button the window comes up and it the scanner selected and Pages, and Source Document, but there are NO options below "Device-Dependant options".  If you Scan, it will scan in colour at maximum resolution.  There is nowhere to change the settings now.  

Is there something that I should do so that I can get gscan to work, cause I really like the GUI compared to Xsane.

It sounds to me as though there is something about the device-dependent options that gscan2pdf doesn't understand.

If you start gscan2pdf with ```
gscan2pdf --debug
```and call up the scan dialog, then there should appear a load of output in the terminal window. Please send me the output and I'll take a look.

---

### Post by Shortchord on 2007-07-15
> **JeffreyRatcliffe said:**
> The dependencies are libgtk2-perl (>= 1:1.043-1), libgtk2-ex-simple-list-perl, perlmagick, libpdf-api2-perl, liblocale-gettext-perl (>= 1.05), libsane, sane-utils, libtiff-tools.

Jeffrey, when I try to install through either Synaptic or the terminal, I get a message "gscan2pdf:
 Depends: libgtk2-ex-simple-list-perl  but it is not installable".  

If I try to install that package separately, I get the following message:

> Package libgtk2-ex-simple-list-perl is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libgtk2-ex-simple-list-perl has no installation candidate

Any suggestions?

---

### Post by ihristov on 2007-07-15
> **Shortchord said:**
> Any suggestions?

You might want to try to update your package list

```
sudo aptitude update
```

and then try the installation again.

---

### Post by JeffreyRatcliffe on 2007-07-16
> **Shortchord said:**
> Jeffrey, when I try to install through either Synaptic or the terminal, I get a message "gscan2pdf:
 Depends: libgtk2-ex-simple-list-perl  but it is not installable".  

You are using Dapper, right? libgtk2-ex-simple-list-perl is available in Edgy onwards. For Dapper users, I have built a package and put it on Sourceforge: [https://sourceforge.net/project/showfiles.php?group_id=174140](https://sourceforge.net/project/showfiles.php?group_id=174140).

---

### Post by gylf on 2007-07-17
Hello!  First off, a huge thank you for gscan2pdf - outstanding work!

> **JeffreyRatcliffe said:**
> Having run the OCR, the buffer is automatically stored with the page (each page has its own buffer), and when you save it as a PDF, the contents of each buffer is saved with the appropriate page as an annotation. If you open the PDF in Acrobat Reader, you will see the notes.

I had hoped that Beagle would then index the annotations, but unfortunately this is not the case. It relies on pdftotext, which at the moment doesn't read them. I have logged a feature request.

I agree that the current GUI design for the OCR integration isn't very good, but until either pdftotext starts reading the annotations, or I figure out a better way of embedding the OCR output in the PDF, I'm not sure how useful it is.


Have there been any changes in this regard?  I tried gscan2pdf last night and it worked perfectly, including accurate OCR. But I wasn't able to use the "find" feature in the PDFs I made.

---

### Post by JeffreyRatcliffe on 2007-07-17
> **gylf said:**
> Have there been any changes in this regard?  I tried gscan2pdf last night and it worked perfectly, including accurate OCR. But I wasn't able to use the "find" feature in the PDFs I made.

gscan2pdf embeds the OCR output as plain text behind the scan, so whilst "find" in your favourite PDF viewer will find the plain text, you won't be able to see it, as it is hidden behind the scan, and I have picked a miniscule font size to make sure that it fits on the page.

This technique, however, ensures that Beagle will index it.

As soon as an OSS OCR engine digs out not only the text itself, but also its size and position, I will adjust the embedding in the PDF appropriately, and "find" in the PDF viewer will work as expected.

---

### Post by gylf on 2007-07-17
Thanks for the fast reply!  I understand what your saying.  I'm very impressed that this will work with Beagle (and I assume Google Desktop as well).  I would say that the "find" feature is really pretty minor in comparison.

One quick follow-up question though: Since each OCR buffer is stored on a per-page basis, will doing a "find" pull you to the right page (but not the exact location of the text)?

---

### Post by JeffreyRatcliffe on 2007-07-17
> **gylf said:**
> One quick follow-up question though: Since each OCR buffer is stored on a per-page basis, will doing a "find" pull you to the right page (but not the exact location of the text)?

I've just tried it with acroread: it does find the correct page for you.

---

### Post by JeffreyRatcliffe on 2007-07-23
Following the open source edict of "Release early, release often", I have uploaded version 0.9.15 of my utility gscan2pdf to [http://sourceforge.net/projects/gscan2pdf](http://sourceforge.net/projects/gscan2pdf).

I have every intention of developing it into a fully-fledged application, so please as much constructive feedback as you like.

Changes:
+ Fixed bug setting defaults, also responsible for preventing the
  device-dependent options being displayed in certain circumstances.
+ store unpaper options in settings
+ fractional instead of pulsing ProgressBar & more info during PDF save
+ fixed bug where spaces in mode not escaped in shell
+ fixed bug parsing device-dependent options (affecting some Brother scanners).
+ option not to restore window settings.
  closes Debian bug 433497 (please don't remember window position)
+ Update to French translation (thanks to Nicolas Stransky)

Just add the following line to your /etc/apt/sources.list:```
deb http://gscan2pdf.sourceforge.net/download/debian binary/
```
If you are you are using Synaptic, then use menu Edit/Reload Package Information, search for gscan2pdf in the package list, and lo and behold, you can install the nice shiny new version automatically.

From the command line:```
sudo apt-get update
sudo apt-get install gscan2pdf
```

If you add my key to your list of trusted keys, then you will no longer get
the "not authenticated" warnings:```
gpg --keyserver www.keyserver.net --recv-keys 4DD7CC93
gpg --export --armor 4DD7CC93 | sudo apt-key add -
```

The dependencies are libgtk2-perl (>= 1:1.043-1), libgtk2-ex-simple-list-perl, perlmagick, libpdf-api2-perl, liblocale-gettext-perl (>= 1.05), libsane, sane-utils, libtiff-tools.

The help will require Gtk2::Ex::PodViewer. Rotating requires Imagemagick. The scanadf frontend is in sane. For Email as PDF, you need xdg-utils. OCR requires gocr. Having installed gscan2pdf, locate the gscan2pdf entry in Synaptic, right-click it and you can install them under "Recommends".

If anybody fancies translating gscan2pdf into any other languages, they are welcome to do so on Rosetta ([https://launchpad.net/products/gscan2pdf/trunk/+pots/gscan2pdf](https://launchpad.net/products/gscan2pdf/trunk/+pots/gscan2pdf))

---

### Post by JeffreyRatcliffe on 2007-07-23
> **ihristov said:**
> 3) After I added the sourceforge repo, the auto-update application tells me there is an update, but it's not able to display the change list. I noticed that when I opened the repo URL [http://gscan2pdf.sourceforge.net/download/debian/binary/](http://gscan2pdf.sourceforge.net/download/debian/binary/) directly in a browser I see there are some "changes" files - for example "gscan2pdf_0.9.12_i386.changes". I wonder why it has an architecture in the file name? I am running AMD64 version of Ubuntu 7.04, so maybe this is a reason it does not display the change log.

It seems to be a bug/feature in the Debian packaging tools that puts the i386 in the .changes filename. In this case, "all" would be more appropriate. However, it seems that this has got nothing to do with not displaying the changelog in the Update Manager/Synaptic:

> **ihristov said:**
> When I tried to display the changes directly from Synaptic it told me that it can't retrieve the file

[http://changelogs.ubuntu.com/changelogs/pool/main/g/gscan2pdf/gscan2pdf_0.9.12/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/g/gscan2pdf/gscan2pdf_0.9.12/changelog)

In other words for some reason it assumes that the change log is at changelogs.ubuntu.com, instead of at the original repository URL

It seems that the Update Manager/Synaptic only look in changelogs.ubuntu.com for changelogs, and therefore only official packages will have their changelog displayed, as nobody else has write access.

---

### Post by gylf on 2007-07-23
> **JeffreyRatcliffe said:**
> 
I have every intention of developing it into a fully-fledged application, so please as much constructive feedback as you like.


I think the application is outstanding. 

One feature I was going to mention was encrypt/password-protect a document upon generation, but I didn't want to contribute to feature-creep.  Right now I use PDF toolkit to do this after the fact, which works fine.  So if others would use this feature, just an idea.

I'm also having trouble getting the email feature working.  The proper library is installed.  Thunderbird is installed, but I have Evolution set as the default client in Gnome I believe.  Maybe this has already been addressed (this thread is getting a bit long!)

Thank you again for all your hard work.

---

### Post by JeffreyRatcliffe on 2007-07-23
> **gylf said:**
> One feature I was going to mention was encrypt/password-protect a document upon generation, but I didn't want to contribute to feature-creep.  Right now I use PDF toolkit to do this after the fact, which works fine.  So if others would use this feature, just an idea.

Would anyone else use this?

> **gylf said:**
> I'm also having trouble getting the email feature working.  The proper library is installed.  Thunderbird is installed, but I have Evolution set as the default client in Gnome I believe.  Maybe this has already been addressed (this thread is getting a bit long!)

This should work with Evolution, but won't with Thunderbird, as explained in the help. Do you get an error message?

---

### Post by gylf on 2007-07-23
> **JeffreyRatcliffe said:**
> 
This should work with Evolution, but won't with Thunderbird, as explained in the help. Do you get an error message?

Nope, just stays grayed out, even when my "default email client" in the Gnome settings is set to evolution... is that where gscan2pdf detects the default email client?  I will try this again over lunch (I'm at work right now) and see if I can get you more info.

---

### Post by JeffreyRatcliffe on 2007-07-23
> **gylf said:**
> Nope, just stays grayed out, even when my "default email client" in the Gnome settings is set to evolution... is that where gscan2pdf detects the default email client?  I will try this again over lunch (I'm at work right now) and see if I can get you more info.

gscan2pdf just checks for the presence of the xdg-utils package, and if it not there, ghosts the menu item. If you think it is installed, but that gscan2pdf hasn't found it, email the output of ```
gscan2pdf --debug
``` to ra28145 at users dot sf dot net (you don't need to scan anything in this case, just start it, and quit).

---

### Post by gylf on 2007-07-25
> **JeffreyRatcliffe said:**
> gscan2pdf just checks for the presence of the xdg-utils package, and if it not there, ghosts the menu item. If you think it is installed, but that gscan2pdf hasn't found it, email the output of ```
gscan2pdf --debug
``` to ra28145 at users dot sf dot net (you don't need to scan anything in this case, just start it, and quit).

An update (sorry it took so long):

The debug command showed xdg-utils was installed; I tried sending an email using it from the command line and that worked fine, but the menu option was still grayed out.  Then I upgraded from 9.14 to 9.15 and now it appears to be working great.

When I originally installed 9.14, evolution was probably not selected as the default email client and xdg-utils was not installed.  I made those changes later.  Would that have caused the problem?  

Regardless, it's working now so all is well :)

---

### Post by JeffreyRatcliffe on 2007-07-25
> **gylf said:**
> When I originally installed 9.14, evolution was probably not selected as the default email client and xdg-utils was not installed.  I made those changes later.  Would that have caused the problem?

gscan2pdf should check for necessary packages every time you start it, so that shouldn't have been the problem. But if it is working now...

---

### Post by JeffreyRatcliffe on 2007-08-24
Following the open source edict of "Release early, release often", I have uploaded version 0.9.16 of my utility gscan2pdf to [http://sourceforge.net/projects/gscan2pdf](http://sourceforge.net/projects/gscan2pdf).

I have every intention of developing it into a fully-fledged application, so please as much constructive feedback as you like.

Changes:
+ do not restore mode setting if default device not found
+ workaround for those versions of imagemagick that produce 16bit output with rotate.
  Patch 1760543 (rotate creates 16bit images that tesseract can't read) from Chris Mayo
+ ProgressBar during image import
+ Downsample option.
  Closes Feature Request 1722832 (setting the resolution before export)
+ Hidden text layer from OCR in djvu output
+ Support for language options in tesseract-2.00
+ UTF-8 support in OCR output
+ Fixed bug caused by imagemagick giving resolution=0.
  Closes bug 1770367 (Illegal division by zero)
+ ProgressBar during TIFF save
+ better attempt at trapping errors whilst embedding scan in PDF
+ ProgressBar during DjVu save
+ Stop unpaper and ocr if scan is cancelled
+ Fixed scrolling bug during drag and drop
+ Update to Dutch translation (thanks to Eric Spierings)
+ Update to French translation (thanks to Nicolas Stransky)
+ Update to Spanish translation (thanks to Rodrigo Donado)

Just add the following line to your /etc/apt/sources.list:```
deb http://gscan2pdf.sourceforge.net/download/debian binary/
```
If you are you are using Synaptic, then use menu Edit/Reload Package Information, search for gscan2pdf in the package list, and lo and behold, you can install the nice shiny new version automatically.

From the command line:```
sudo apt-get update
sudo apt-get install gscan2pdf
```

If you add my key to your list of trusted keys, then you will no longer get
the "not authenticated" warnings:```
gpg --keyserver www.keyserver.net --recv-keys 4DD7CC93
gpg --export --armor 4DD7CC93 | sudo apt-key add -
```

The dependencies are libgtk2-perl (>= 1:1.043-1), libgtk2-ex-simple-list-perl, perlmagick, libpdf-api2-perl, liblocale-gettext-perl (>= 1.05), libsane, sane-utils, libtiff-tools.

The help will require Gtk2::Ex::PodViewer. Rotating requires Imagemagick. The scanadf frontend is in sane. For Email as PDF, you need xdg-utils. OCR requires gocr, or better tesseract. Having installed gscan2pdf, locate the gscan2pdf entry in Synaptic, right-click it and you can install them under "Recommends".

If anybody fancies translating gscan2pdf into any other languages, they are welcome to do so on Rosetta ([https://launchpad.net/products/gscan2pdf/trunk/+pots/gscan2pdf](https://launchpad.net/products/gscan2pdf/trunk/+pots/gscan2pdf))

---

### Post by moshuptrail on 2007-08-25
Would you check your key on the keyserver.  I'm getting:

gpgkeys: key 4DD7CC93 not found on keyserver

---

### Post by JeffreyRatcliffe on 2007-08-25
> **moshuptrail said:**
> Would you check your key on the keyserver.  I'm getting:

gpgkeys: key 4DD7CC93 not found on keyserver

[www.keyserver.net](www.keyserver.net) seems to be down. Try subkeys.pgp.net

---

### Post by Dunkeltron on 2007-08-29
@JeffreyRatcliffe, you say:

> OCR requires gocr, or better tesseract.

is there something I have todo for gscan2pdf recognizing tesseract?
Gocr was found, but I have no way of choice for tesseract. So I tried to kick gocr but now there is no OCR.

Perhaps I have to set a symlink or a path or some config file?

By the way: A really great piece of software and exactly what I need. Thank you!

---

### Post by JeffreyRatcliffe on 2007-08-30
> **Dunkeltron said:**
> is there something I have todo for gscan2pdf recognizing tesseract?

gscan2pdf should just recognise that it is available.

What do you get from ```
which tesseract
``` on the command line?

---

### Post by Dunkeltron on 2007-08-30
seems to be okay: it gives
```
/usr/bin/tesseract
```

But now there is OCR agian. Perhaps the reboot has done it.
Thank you

---

### Post by Dunkeltron on 2007-08-31
I now can choose OCR (it tells not what OCR, but tesseract is there, gocr not) and when it shall ocr a document I get a panel with the button "start OCR". Then I start it and a progression panel pops up and let me wait for a while.

But when its over, nothing is in the area in the main window.
With gocr I found at this lower area the result of the OCR (not really usable, but still some chars)

So I did it again. This time greping ps aux for "tesseract"
Nothing...

Have I done everything right? Should there be tesseract?

---

### Post by JeffreyRatcliffe on 2007-08-31
> **Dunkeltron said:**
> I now can choose OCR (it tells not what OCR, but tesseract is there, gocr not) and when it shall ocr a document I get a panel with the button "start OCR". Then I start it and a progression panel pops up and let me wait for a while.

But when its over, nothing is in the area in the main window.
With gocr I found at this lower area the result of the OCR (not really usable, but still some chars)

The idea is that with an image in the detail view (from scan, imported, etc.) you start the OCR engine, and the output appears in the buffer below the detail view. You can edit it if you like, and it gets embedded behind the image when you save the page as a PDF or DJVU.

Note that for decent results, you need a resolution of at least 300, and better 400dpi.

You can also get gscan2pdf to run the OCR engine automatically as part of the scan process.

---

### Post by Dunkeltron on 2007-09-01
Well  I think I do understand how it should work - but I'm afraid that ist doesn't work here. Scan is great and all went fine.  Unpaper does something if I use it (it will need a bit time for me to make a good result) - all okay.

But when I tried to start OCR (the tesseract one - which was the only ocr on my system) a small window opened telling me it is doing ocr and took a long time for showing it, but after that there was nothing in the edit area where it should be. No text or anything at all.

Now I have installed GOCR again and there is a result. Well not a very good result and it takes much more time per page, but there are some characters.

I tried tesseract from the shell and it also worked.

Is it possible that gscan2pdf everytime tries to use GOCR? Or a tesseract version is needed newer than the feisty-one (1.02-3)
Is there something I can find out (log or a debug mode)?

It would be great if I could bring it to work.

Thank you for your assistance (till now and furtheron)

---

### Post by JeffreyRatcliffe on 2007-09-02
> **Dunkeltron said:**
> But when I tried to start OCR (the tesseract one - which was the only ocr on my system) a small window opened telling me it is doing ocr and took a long time for showing it, but after that there was nothing in the edit area where it should be. No text or anything at all.

That doesn't sound good. Please start gscan2pdf with ```
gscan2pdf --debug
``` get something in the detail window, try to use OCR set to tesseract, and post output from the terminal window to ra28145 at users.sf.net

> **Dunkeltron said:**
> Now I have installed GOCR again and there is a result. Well not a very good result and it takes much more time per page, but there are some characters.

My results with tesseract are much better than GOCR. The only advantage that I can see of GOCR over tesseract 1.02 is that GOCR supports non-English characters.

> **Dunkeltron said:**
> Is it possible that gscan2pdf everytime tries to use GOCR? Or a tesseract version is needed newer than the feisty-one (1.02-3)

I was using the Feisty version until very recently when I packaged tesseract-2.01 in an attempt to get it into Debian and Gutsy. I use the new version in England and German with great success. But the results of the tesseract-1.02 were also good.

---

### Post by Dunkeltron on 2007-09-02
I were right - gocr is searched by gscan2pdf though I have purged it before and also reinstalled tesseract.

So I was going to reinstall gscan2pdf itself. And there I found my fault: It's just a few days from today when I have installed gscan2pdf but version has grown from 0.9.9 up to recently 0.9.16 and much parts have changed.

Now everything is working and all my reporting and asking seems to be killing of time. Sorry.

---

### Post by kafkaian on 2007-09-20
On both latest and Feisty kernels upgrading to 0.9.16 has caused a real system slowdown once the app is invoked.

I have had to force quit gscan several times to get the system back to normal speed whilst even the mouse cursor becomes laggy. Anyone else with the same problem?

After getting an 'unpaper' warning, here's the debug dump:

> root@ubuntu:/home/ian# gscan2pdf --debug
gscan2pdf 0.9.16
Using en_GB.UTF-8 locale
Gtk2-Perl version 1.140
Built for 2.10.9
Running with 2.10.11
$VAR1 = {
          'mode' => 'Color',
          'month' => '10',
          'x' => '210',
          'author' => 'Ian',
          'window_maximize' => '1',
          'y' => '297',
          'keywords' => '',
          'compression' => 'None',
          'downsample dpi' => 150,
          'layout' => 'single',
          'cwd' => '/home/ian/Desktop',
          'window_width' => '800',
          'day' => '19',
          'window_x' => '0',
          'window_y' => '0',
          't' => 0,
          'thumb panel' => '412',
          'Paper size' => 'A4',
          'Page range' => 'all',
          'subject' => '',
          'window_height' => '600',
          'device' => 'niash:libusb:003:002',
          'l' => 0,
          'pages to scan' => '1',
          'downsample' => '',
          'resolution' => '150',
          'title' => 'blahdeblah',
          'year' => '2006'
        };
Found PDF::API2
Found Image::Magick
Found ImageMagick
Found scanadf
Found xdg-email
Found gocr
Found cjb2 (djvu)
Found libtiff
scanimage --formatted-device-list="'%i','%d','%v %m'
" 2>/dev/null
Forked PID 9568
Waiting to reap process at /usr/bin/gscan2pdf line 2732.
Reaped PID -1
'0','niash:libusb:003:002','Hewlett-Packard ScanJet 4300C'
scanimage --help --device-name='niash:libusb:003:002' --mode='Color'
Forked PID 9598
Waiting to reap process at /usr/bin/gscan2pdf line 3733.
Reaped PID -1
Usage: scanimage [OPTION]...

Start image acquisition on a scanner device and write PNM image data to
standard output.

-d, --device-name=DEVICE   use a given scanner device (e.g. hp:/dev/scanner)
    --format=pnm|tiff      file format of output file
-i, --icc-profile=PROFILE  include this ICC profile into TIFF file
-L, --list-devices         show available scanner devices
-f, --formatted-device-list=FORMAT similar to -L, but the FORMAT of the output
                           can be specified: %d (device name), %v (vendor),
                           %m (model), %t (type), and %i (index number)
-b, --batch[=FORMAT]       working in batch mode, FORMAT is `out%d.pnm' or
                           `out%d.tif' by default depending on --format
    --batch-start=#        page number to start naming files with
    --batch-count=#        how many pages to scan in batch mode
    --batch-increment=#    increase number in filename by an amount of #
    --batch-double         increment page number by two for 2sided originals
                           being scanned in a single sided scanner
    --batch-prompt         ask for pressing a key before scanning a page
    --accept-md5-only      only accept authorization requests using md5
-p, --progress             print progress messages
-n, --dont-scan            only set options, don't actually scan
-T, --test                 test backend thoroughly
-h, --help                 display this help message and exit
-v, --verbose              give even more status messages
-B, --buffer-size          change default input buffersize
-V, --version              print version information

Options specific to device `niash:libusb:003:002':
  Geometry:
    -l 0..220mm (in steps of 1) [0]
        Top-left x position of scan area.
    -t 0..297mm (in steps of 1) [0]
        Top-left y position of scan area.
    -x 0..220mm (in steps of 1) [210]
        Width of scan-area.
    -y 0..297mm (in steps of 1) [290]
        Height of scan-area.
    --resolution 75|150|300|600dpi [150]
        Sets the resolution of the scanned image.
  Image:
    --gamma-table 0..255,... (in steps of 1)
        Gamma-correction table.  In color mode this option equally affects the
        red, green, and blue channels simultaneously (i.e., it is an intensity
        gamma table).
  Scan Mode:
    --mode Color|Gray|Lineart [Color]
        Selects the scan mode (e.g., lineart, monochrome, or color).
  Enhancement:
    --threshold 0..100% (in steps of 1) [inactive]
        Select minimum-brightness to get a white point

Type ``scanimage --help -d DEVICE'' to get list of all options for DEVICE.

List of available devices:
    niash:libusb:003:002
$VAR1 = {
          'threshold' => {
                           'tip' => 'Select minimum-brightness to get a white point',
                           'default' => 'inactive',
                           'values' => '0..100% (in steps of 1)'
                         },
          'mode' => {
                      'tip' => 'Selects the scan mode (e.g., lineart, monochrome, or color).',
                      'default' => 'Color',
                      'values' => 'Color|Gray|Lineart'
                    },
          'resolution' => {
                            'tip' => 'Sets the resolution of the scanned image.',
                            'default' => '150',
                            'values' => '75|150|300|600dpi'
                          }
        };
$VAR1 = {
          'l' => '0',
          'y' => '297',
          'mode' => 'Color',
          'resolution' => '150',
          'x' => '210',
          't' => '0'
        };
scanimage --device-name='niash:libusb:003:002' --mode='Color' -l 0 -y 297 --resolution='150' -x 210 -t 0 --batch --batch-count=1
Forked PID 9622
scanimage: rounded value of tl-x from 0 to 0
scanimage: rounded value of resolution from 150 to 150
scanimage: rounded value of tl-y from 0 to 0
Importing out1.pnm, format Portable anymap
Added /tmp/KdV1ztrrZ8/dbS0nkY1v9.pnm at page 1 with resolution 150
Waiting to reap process at /usr/bin/gscan2pdf line 3278.
Reaped PID 9622


---

### Post by tiepolo on 2007-09-20
Hello!

I'm trying to use gscan2pdf with a scx-4100 multifunction from Samsung; i'm using here feisty;

1) scanner works with its own samsung driver;
2) scanner works with xsane (which works in root)
3) gscan2pdf doesn't work; 
scanimage --list-devices gives 

Segmentation fault (core dumped),

with  sudo gives    

device `smfp:SAMSUNG SCX-4100 Series on USB:0' is a SAMSUNG SCX-4100 Series on USB:0 Flatbed Scanner

using sudo gscan2pdf i get the front end open, but i get segmentation fault when i ask to acquire;

What can be the problem?

Thanks in advance,

Paolo

---

### Post by JeffreyRatcliffe on 2007-09-24
> **kafkaian said:**
> On both latest and Feisty kernels upgrading to 0.9.16 has caused a real system slowdown once the app is invoked.

I have had to force quit gscan several times to get the system back to normal speed whilst even the mouse cursor becomes laggy. Anyone else with the same problem?

After getting an 'unpaper' warning, here's the debug dump:

Apologies for the late reply - was on holiday.

I've not noticed any problems with speed. Are you talking about upgrading from 0.9.15->0.9.16, or did you upgrade from an earlier version?

Is the speed problem just while scanning. i.e. do you have it when the app is sitting open doing nothing?

I can't see any problems with the --debug output.

---

### Post by JeffreyRatcliffe on 2007-09-24
> **tiepolo said:**
> I'm trying to use gscan2pdf with a scx-4100 multifunction from Samsung; i'm using here feisty;

1) scanner works with its own samsung driver;
2) scanner works with xsane (which works in root)
3) gscan2pdf doesn't work; 
scanimage --list-devices gives 

Segmentation fault (core dumped),

with  sudo gives    

device `smfp:SAMSUNG SCX-4100 Series on USB:0' is a SAMSUNG SCX-4100 Series on USB:0 Flatbed Scanner

using sudo gscan2pdf i get the front end open, but i get segmentation fault when i ask to acquire;

What can be the problem?

Apologies for the late reply - was on holiday.

If scanimage --list-devices doesn't work without sudo, then there is something fundamental wrong with your scanner backend and gscan2pdf has no chance. I see there is bug on launchpad: [https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/116105](https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/116105)

It rather seems that the backend is closed-source, supplied by Samsung, so you might not get an solution.

Start gscan2pdf with ```
sudo gscan2pdf --debug
``` and post the output from the command line.

---

### Post by lonal on 2007-09-29
i've got the same problem...
i noticed that starting gscan2pdf with sudo in a terminal allows the program to see my scanner
(samsung scx-4521f) but it still doesn't work
here it is my sudo gscan2pdf --debug
thanks for help

```
gscan2pdf 0.9.16
Using it_IT.UTF-8 locale
Gtk2-Perl version 1.140
Built for 2.10.9
Running with 2.10.11
$VAR1 = {
          'ocr panel' => '530',
          'frontend' => 'scanimage',
          'author' => 'ranieri',
          'window_maximize' => '1',
          'keywords' => '',
          'downsample dpi' => '150',
          'layout' => 'single',
          'cwd' => '/home/tovograz/PDF',
          'window_width' => '1024',
          'window_x' => '0',
          'quality' => '75',
          'window_y' => '25',
          'date offset' => '0',
          'OCR on scan' => '',
          't' => '0',
          'thumb panel' => '128',
          'enable options' => '1',
          'Page range' => 'all',
          'subject' => '',
          'version' => '0.9.16',
          'window_height' => '693',
          'device' => 'smfp:SAMSUNG SCX-4x21 Series on USB:0',
          'startup warning' => '1',
          'l' => '0',
          'pages to scan' => 'all',
          'downsample' => '',
          'restore window' => '1',
          'title' => '',
          'unpaper on scan' => '',
          'pdf compression' => 'png'
        };
Found PDF::API2
Found Image::Magick
Found ImageMagick
Found scanadf
Found xdg-email
Found gocr
Found unpaper
Found libtiff
scanimage --formatted-device-list="'%i','%d','%v %m'
" 2>/dev/null
Forked PID 9868
Waiting to reap process at /usr/bin/gscan2pdf line 2732.
Reaped PID -1
'0','smfp:SAMSUNG SCX-4x21 Series on USB:0','SAMSUNG SCX-4x21 Series on USB:0'
scanimage --help --device-name='smfp:SAMSUNG SCX-4x21 Series on USB:0'
Forked PID 9947
Segmentation fault (core dumped)
Waiting to reap process at /usr/bin/gscan2pdf line 3733.
Reaped PID -1
Usage: scanimage [OPTION]...

Start image acquisition on a scanner device and write PNM image data to
standard output.

-d, --device-name=DEVICE   use a given scanner device (e.g. hp:/dev/scanner)
    --format=pnm|tiff      file format of output file
-i, --icc-profile=PROFILE  include this ICC profile into TIFF file
-L, --list-devices         show available scanner devices
-f, --formatted-device-list=FORMAT similar to -L, but the FORMAT of the output
                           can be specified: %d (device name), %v (vendor),
                           %m (model), %t (type), and %i (index number)
-b, --batch[=FORMAT]       working in batch mode, FORMAT is `out%d.pnm' or
                           `out%d.tif' by default depending on --format
    --batch-start=#        page number to start naming files with
    --batch-count=#        how many pages to scan in batch mode
    --batch-increment=#    increase number in filename by an amount of #
    --batch-double         increment page number by two for 2sided orig at /usr/bin/gscan2pdf line 3739.
$VAR1 = {};
$VAR1 = {};
scanimage --device-name='smfp:SAMSUNG SCX-4x21 Series on USB:0' --batch 
Forked PID 9993
Messaggio sconosciuto: Segmentation fault (core dumped)
Waiting to reap process at /usr/bin/gscan2pdf line 3278.
Reaped PID 9993
scanadf --help --device-name='smfp:SAMSUNG SCX-4x21 Series on USB:0'
Forked PID 10040
Segmentation fault (core dumped)
Waiting to reap process at /usr/bin/gscan2pdf line 3733.
Reaped PID -1
Warning: something's wrong at /usr/bin/gscan2pdf line 3739.
substr outside of string at /usr/bin/gscan2pdf line 3767.
Use of uninitialized value in index at /usr/bin/gscan2pdf line 3768.
Use of uninitialized value in length at /usr/bin/gscan2pdf line 3768.
Use of uninitialized value in substr at /usr/bin/gscan2pdf line 3768.
$VAR1 = {};
$VAR1 = {};
scanadf --device-name='smfp:SAMSUNG SCX-4x21 Series on USB:0' -o out%d.pnm --start-count=1  > /dev/stderr
Forked PID 10082
Messaggio sconosciuto: Segmentation fault (core dumped)
Waiting to reap process at /usr/bin/gscan2pdf line 3408.
Reaped PID 10082

```

---

### Post by RSkog on 2007-09-29
The problem with xsane, scanimage etc throwing a segmentation fault for the Samsung printers has to do with the driver accessing io ports, that only root has access to. 

See the post at [http://ubuntuforums.org/showthread.php?t=563159](http://ubuntuforums.org/showthread.php?t=563159) on how to replace the driver with a patched one that allows you to use the scanner without having to sudo.

keywords: segmentation fault, Samsung SCX-4521F, scan, scanner, driver, install

I don't know however if this will allow you to use the pdf script.

/Richard

---

### Post by JeffreyRatcliffe on 2007-10-01
> **RSkog said:**
> The problem with xsane, scanimage etc throwing a segmentation fault for the Samsung printers has to do with the driver accessing io ports, that only root has access to. 

See the post at [http://ubuntuforums.org/showthread.php?t=563159](http://ubuntuforums.org/showthread.php?t=563159) on how to replace the driver with a patched one that allows you to use the scanner without having to sudo.

Thanks for this. Provided scanimage or scanadf produces sensible output, gscan2pdf should work.

---

### Post by JeffreyRatcliffe on 2007-10-02
Following the open source edict of "Release early, release often", I have uploaded version 0.9.17 of my utility gscan2pdf to [http://sourceforge.net/projects/gscan2pdf](http://sourceforge.net/projects/gscan2pdf).

Changes:
+ cut, copy and paste of pages
  Closes Feature Request 1780866 (Cut/copy/paste editing functions)
+ multiple-item drag-and-drop, including copy.
  Closes Feature Request 1743098 (Improved drag'n'drop reordering of pages)
+ fixed bug saving DjVu with 2 pages
+ ProgressBar during scan
+ extended page numbering to scan dialog
+ Update to Czech translation (thanks to Petr Jelínek)
+ Update to Danish translation (thanks to Jacob Nielsen)
+ Update to German translation (thanks to Matthias Gutjahr)
+ Added Greek translation (thanks to Spartakus)
+ Update to French translation (thanks to Nicolas Stransky)
+ Update to Italian translation (thanks to Andrea (pikkio))
+ Update to Polish translation (thanks to Piotr Str&#281;bski)
+ Update to Russian translation (thanks to Alexandre Prokoudine)
+ Update to Spanish translation (thanks to Yözen Hernández)
+ Relicensed under GPLv3

Just add the following line to your /etc/apt/sources.list:```
deb http://gscan2pdf.sourceforge.net/download/debian binary/
```
If you are you are using Synaptic, then use menu Edit/Reload Package Information, search for gscan2pdf in the package list, and lo and behold, you can install the nice shiny new version automatically.

From the command line:```
sudo apt-get update
sudo apt-get install gscan2pdf
```

If you add my key to your list of trusted keys, then you will no longer get the "not authenticated" warnings:```
gpg --keyserver www.keyserver.net --recv-keys 4DD7CC93
gpg --export --armor 4DD7CC93 | sudo apt-key add -
```

The dependencies are libgtk2-perl (>= 1:1.043-1), libgtk2-ex-simple-list-perl, perlmagick, libpdf-api2-perl, liblocale-gettext-perl (>= 1.05), libsane, sane-utils, libtiff-tools.

The help will require Gtk2::Ex::PodViewer. The scanadf frontend is in sane. For Email as PDF, you need xdg-utils. OCR requires gocr, or better tesseract. Having installed gscan2pdf, locate the gscan2pdf entry in Synaptic, right-click it and you can install them under "Recommends".

If anybody fancies translating gscan2pdf into any other languages, they are welcome to do so on Rosetta ([https://launchpad.net/products/gscan2pdf/trunk/+pots/gscan2pdf](https://launchpad.net/products/gscan2pdf/trunk/+pots/gscan2pdf))

---

### Post by kafkaian on 2007-10-15
I will do a --debug if necessary but what's the word this working on 7.04 or 7.10? After successive upgrades the once superb (on Dapper) gscan2pdf has ground to a halt becoming very slow and inefficient to use.

---

### Post by David Valentine on 2007-10-15
> **kafkaian said:**
> I will do a --debug if necessary but what's the word this working on 7.04 or 7.10? After successive upgrades the once superb (on Dapper) gscan2pdf has ground to a halt becoming very slow and inefficient to use.I suppose everyone has their own experience, but mine has been, and continues to be, very positive.

---

### Post by JeffreyRatcliffe on 2007-10-16
> **kafkaian said:**
> I will do a --debug if necessary but what's the word this working on 7.04 or 7.10? After successive upgrades the once superb (on Dapper) gscan2pdf has ground to a halt becoming very slow and inefficient to use.

I did reply to your post:

> I've not noticed any problems with speed. Are you talking about upgrading from 0.9.15->0.9.16, or did you upgrade from an earlier version?

Is the speed problem just while scanning. i.e. do you have it when the app is sitting open doing nothing?

I can't see any problems with the --debug output.

The point is - either the problem is with gscan2pdf itself, in which case installing successively older versions from the website until the speed is acceptable will give me an idea what the cause might be. Alternatively, if the problem is to do with something else, e.g. the scanner driver, then an old version will have the same speed problem.

What machine are you running it on? On my Pentium D, everything is fine.

---

### Post by kafkaian on 2007-10-16
> **JeffreyRatcliffe said:**
> I did reply to your post:



The point is - either the problem is with gscan2pdf itself, in which case installing successively older versions from the website until the speed is acceptable will give me an idea what the cause might be. Alternatively, if the problem is to do with something else, e.g. the scanner driver, then an old version will have the same speed problem.

What machine are you running it on? On my Pentium D, everything is fine.

Apologies Jeffrey. Didn't meant to double post, just slipped my mind that I had done this on this forum before. Probably meant to go back and forgot.

I have a dual core Pentium 4, 3 GHz. A couple of years old now but this was great on Dapper, and Edgy if I remember but I can't decide at what point I lost it as I was doing all sorts of upgrades without testing gscan. I think I'll regress and see how it goes and report back.

And yes the slow down really is more during scanning than when it is sitting idle

---

### Post by mavila on 2007-10-25
I had been using this under feisty with an Avision AV210. The 'scan' dialog used to give me a couple of options on setting paper sizes manually (there is now only a4, letter, and legal choices) and resolution (most important to me).

For whatever reason I dont have these choices under Gutsy. I ended up doing a complete fresh install on a new drive however, so Im pretty sure that its a driver issue. Can you point me int the right direction so I can get the scanner options back?

thanks

---

### Post by JeffreyRatcliffe on 2007-10-25
> **mavila said:**
> For whatever reason I dont have these choices under Gutsy. I ended up doing a complete fresh install on a new drive however, so Im pretty sure that its a driver issue. Can you point me int the right direction so I can get the scanner options back?

What version have you got under Gutsy? v0.9.13 is now in Universe, but this is very old. 0.9.17 is available from the gscan2pdf website on Sourceforge.

---

### Post by mavila on 2007-10-26
Jeffry - thanks for the tip. I have 0.9.13 (thats whats in the Gutsy repository) on this system. I honestly dont remember what version I had installed on Feisty (but I can still boot that and figure it our). In hindsight I may have done just what you suggested - download the latest version from Sourceforge, and will do that.

Greatly appreciate the direction...

*** update *** Jeffry - that was the ticket to getting the additional settings back. FOr whatever reason, 0.9.13 seems to be whats in teh standard repositories... upgrading to 0.9.17 added the feature I was looking for.

Greatly appreciated!

Matt

---

### Post by kafkaian on 2007-10-29
> **kafkaian said:**
> Apologies Jeffrey. Didn't meant to double post, just slipped my mind that I had done this on this forum before. Probably meant to go back and forgot.

I have a dual core Pentium 4, 3 GHz. A couple of years old now but this was great on Dapper, and Edgy if I remember but I can't decide at what point I lost it as I was doing all sorts of upgrades without testing gscan. I think I'll regress and see how it goes and report back.

And yes the slow down really is more during scanning than when it is sitting idle

These issues have now resolved since fully upgrading to Gutsy. Basically I had the development/kernel only version of 7.10 and since allowing Synaptic to upgrade having returned from India last night, everything is as was i.e. beautifully quick and very efficient.:guitar::)

---

### Post by Stinger on 2007-11-05
Hi , thanks for an excellent application to scan multi page documents.
I would like to propose a couple of suggestions for your application for making it even better.

1. use [tiff2pdf]("http://remotesensing.org/libtiff/man/tiff2pdf.1.html") for creating pdfs with an even smaller footprint using the tiff compressions.

2. Adding a preview window like xsane to crop images before scanning.

---

### Post by JeffreyRatcliffe on 2007-11-05
> **Stinger said:**
> 1. use [tiff2pdf]("http://remotesensing.org/libtiff/man/tiff2pdf.1.html") for creating pdfs with an even smaller footprint using the tiff compressions.

2. Adding a preview window like xsane to crop images before scanning.

Originally, gscan2pdf DID use tiff2pdf. However, then there is no possibility to embed OCR output in the PDF. I will, however, look at the possibility of embedding the image at a TIFF with the tiffcp compression options, which should achieve what you want.

Have you tried the DjVu output? The file size is MUCH better than PDF.

Image cropping has been on my todo list for some time.

---

### Post by Stinger on 2007-11-05
> **JeffreyRatcliffe said:**
> Originally, gscan2pdf DID use tiff2pdf. However, then there is no possibility to embed OCR output in the PDF. I will, however, look at the possibility of embedding the image at a TIFF with the tiffcp compression options, which should achieve what you want.

Have you tried the DjVu output? The file size is MUCH better than PDF.

Image cropping has been on my todo list for some time.

Thanks for taking time to answer.
I see your point about OCR output and I'm glad to see you will look at the possibility to embed the image as a TIFF with tiffcp.

I have just tried the DjVu output , I must say I'm impressed , just scanned 5 pages and saved them as PDF , TIFF ad DjVu , file size where: PDF 695kb , TIFF 159kb and DjVu 78kb , the result speaks for it self , 
Maybe DjVu is what I want ? is there a way to convert DjVu to PDF if I want to email a document later on ?

small notice
gscan2pdf seems to be able to create DjVu but not able to import it.

Question: will gscan2pdf be able to produce color DjVu in the future ?

DjVu is a great format I just wasn't aware of it , thanks for pointing it out.

BTW do you know the Kodak Imaging software ? It was available as part of Windows installation from Win95 to Win2k but removed again in Winxp. If you do , you will know exactly what I'm trying to replace.

Thanks for gscan2pdf.

---

### Post by JeffreyRatcliffe on 2007-11-06
> **Stinger said:**
> Maybe DjVu is what I want ? is there a way to convert DjVu to PDF if I want to email a document later on ?

small notice
gscan2pdf seems to be able to create DjVu but not able to import it.

Question: will gscan2pdf be able to produce color DjVu in the future ?

DjVuPhoto compression is already in the upcoming release, as is DjVu import. In the mean time, djvu2pdf should do what you want.

> **Stinger said:**
> BTW do you know the Kodak Imaging software ? It was available as part of Windows installation from Win95 to Win2k but removed again in Winxp. If you do , you will know exactly what I'm trying to replace.

Yes. The original description of gscan2pdf was to be a replacement for Imaging. I removed the reference when I found that there were features I wanted that weren't in Imaging, and vice versa.

---

### Post by Stinger on 2007-11-07
> **JeffreyRatcliffe said:**
> DjVuPhoto compression is already in the upcoming release, as is DjVu import. In the mean time, djvu2pdf should do what you want.

I can see you are way ahead of me :) thanks.

> **JeffreyRatcliffe said:**
> Yes. The original description of gscan2pdf was to be a replacement for Imaging. I removed the reference when I found that there were features I wanted that weren't in Imaging, and vice versa.

Some features I like about Imaging is the ability to add text and lines to the image , you can highlight areas of the image , you can cut and paste in your image. the last feature I use a lot , I have two sessions of Imaging running , cut from one image and paste to another ( both scanned as lineart ).
When I'm done editing I have a small tiff containing eg. highlights and added text [COLOR="Red"] but only if I use Imaging to open it ![/COLOR] if I use eye of gnome or GIMP instead I only get the image and not the highlighted areas and the added text.
So to use the features of Imaging I have an old machine running win2k.To export to others I use [PrimoPDF]("http://www.primopdf.com/") to create a pdf file for eg. email.

For most of my documents gscan2pdf is the number one choice and I like DjVu a lot.

gscan2pdf has a lot of useful features that Imaging does not eg. PDF , DjVu and OCR.
Imagine if these two powerful tools could be combined... it would be the most powerful document / image tool available..

Thanks a lot for your help.

---

### Post by JeffreyRatcliffe on 2007-11-08
> **Stinger said:**
> Some features I like about Imaging is the ability to add text and lines to the image , you can highlight areas of the image , you can cut and paste in your image. the last feature I use a lot , I have two sessions of Imaging running , cut from one image and paste to another ( both scanned as lineart ).
When I'm done editing I have a small tiff containing eg. highlights and added text [COLOR="Red"] but only if I use Imaging to open it ![/COLOR] if I use eye of gnome or GIMP instead I only get the image and not the highlighted areas and the added text.

There are two separate points here both of which will get into gscan2pdf when I've worked out the details. The first will be cutting (cropping) and pasting portions of the image. This I would myself find occasionally useful.

The ability to add text to the image depends upon tesseract. At the moment, the OCR output is embedded in point 1 text, simply to make sure that it all fits on the page. As soon as tesseract supports a simple way of exporting the text position, as well as the text itself, I will embed the text in the correct position with the correct size. Highlighting will follow from that. This I consider just a really cool feature to have, rather than particularly useful.

---

### Post by stoodleysnow on 2007-11-08
Scan with Xsane, save as PNG, open with OpenOffice.org Draw, edit if necessary and save as PDF.:)

---

### Post by JeffreyRatcliffe on 2007-11-08
> **stoodleysnow said:**
> Scan with Xsane, save as PNG, open with OpenOffice.org Draw, edit if necessary and save as PDF.:)

You can scan direct from OODraw. The DjVu, embedded OCR output, etc., you can't.

---

### Post by Stinger on 2007-11-09
> **JeffreyRatcliffe said:**
> There are two separate points here both of which will get into gscan2pdf when I've worked out the details. The first will be cutting (cropping) and pasting portions of the image. This I would myself find occasionally useful.

The ability to add text to the image depends upon tesseract. At the moment, the OCR output is embedded in point 1 text, simply to make sure that it all fits on the page. As soon as tesseract supports a simple way of exporting the text position, as well as the text itself, I will embed the text in the correct position with the correct size. Highlighting will follow from that. This I consider just a really cool feature to have, rather than particularly useful.

Thanks again for taking time to look at my postings.

I'm very glad that you consider some of my ideas and thats what it is , ideas , you decide what goes where and when. ;)

OCR is not a priority for me , but I can show you what I can do in Imaging , I have attached 7 shots.

1 and 2 is cut and paste , 3 is adding text , 4 is the highlighter , 5 adding an line , 6 rubber stamp and 7 the output from the PDF printer.
I like the bottom toolbar from Imaging.

---

### Post by Stinger on 2007-11-09
And here the two last shots.
As you can see there is an error from the PDF printer , the highlighted area should be behind the image.

---

### Post by JeffreyRatcliffe on 2007-11-09
> **Stinger said:**
> OCR is not a priority for me , but I can show you what I can do in Imaging , I have attached 7 shots.

These sort of features will require quite large changes to gscan2pdf, and at the moment, I don't know how to realise them. As stoodleysnow has already pointed out, your best bet for marking up scans at the moment is OODraw (or perhaps Inkscape).

---

### Post by JeffreyRatcliffe on 2007-11-16
Following the open source edict of "Release early, release often", I have uploaded version 0.9.18 of my utility gscan2pdf to [http://sourceforge.net/projects/gscan2pdf](http://sourceforge.net/projects/gscan2pdf).

Changes:
+ recoded DjVu save
+ Photo compression to DjVu output. Respect! Miles better than JPEG
+ DjVu import
+ PS to save as image options
+ Split options in scan dialog into two tabs.
  Closes bug 1812030 (Dialog Box Too Big to fit on screen)
+ build scan window before scanning for devices in order to make sure that
  it centres properly.
  Closes Debian bug #440902: window placement of scan dialog
+ djvu compression automatic on image depth to allow multiple pages with
  different compression for each page
+ TIFF compression options to PDF output
  Closes bug 1803099 (created PDF files are huge)
+ threshold tool.
  Closes feature request 1750849 (RFE: support software controlled contrast)
+ paper size editor
+ detect if destination directory is read-only
  Closes 1829961 (Crash saving .pdf in r/o subdirectory using v0.9.17)
+ reset start page number in scan dialog after deleting a page
+ Update to Czech translation (thanks to Petr Jelínek)
+ Update to French translation (thanks to Nicolas Stransky)
+ Update to German translation (thanks to Matthias Gutjahr)
+ Update to Greek translation (thanks to Ioannis Koniaris)
+ Update to Polish translation (thanks to Brech)
+ Update to Russian translation (thanks to Alexandre Prokoudine)

Just add the following line to your /etc/apt/sources.list:```
deb http://gscan2pdf.sourceforge.net/download/debian binary/
```
If you are you are using Synaptic, then use menu Edit/Reload Package Information, search for gscan2pdf in the package list, and lo and behold, you can install the nice shiny new version automatically.

From the command line:```
sudo apt-get update
sudo apt-get install gscan2pdf
```

If you add my key to your list of trusted keys, then you will no longer get the "not authenticated" warnings:```
gpg --keyserver www.keyserver.net --recv-keys 4DD7CC93
gpg --export --armor 4DD7CC93 | sudo apt-key add -
```

The dependencies are libgtk2-perl (>= 1:1.090), libgtk2-ex-simple-list-perl, perlmagick, libpdf-api2-perl, liblocale-gettext-perl (>= 1.05), libsane, sane-utils, libtiff-tools.

The help will require Gtk2::Ex::PodViewer. The scanadf frontend is in sane. For Email as PDF, you need xdg-utils. OCR requires gocr, or better tesseract. Having installed gscan2pdf, locate the gscan2pdf entry in Synaptic, right-click it and you can install them under "Recommends".

If anybody fancies translating gscan2pdf into any other languages, they are welcome to do so on Rosetta ([https://launchpad.net/products/gscan2pdf/trunk/+pots/gscan2pdf](https://launchpad.net/products/gscan2pdf/trunk/+pots/gscan2pdf))

---

### Post by pneaveill on 2007-11-17
Jeff and all

Just want to say a big thanks for all the hard work on this project. I am happy to report that I downloaded and installed the program to scan from my HP OJ 7110 and it ran first time. Woo hoo. Now to get it working on wife's computer. . . .

---

### Post by JeffreyRatcliffe on 2007-11-19
Following the open source edict of "Release early, release often", I have uploaded version 0.9.19 of my utility gscan2pdf to [http://sourceforge.net/projects/gscan2pdf](http://sourceforge.net/projects/gscan2pdf).

Changes:
+ fixed bug creating user-defined paper sizes

Just add the following line to your /etc/apt/sources.list:```
deb http://gscan2pdf.sourceforge.net/download/debian binary/
```
If you are you are using Synaptic, then use menu Edit/Reload Package Information, search for gscan2pdf in the package list, and lo and behold, you can install the nice shiny new version automatically.

From the command line:```
sudo apt-get update
sudo apt-get install gscan2pdf
```

If you add my key to your list of trusted keys, then you will no longer get the "not authenticated" warnings:```
gpg --keyserver www.keyserver.net --recv-keys 4DD7CC93
gpg --export --armor 4DD7CC93 | sudo apt-key add -
```

The dependencies are libgtk2-perl (>= 1:1.090), libgtk2-ex-simple-list-perl, perlmagick, libpdf-api2-perl, liblocale-gettext-perl (>= 1.05), libsane, sane-utils, libtiff-tools.

The help will require Gtk2::Ex::PodViewer. The scanadf frontend is in sane. For Email as PDF, you need xdg-utils. OCR requires gocr, or better tesseract. Having installed gscan2pdf, locate the gscan2pdf entry in Synaptic, right-click it and you can install them under "Recommends".

If anybody fancies translating gscan2pdf into any other languages, they are welcome to do so on Rosetta ([https://launchpad.net/products/gscan2pdf/trunk/+pots/gscan2pdf](https://launchpad.net/products/gscan2pdf/trunk/+pots/gscan2pdf))

---

### Post by moshuptrail on 2007-11-21
Hey Jeffrey -
Kudos.  I have been using since the beginning.  Great stuff. 
But something broke in the last month or so.
Using HP Officejet v40 to scan, I am getting the following:
Unknown message: scanimage: setting of option --br-x failed (Invalid argument)

The newest version did not fix or cause this, but I'm not sure when it cropped up.
I think it's been about a month since last time I scanned.

---

### Post by JeffreyRatcliffe on 2007-11-21
[QUOTE=moshuptrail]Using HP Officejet v40 to scan, I am getting the following:
Unknown message: scanimage: setting of option --br-x failed (Invalid argument)[/QUOTE]

Thanks for providing me with the --debug output. The problem, I assume is ```
    -x 0..215.9mm [215.9]
        Width of scan-area.
```

But you attempted a scan that was 216 wide. Previously, I had complaints that gscan2pdf wouldn't scan 216 if the scanner said it could do 215.9, so I added a 1mm tolerance. Seems this is biting me back.

Please confirm this by changing the paper size to 215 and trying to scan.

---

### Post by moshuptrail on 2007-11-21
That was it, exactly. 
But I had to manually edit the .gscan2pdf file.  I was not able to find anything in the UI to adjust the paper size.  Am I missing something?  But it was back at 216!  One of the updates must have diddled it.
All fixed now.
Thanks.  This program is better than anything I'm aware of, even for Windows. (i.e. licensed at a horrific price)

---

### Post by JeffreyRatcliffe on 2007-11-22
> **moshuptrail said:**
> But I had to manually edit the .gscan2pdf file.  I was not able to find anything in the UI to adjust the paper size.  Am I missing something?  But it was back at 216!

New in 0.9.19 is the ability to edit the paper sizes. Change the paper size to Edit, and you'll get a dialog where a double-click will allow you to change the size or the name, etc.

Thanks for the feedback. I'll change the code so that in a case like yours, gscan2pdf would ask for a 215.9 wide scan.

---

### Post by Blankman on 2007-12-06
Thanks for all your efforts on this - a 400+ thread, that's patience for you!  As a result of the thread size, I hope I am not duplicating a query. 

I am running Ubuntu 6.06 LTS - Dapper Drake; Printer/Scanner being used: HP Photosmart C5280 All-in-One

1.  Presently I scan documents in via Xsane 0.97, save each individual document as a .tiff document and then use your software (gscan2pdf 0.9.19) to collate the multiple individual .tiff pages into one document and convert to a PDF.  The reason for this long winded approach to converting multiple page to a single PDF document is that I am unable to scan using gscan2pdf 0.9.19 - although the software does identify my printer.  The warning message received is: *Unknown message: scanimage: setting of option --br-y failed (Invalid argument)*.  Any thoughts? An idiots guide would be good - as you will note from the next query.

2.  I thought that perhaps the "Help" feature would assist.  Unfortunately I cannot open it.  The error message reads: *The help viewer requires module Gtk2::Ex::PodViewer Alternatively, try: gscan2pdf --help"*.  I have tried to locate Gtk2::Ex::PodViewer in Synaptic but its not there.  I have also tried to run *sudo apt-get gscan2pdf --help* in the terminal but obviously didn't get the right result - perhaps because I am a bit of a muppet and still trying to find my way around Linux, in which case please forgive what could be a rather obvious answer!

Thanks for all your efforts so far!

---

### Post by JeffreyRatcliffe on 2007-12-06
> **Blankman said:**
> I am unable to scan using gscan2pdf 0.9.19 - although the software does identify my printer.  The warning message received is: *Unknown message: scanimage: setting of option --br-y failed (Invalid argument)*.  Any thoughts? An idiots guide would be good - as you will note from the next query.

If you start gscan2pdf with ```
gscan2pdf --debug
``` try to scan, and post the output from the command line to ra28145 at sf.users.net, I'll take a look.

> **Blankman said:**
> 2.  I thought that perhaps the "Help" feature would assist.  Unfortunately I cannot open it.  The error message reads: *The help viewer requires module Gtk2::Ex::PodViewer Alternatively, try: gscan2pdf --help"*.  I have tried to locate Gtk2::Ex::PodViewer in Synaptic but its not there.  I have also tried to run *sudo apt-get gscan2pdf --help* in the terminal but obviously didn't get the right result

libgtk2-ex-podviewer-perl is the name of the Gtk2::Ex::PodViewer package.

Alternatively, the help can be viewed with ```
gscan2pdf --help
``` or ```
man gscan2pdf
``` or [http://gscan2pdf.sourceforge.net/](http://gscan2pdf.sourceforge.net/)

---

### Post by Fitzcarraldo on 2007-12-15
I use both Ubuntu and Sabayon Linux, and have installed gscan2pdf under Sabayon. It works very well and is exactly what I was looking for. Thanks for a great application, Jeffrey.

[http://www.sabayonlinux.org/forum/viewtopic.php?f=54&t=11875](http://www.sabayonlinux.org/forum/viewtopic.php?f=54&t=11875)

---

### Post by JeffreyRatcliffe on 2007-12-15
Thanks for the feedback.

I didn't know that Linux Magazine had run the article on gscan2pdf. What did they say?

---

### Post by sybille on 2007-12-15
Here's a link to a copy of the Linux Magazine article:
[http://w3.linux-magazine.com/issue/85/Electronic_Document_Archives_with_Gscan2pdf.pdf](http://w3.linux-magazine.com/issue/85/Electronic_Document_Archives_with_Gscan2pdf.pdf)
(It's a pdf file.)

---

### Post by JeffreyRatcliffe on 2007-12-15
> **sybille said:**
> Here's a link to a copy of the Linux Magazine article:
[http://w3.linux-magazine.com/issue/85/Electronic_Document_Archives_with_Gscan2pdf.pdf](http://w3.linux-magazine.com/issue/85/Electronic_Document_Archives_with_Gscan2pdf.pdf)
(It's a pdf file.)

Ah. Thanks!

Just out of interest - would a scan preview be that interesting? Also software controls for contrast and brightness for those scanners for which SANE doesn't offer options?

---

### Post by Fitzcarraldo on 2007-12-15
I don't miss a scan preview facility and, given the purpose of gscan2pdf, I was a little surprised that the article mentioned it. I suppose a scan preview would only be of much use if one also has the ability to select a smaller area of a page for scanning, rather than scanning the entire page (e.g. scanning an article on a newspaper page).

Contrast and brightness controls might be useful in certain cases I suppose although, to be honest, I can't recall ever needing to use such controls when using scanning programs that have them.

---

### Post by dominics on 2007-12-18
Hi Jeffrey, 


I cant seem to install gscan2pdf. I get the following message when  I attempt to install using apt-get install gscan2pdf.

This is the output I receive:

dom@dom-laptop:~$ sudo apt-get install gscan2pdf
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  gscan2pdf: Depends: sane-utils but it is not installable
             Depends: libtiff-tools but it is not installable
             Depends: libpdf-api2-perl but it is not installable
             Depends: libconfig-general-perl but it is not installable
             Depends: perlmagick but it is not installable
             Depends: imagemagick but it is not installable
E: Broken packages

Any ideas? 

Thanks 

Dom

---

### Post by FuturePilot on 2007-12-18
Can you post your sources.list
```
cat /etc/apt/sources.list
```

---

### Post by dominics on 2007-12-19
Finally got it to install. Took one look at the sources list and found most were commented out. Once uncommented and system updated, gscan2pdf installed straight away.

Thanks

Dom

---

### Post by sybille on 2007-12-19
If you're not using it, you might think of adding the gscan2pdf sourceforge repository. With it, you will be sure to have the newest version.

Instructions for adding the repository and its gpg key can be found here:
[http://gscan2pdf.sourceforge.net/](http://gscan2pdf.sourceforge.net/)
(Scroll to the Debian-based download instructions.)

---

### Post by pneaveill on 2007-12-19
As stated a few weeks ago, my compter worked fine with it, but never did get wife's computer to work with gscan. 

Wife's computer P-4, 768mb RAM and HP psc 1310 running 0.9.19

Unknown message: scanimage: setting of option --br-y failed (Invalid argument)

what else do you need to know?

---

### Post by JeffreyRatcliffe on 2007-12-20
> **pneaveill said:**
> Unknown message: scanimage: setting of option --br-y failed (Invalid argument)

what else do you need to know?

To be certain, the output from ```
gscan2pdf --debug
``` after you have tried to scan, but there is a bug in gscan2pdf 0.9.19 where that error message is produced if you try to scan a larger size than the scanner can cope with. i.e. try reducing the page size.

---

### Post by pneaveill on 2007-12-20
gscan2pdf --debug
gscan2pdf 0.9.19
Using C locale
:US Legal:
:US Letter:
:A4:
Gtk2-Perl version 1.140
Built for 2.10.9
Running with 2.12.0
$VAR1 = {
          'no-blackfilter' => '',
          'ocr panel' => '752',
          'frontend' => 'scanadf',
          'Paper' => {
                       'US Legal' => {
                                       'l' => '0',
                                       'y' => '356',
                                       'x' => '216',
                                       't' => '0'
                                     },
                       'US Letter' => {
                                        'l' => '0',
                                        'y' => '279',
                                        'x' => '216',
                                        't' => '0'
                                      },
                       'A4' => {
                                 'l' => '0',
                                 'y' => '297',
                                 'x' => '210',
                                 't' => '0'
                               }
                     },
          'mode' => 'Color',
          'window_maximize' => '1',
          'ocr engine' => 'gocr',
          'no-border-scan' => '',
          'no-blurfilter' => '',
          'white-threshold' => '0.9',
          'layout' => 'single',
          'cwd' => '/home/**user**',
          't' => '0',
          'OCR on scan' => '',
          'Paper size' => 'US Letter',
          'Page range' => 'all',
          'no-deskew' => '',
          'window_height' => '953',
          'startup warning' => '1',
          'no-grayfilter' => '',
          'pages to scan' => '1',
          'resolution' => '75',
          'no-border-align' => '',
          'unpaper on scan' => '',
          'source' => 'Flatbed',
          'downsample dpi' => '150',
          'compression' => 'JPEG',
          'window_width' => '1280',
          'deskew-scan-direction' => 'left,right',
          'window_x' => '0',
          'threshold tool' => '80',
          'window_y' => '25',
          'thumb panel' => '160',
          'enable options' => '1',
          'version' => '0.9.19',
          'device' => 'hpaio:/usb/psc_1310_series?serial=MY41J1D14PO2',
          'no-noisefilter' => '',
          'l' => '0',
          'no-mask-scan' => '',
          'downsample' => '',
          'black-threshold' => '0.33',
          'restore window' => '1',
          'batch-scan' => 'no'
        };
Found PDF::API2
Found Image::Magick
Found ImageMagick
Found scanadf
Found xdg-email
Found gocr
Found cjb2 (djvu)
Found unpaper
Found libtiff

---

### Post by JeffreyRatcliffe on 2007-12-21
> **pneaveill said:**
> gscan2pdf --debug

Please start with

```
gscan2pdf --debug
```

and post the output from the commandline **after** you have tried to scan.

---

### Post by pneaveill on 2007-12-21
Inching forward . . .

I tried it again at letter=216*279; and a4=210*297

both of them gave same results as last time.

tried narrrowing it to 210*270 and **got *.pdf**, but the text at the bottom was gibbereish:confused:

thanks in advance

---

### Post by JeffreyRatcliffe on 2007-12-21
> **pneaveill said:**
> tried narrrowing it to 210*270 and **got *.pdf**, but the text at the bottom was gibbereish:confused:

Do you mean that the scan itself was OK, but that the OCR output was gibberish?

---

### Post by pneaveill on 2007-12-21
> **JeffreyRatcliffe said:**
> Do you mean that the scan itself was OK, but that the OCR output was gibberish?

Affirm pic is fine, text is gibberish -- if, and only if, I physically change the settings

---

### Post by JeffreyRatcliffe on 2007-12-22
> **pneaveill said:**
> Affirm pic is fine, text is gibberish -- if, and only if, I physically change the settings

That generally comes of not using a high-enough resolution. I use 400dpi.

---

### Post by pneaveill on 2007-12-26
> **JeffreyRatcliffe said:**
> That generally comes of not using a high-enough resolution. I use 400dpi.

 Thanks. How do I change that?

---

### Post by JeffreyRatcliffe on 2007-12-27
> **pneaveill said:**
> Thanks. How do I change that?

On the scan dialog. If you are using v0.9.19, then it is on the second tab, labelled "Scan Options" (the first tab being labelled "Page Options").

It looks from your previous output as though you are currently using 75dpi.

---

### Post by kafkaian on 2008-01-11
I currently have a problem with Scan Options --> Paper Size in that the A4 default is all I can get. When the window moves into edit, one can enter new sizes but not choose them from the dropdown, only A4.

Perhaps my old scanner is limited but the older software versions used to work okay w.r.t. this:

Scanner - HPScanjet 4300
Version gscan2pdf 0.9.19
gscan2pdf 0.9.19
Using en_GB.UTF-8 locale
Gtk2-Perl version 1.140
Built for 2.10.9
Running with 2.12.0
$VAR1 = {
          'Paper' => {
                       'US Legal' => {
                                     'l' => 0,
                                     'y' => 356,
                                     'x' => 216,
                                     't' => 0
                                   },
                       'US Letter' => {
                                      'l' => 0,
                                      'y' => 279,
                                      'x' => 216,
                                      't' => 0
                                    },
                       'A4' => {
                               'l' => 0,
                               'y' => 297,
                               'x' => 210,
                               't' => 0
                             }
                     },
          'month' => '10',
          'mode' => 'Color',
          'author' => '',
          'x' => '210',
          'window_maximize' => '1',
          'downsample dpi' => 150,
          'y' => '297',
          'keywords' => '',
          'compression' => 'None',
          'layout' => 'single',
          'window_width' => '800',
          'cwd' => '/home/ian/Desktop',
          'day' => '19',
          'threshold tool' => 80,
          'window_x' => '0',
          'window_y' => '0',
          't' => 0,
          'thumb panel' => '412',
          'Paper size' => 'A4',
          'Page range' => 'all',
          'subject' => '',
          'window_height' => '600',
          'device' => 'niash:libusb:003:002',
          'l' => 0,
          'downsample' => '',
          'pages to scan' => '1',
          'resolution' => '150',
          'title' => 'blahdeblah',
          'year' => '2006'
        };
Found PDF::API2
Found Image::Magick
Found ImageMagick
Found scanadf
Found xdg-email
Found gocr
Found cjb2 (djvu)
Found libtiff

---

### Post by JeffreyRatcliffe on 2008-01-11
> **kafkaian said:**
> I currently have a problem with Scan Options --> Paper Size in that the A4 default is all I can get. When the window moves into edit, one can enter new sizes but not choose them from the dropdown, only A4.

The dropdown will not display those sizes larger than the scanner can scan.

I've added a 'manual' option to the upcoming release which displays spinbuttons limited to the range the scanner can manage.

In the meantime, look at the output from scanimage --help, which displays in the -y and -x options what SANE thinks your scanner can do, and put numbers the same or smaller than this in for your page size

---

### Post by cytg on 2008-01-11
whats wrong with xsane ?

---

### Post by kafkaian on 2008-01-15
> **JeffreyRatcliffe said:**
> The dropdown will not display those sizes larger than the scanner can scan.

I've added a 'manual' option to the upcoming release which displays spinbuttons limited to the range the scanner can manage.

In the meantime, look at the output from scanimage --help, which displays in the -y and -x options what SANE thinks your scanner can do, and put numbers the same or smaller than this in for your page size

Thanks Jeffrey

---

### Post by JeffreyRatcliffe on 2008-01-19
Following the open source edict of "Release early, release often", I have uploaded version 0.9.20 of my utility gscan2pdf to [http://sourceforge.net/projects/gscan2pdf](http://sourceforge.net/projects/gscan2pdf).

Changes:
+ fixed bug where backslashes in text layer in djvu files not escaped.
+ made ctrl-x, ctrl-c, ctrl-v work in text buffer
+ suppressed multiple paper size editor windows
+ manual paper size
+ fixed bug trying to scan large paper size than scanner allows
+ warning message when paper sizes too big for scanner
+ recognise warm-up message from gt68xx driver
  Closes Debian bug #449421
+ cope with spaces in filename of image to save
  Closes Debian bug #457377
+ improve tesseract language file search
+ implement --pagewidth|height properly [2348533a4a6a]
  Closes Debian bug #457376 (gscan2pdf: Some paper sizes not available)
+ account for options that completely disappear or appear between modes
  Closes 1868985 (can't disable invalid options (e.g. threshold))
  Closes Debian bug #457249
   (gscan2pdf: Tries to set threshold option for color scans)
+ scanner.svg, pdf.svg, gscan2pdf.svg
- scanner.png, pdf.png, gscan2pdf.png
  Closes bug 1836312 (Tangoify Icons)
+ fixed bug parsing scanimage progress output
  Closes Debian bug #457375 (gscan2pdf: Nondeterministic duplex scanning)
+ ask when quitting if not all pages have been saved.
  Closes Debian bug #461058 (does not ask when quitting without saving the PDF)

Just add the following line to your /etc/apt/sources.list:```
deb http://gscan2pdf.sourceforge.net/download/debian binary/
```
If you are you are using Synaptic, then use menu Edit/Reload Package Information, search for gscan2pdf in the package list, and lo and behold, you can install the nice shiny new version automatically.

From the command line:```
sudo apt-get update
sudo apt-get install gscan2pdf
```

If you add my key to your list of trusted keys, then you will no longer get the "not authenticated" warnings:```
gpg --keyserver www.keyserver.net --recv-keys 4DD7CC93
gpg --export --armor 4DD7CC93 | sudo apt-key add -
```

The dependencies are libgtk2-perl (>= 1:1.090), libgtk2-ex-simple-list-perl, perlmagick, libpdf-api2-perl, liblocale-gettext-perl (>= 1.05), libsane, sane-utils, libtiff-tools.

The help will require Gtk2::Ex::PodViewer. The scanadf frontend is in sane. For Email as PDF, you need xdg-utils. OCR requires gocr, or better tesseract. Having installed gscan2pdf, locate the gscan2pdf entry in Synaptic, right-click it and you can install them under "Recommends".

If anybody fancies translating gscan2pdf into any other languages, they are welcome to do so on Rosetta ([https://launchpad.net/products/gscan2pdf/trunk/+pots/gscan2pdf](https://launchpad.net/products/gscan2pdf/trunk/+pots/gscan2pdf))

---

### Post by JeffreyRatcliffe on 2008-02-02
Following the open source edict of "Release early, release often", I have uploaded version 0.9.21 of my utility gscan2pdf to [http://sourceforge.net/projects/gscan2pdf](http://sourceforge.net/projects/gscan2pdf).

Changes:
+ ensure quit question only displayed once, rather than once per not-saved page
+ update selected/current/all heuristic
  Closes Debian bug #461859 (better selected/current/all heuristic)
+ reset start page in scan dialog after File/New selected
  Closes 1879331 (Choosing New file does not zero page count)
+ request page range when importing a PDF with more than one page
  Closes Debian bug #461076 (importing PDFs causes /tmp/ overflow)
+ File/Compress working files
+ fixed bug remembering setting where setting is first in a list
+ fixed bug where thumbs get unselected after saving
+ fixed wide character crash caused by translations containing utf8.
+ Initial Turkish translation (thanks to denz)
+ Update to Brazilian Portuguese translation (thanks to luther-x)
+ Update to Czech translation (thanks to Petr Jelínek)
+ Update to Greek translation (thanks to jimpap)
+ Update to Polish translation (thanks to nikt_taki)

Just add the following line to your /etc/apt/sources.list:```
deb http://gscan2pdf.sourceforge.net/download/debian binary/
```
If you are you are using Synaptic, then use menu Edit/Reload Package Information, search for gscan2pdf in the package list, and lo and behold, you can install the nice shiny new version automatically.

From the command line:```
sudo apt-get update
sudo apt-get install gscan2pdf
```

If you add my key to your list of trusted keys, then you will no longer get the "not authenticated" warnings:```
gpg --keyserver www.keyserver.net --recv-keys 4DD7CC93
gpg --export --armor 4DD7CC93 | sudo apt-key add -
```

The dependencies are libgtk2-perl (>= 1:1.090), libgtk2-ex-simple-list-perl, perlmagick, libpdf-api2-perl, liblocale-gettext-perl (>= 1.05), libsane, sane-utils, libtiff-tools.

The help will require Gtk2::Ex::PodViewer. The scanadf frontend is in sane. For Email as PDF, you need xdg-utils. OCR requires gocr, or better tesseract. Having installed gscan2pdf, locate the gscan2pdf entry in Synaptic, right-click it and you can install them under "Recommends".

If anybody fancies translating gscan2pdf into any other languages, they are welcome to do so on Rosetta ([https://launchpad.net/products/gscan2pdf/trunk/+pots/gscan2pdf](https://launchpad.net/products/gscan2pdf/trunk/+pots/gscan2pdf))

---

### Post by mrojas73 on 2008-02-02
> **JeffreyRatcliffe said:**
> Following the open source edict of "Release early, release often", I have uploaded version 0.9.21 of my utility gscan2pdf to [http://sourceforge.net/projects/gscan2pdf](http://sourceforge.net/projects/gscan2pdf).

Changes:
+ ensure quit question only displayed once, rather than once per not-saved page
+ update selected/current/all heuristic
  Closes Debian bug #461859 (better selected/current/all heuristic)
+ reset start page in scan dialog after File/New selected
  Closes 1879331 (Choosing New file does not zero page count)
+ request page range when importing a PDF with more than one page
  Closes Debian bug #461076 (importing PDFs causes /tmp/ overflow)
+ File/Compress working files
+ fixed bug remembering setting where setting is first in a list
+ fixed bug where thumbs get unselected after saving
+ fixed wide character crash caused by translations containing utf8.
+ Initial Turkish translation (thanks to denz)
+ Update to Brazilian Portuguese translation (thanks to luther-x)
+ Update to Czech translation (thanks to Petr Jelínek)
+ Update to Greek translation (thanks to jimpap)
+ Update to Polish translation (thanks to nikt_taki)

Just add the following line to your /etc/apt/sources.list:```
deb http://gscan2pdf.sourceforge.net/download/debian binary/
```
If you are you are using Synaptic, then use menu Edit/Reload Package Information, search for gscan2pdf in the package list, and lo and behold, you can install the nice shiny new version automatically.

From the command line:```
sudo apt-get update
sudo apt-get install gscan2pdf
```

If you add my key to your list of trusted keys, then you will no longer get the "not authenticated" warnings:```
gpg --keyserver www.keyserver.net --recv-keys 4DD7CC93
gpg --export --armor 4DD7CC93 | sudo apt-key add -
```

The dependencies are libgtk2-perl (>= 1:1.090), libgtk2-ex-simple-list-perl, perlmagick, libpdf-api2-perl, liblocale-gettext-perl (>= 1.05), libsane, sane-utils, libtiff-tools.

The help will require Gtk2::Ex::PodViewer. The scanadf frontend is in sane. For Email as PDF, you need xdg-utils. OCR requires gocr, or better tesseract. Having installed gscan2pdf, locate the gscan2pdf entry in Synaptic, right-click it and you can install them under "Recommends".

If anybody fancies translating gscan2pdf into any other languages, they are welcome to do so on Rosetta ([https://launchpad.net/products/gscan2pdf/trunk/+pots/gscan2pdf](https://launchpad.net/products/gscan2pdf/trunk/+pots/gscan2pdf))

It only gets better and better Jeffrey, thank you very much.

---

### Post by saabaero on 2008-02-05
thanks for this program. I'm trying as much as i can to translate it to Dutch.

---

### Post by JeffreyRatcliffe on 2008-02-05
> **saabaero said:**
> I'm trying as much as i can to translate it to Dutch.

Thanks!

---

### Post by saabaero on 2008-02-05
however, after testing the program, i think it would be very helpful (at least to me) if you could open a PDF file for example, and add pages by scanning. When I now import a PDF, i only get a few images.

this would make it a real pdf-writer!

---

### Post by JeffreyRatcliffe on 2008-02-05
> **saabaero said:**
> however, after testing the program, i think it would be very helpful (at least to me) if you could open a PDF file for example, and add pages by scanning. When I now import a PDF, i only get a few images.

The PDF import is meant to allow the program to read the files that it has read. It is completely beyond the scope of the program to be able to read all objects in the complete PDF spec.

I have, however, thought about an "append to PDF" option. This is, at least, not so hard.

---

### Post by saabaero on 2008-02-05
> **saabaero said:**
>  I'm trying as much as i can to translate it to Dutch.

at least 81% of the dutch language is translated correctly. I hope i helped somebody!

---

### Post by knathraak on 2008-02-14
Jeffrey,

I've been subscribed to this thread since I created it (about 2 1/2 years ago!) and have kept up with your project from a distance.  Shortly after my initial post, my need to scan to pdfs went away, so I never gave your program a try.  Now that I'm trying to go paperless, I've finally given it a go.  I just wanted to let you know that I really like it so far.

Thanks for the hard work on this.

Zach

---

### Post by JeffreyRatcliffe on 2008-03-05
Following the open source edict of "Release early, release often", I have uploaded version 0.9.22 of my utility gscan2pdf to [http://sourceforge.net/projects/gscan2pdf](http://sourceforge.net/projects/gscan2pdf).

Changes:
+ fixed incorrect error message when saving image
  Closes Debian bug #463708 (gscan2pdf: Error when saving as PNG)
+ Edit/Preferences to choose TMPDIR
+ moved Frontends, Save options and Restore window settings to Edit/Preferences
+ improve error messages saving PDF
+ unsharp mask tool
+ merged Save PDF, Save Image & Save DjVu dialogs
+ request page range when importing a DjVu with more than one page, and extract
  the pages singly
  Closes Debian bug #462171 (importing DjVu files fails, hogs memory)
+ replace some unpaper references with 'Clean up'
  Closes 1889896 ('unpaper' should be called something more clear)
+ prepopulate PDF filename with title
  Closes 1889901 (Use PDF 'Title' as the default file name in the save dialog)
+ change max number of pages to scan to 999
  Closes 1803801 (page # in document scan dialog show only number till 99)
+ use gtk+ set_do_overwrite_confirmation
+ prevent page range widget switching to all when deleting a page
+ progress bar whilst rotating
  Closes 1895947 (Show progress bar when rotating pages)
+ rotate options to scan dialog
  Closes 1889674 (Patch for Duplex Scanning)
+ fixed about dialog
+ use tiffcp rather than tiffsplit to import TIFFs
  Closes Debian bug #462171 (importing DjVu files fails, hogs memory)
+ Initial Slovenian translation (thanks to Robert Hrovat)
+ Update to Brazilian Portuguese translation (thanks to Manuel Rennecke)
+ Update to Czech translation (thanks to Petr Jelínek)
+ Update to Danish translation (thanks to Jacob Nielsen)
+ Update to Dutch translation (thanks to saabaero)
+ Update to French translation (thanks to Manuel Rennecke)
+ Update to German translation (thanks to Matthias Gutjahr)
+ Update to Portuguese translation (thanks to Manuel Rennecke)
+ Update to Russian translation (thanks to Alexandre Prokoudine)
+ Update to Spanish translation (thanks to Manuel Rennecke)
+ Update to Swedish translation (thanks to Poppe)
+ Update to Belarusian translation (thanks to booxter)
+ Update to Italian translation (thanks to Andrea (pikkio))
+ Update to Polish translation (thanks to Piotr Str&#281;bski)
+ Update to Traditional Chinese translation (thanks to Chien Cheng Wei)

Just add the following line to your /etc/apt/sources.list:```
deb http://gscan2pdf.sourceforge.net/download/debian binary/
```
If you are you are using Synaptic, then use menu Edit/Reload Package Information, search for gscan2pdf in the package list, and lo and behold, you can install the nice shiny new version automatically.

From the command line:```
sudo apt-get update
sudo apt-get install gscan2pdf
```

If you add my key to your list of trusted keys, then you will no longer get the "not authenticated" warnings:```
gpg --keyserver www.keyserver.net --recv-keys 4DD7CC93
gpg --export --armor 4DD7CC93 | sudo apt-key add -
```

The dependencies are libgtk2-perl (>= 1:1.090), libgtk2-ex-simple-list-perl, perlmagick, libpdf-api2-perl, liblocale-gettext-perl (>= 1.05), libsane, sane-utils, libtiff-tools.

The help will require Gtk2::Ex::PodViewer. The scanadf frontend is in sane. For Email as PDF, you need xdg-utils. OCR requires gocr, or better tesseract. Having installed gscan2pdf, locate the gscan2pdf entry in Synaptic, right-click it and you can install them under "Recommends".

If anybody fancies translating gscan2pdf into any other languages, they are welcome to do so on Rosetta ([https://launchpad.net/products/gscan2pdf/trunk/+pots/gscan2pdf](https://launchpad.net/products/gscan2pdf/trunk/+pots/gscan2pdf))

---

### Post by JeffreyRatcliffe on 2008-03-06
Following the open source edict of "Release early, release often", I have uploaded version 0.9.23 of my utility gscan2pdf to [http://sourceforge.net/projects/gscan2pdf](http://sourceforge.net/projects/gscan2pdf).

Changes:
+ fixed bug running unpaper
+ hide progress bar when asking for page range to import

Just add the following line to your /etc/apt/sources.list:```
deb http://gscan2pdf.sourceforge.net/download/debian binary/
```
If you are you are using Synaptic, then use menu Edit/Reload Package Information, search for gscan2pdf in the package list, and lo and behold, you can install the nice shiny new version automatically.

From the command line:```
sudo apt-get update
sudo apt-get install gscan2pdf
```

If you add my key to your list of trusted keys, then you will no longer get the "not authenticated" warnings:```
gpg --keyserver www.keyserver.net --recv-keys 4DD7CC93
gpg --export --armor 4DD7CC93 | sudo apt-key add -
```

The dependencies are libgtk2-perl (>= 1:1.090), libgtk2-ex-simple-list-perl, perlmagick, libpdf-api2-perl, liblocale-gettext-perl (>= 1.05), libsane, sane-utils, libtiff-tools.

The help will require Gtk2::Ex::PodViewer. The scanadf frontend is in sane. For Email as PDF, you need xdg-utils. OCR requires gocr, or better tesseract. Having installed gscan2pdf, locate the gscan2pdf entry in Synaptic, right-click it and you can install them under "Recommends".

If anybody fancies translating gscan2pdf into any other languages, they are welcome to do so on Rosetta ([https://launchpad.net/products/gscan2pdf/trunk/+pots/gscan2pdf](https://launchpad.net/products/gscan2pdf/trunk/+pots/gscan2pdf))

---

### Post by mwww on 2008-03-25
Jeffrey,

thanks for such a well maintained app!

I have a Canon scanner (FB630U) that consistently produces scans that come out too dark. One of scanimage's custom options for the 630U is "--gain", which is my solution for the problem (for good results, I usually have to set it to value "8").
It'd be great if you could add the device specific option "--gain" to gscan2pdf (see output of scanimage -L below).

One suggestion: 
For people who would like to use rare&obscure scanner options it might be useful to have a custom parameter string field (e.g. under Edit>>Preferences)  that would always be appended verbatim to scanimage's commandline (such as "--gain 3" ). 

Regards,
Michael

------------------------------------
Options specific to device `canon630u:libusb:002:005':
    --resolution auto||75|150|300|600dpi [75]
        Sets the resolution of the scanned image.
    --cal[=(yes|no)] [no]
        Force scanner calibration before scan
    --gain 0..64 (in steps of 1) [1]
        Increase or decrease the analog gain of the CCD array
    --gamma <float> [1.59999]
        Selects the gamma corrected transfer curve
    -l 0..215.9mm [0]
        Top-left x position of scan area.
    -t 0..296.333mm [0]
        Top-left y position of scan area.
    -x 0..215.9mm [215.9]
        Width of scan-area.
    -y 0..296.333mm [296.3]
        Height of scan-area.
------------------------------------

---

### Post by JeffreyRatcliffe on 2008-03-26
> **mwww said:**
> It'd be great if you could add the device specific option "--gain" to gscan2pdf (see output of scanimage -L below).

That ought to be no trouble.

> **mwww said:**
> One suggestion: 
For people who would like to use rare&obscure scanner options it might be useful to have a custom parameter string field (e.g. under Edit>>Preferences)  that would always be appended verbatim to scanimage's commandline (such as "--gain 3" ).

That's an interesting idea. The only disadvantage is that I was hoping to drop scanimage/scanadf support in the future and move to directly using the SANE API (after I have written the Perl bindings for it).

Alternatively, scan in colour/greyscale and use threshold to sort out the contrast. Does that produce the same results?

---

### Post by JeffreyRatcliffe on 2008-03-26
> **mwww said:**
> It'd be great if you could add the device specific option "--gain" to gscan2pdf

I've committed this change. It will be in the next release.

---

### Post by sybille on 2008-03-30
I've modified a macro for OpenOffice.org Writer that I found [posted on the new OOo user forums ]("http://user.services.openoffice.org/en/forum/viewtopic.php?f=7&t=3983&start=0#p18272")to work with gcan2pdf. The macro makes it easy to use gscan2pdf as a frontend for OCR.

When gcan2pdf is launched with the macro, you scan, cleanup with unpaper, and run OCR (tesseract-ocr, preferably) as usual. Select whatever text is needed in the text output area of gscan2pdf and copy it. Then close gscan2pdf (it's not necessary to save the scan, so the warning can be ignored), and choose "Paste" in Writer. The text will be pasted into current document for editing.

So basically, the macro just provides a little bit of integration for scanning text into Writer for editing/layout. I'm finding it to be quite convenient, though.

Here's the macro:
```
sub gscan2pdf for OCR
rem ----------------------------------------------------------------------
rem define variables
dim document   as object
dim dispatcher as object
rem ----------------------------------------------------------------------
rem get access to the document
document   = ThisComponent.CurrentController.Frame
dispatcher = createUnoService("com.sun.star.frame.DispatchHelper")

rem ----------------------------------------------------------------------
dispatcher.executeDispatch(document, ".uno:Cut", "", 0, Array())
Shell("/usr/bin/gscan2pdf")
end sub
```After adding that to OOo Basic macros, it's possible to assign the macro to a toolbar button and also to customize the image on the button. I've used the 16x16 png tango style icon for the Epson scanner found here: [http://www.quantum-bits.org/?page_id=3](http://www.quantum-bits.org/?page_id=3)

If anyone is interested in more complete instructions for adding the macro code or setting up the interface, I'd be happy to write up the details.

---

### Post by mwww on 2008-04-08
> **JeffreyRatcliffe said:**
> 
That's an interesting idea. The only disadvantage is that I was hoping to drop scanimage/scanadf support in the future and move to directly using the SANE API (after I have written the Perl bindings for it).

Alternatively, scan in colour/greyscale and use threshold to sort out the contrast. Does that produce the same results?

No, according to my experiments, the --gain option improves the result in a way that cannot be obtained by means of postprocessing.
But since you implemented it already (thanks!), my suggestion for a "custom parameter string field" is redundant (might still be helpful for others).

---

### Post by mwww on 2008-04-08
> **JeffreyRatcliffe said:**
> I've committed this change. It will be in the next release.
I would like to build it from source (I once read somewhere, how to check out the latest source but I can't find it now). Please let me know, if you want me to test it with the canon630u.

---

### Post by saabaero on 2008-05-08
is it possible to add 1 or 2 quick buttons for scanning that users can preset to their needs? 

for exemple, button 1 A4 / black&white / 300 dpi, button 2 letter/color/150dpi?

anything more information about opening pdf's and adding pages at the end of the file?

keep up the good work!

---

### Post by JeffreyRatcliffe on 2008-05-08
> **saabaero said:**
> is it possible to add 1 or 2 quick buttons for scanning that users can preset to their needs?

I intend a feature to save the current settings as a "profile".

> **saabaero said:**
> anything more information about opening pdf's and adding pages at the end of the file?

Not yet. Real life getting in the way...

---

### Post by JeffreyRatcliffe on 2008-05-14
Following the open source edict of "Release early, release often", I have uploaded version 0.9.24 of my utility gscan2pdf to [http://sourceforge.net/projects/gscan2pdf](http://sourceforge.net/projects/gscan2pdf).

Changes:
+ check that the file can be written before saving PDF, TIFF or PS.
  Closes 1915008 (crash when trying to save in non-writable directory)
+ use gtk+ set_do_overwrite_confirmation for save as DjVu.
+ detect thunderbird mail client and attach PDF appropriately.
  Closes LP 202709 ("Email as PDF" option does not work with Thunderbird)
+ deal correctly with newline character in device name
+ gain option from scanners/canonFB630u
+ always force depth before embedding image in PDF
  Closes LP 204988 (gscan2pdf generates blank pages in the .pdf output)
+ fixed erroneous read-only error writing file
+ fixed threshold tool. Closes 1936561 (Threshold tool fails)
+ Cache options
+ crop tool
+ adf_mode option from Epson GT-2500
+ --device option
+ negate tool
+ fixed bug preventing scanning when no device-dependent options reported
+ Norwegian Bokmal translation (thanks to Mikal Krogstad)
+ Persian translation (thanks to Artin)
+ Hungarian translation (thanks to Szenográdi Norbert Péter)
+ Japanese translation (thanks to John M)
+ Update to Czech translation (thanks to Petr JelÃ*nek)
+ Update to Dutch translation (thanks to Jan Klopper)
+ Update to French translation (thanks to Simon Leblanc)
+ Update to German translation (thanks to Manuel Rennecke)
+ Update to Italian translation (thanks to Alberto)
+ Update to Slovenian translation (thanks to Robert Hrovat)
+ Update to Spanish translation (thanks to starmaker)

Just add the following line to your /etc/apt/sources.list:```
deb http://ppa.launchpad.net/jeffreyratcliffe/ubuntu <release> main
deb-src http://ppa.launchpad.net/jeffreyratcliffe/ubuntu <release> main
```

where <release> is the version of Ubuntu you are using. hardy & gutsy are
supported at the time of writing. intrepid, feisty and dapper will follow as soon as I get gtkimageview to build against those distros.

If you are you are using Synaptic, then use menu Edit/Reload Package Information, search for gscan2pdf in the package list, and lo and behold, you can install the nice shiny new version automatically.

From the command line:```
sudo apt-get update
sudo apt-get install gscan2pdf
```

If you add my key to your list of trusted keys, then you will no longer get the "not authenticated" warnings:```
gpg --keyserver www.keyserver.net --recv-keys 4DD7CC93
gpg --export --armor 4DD7CC93 | sudo apt-key add -
```

The dependencies are libgtk2-imagevew-perl, libgtk2-ex-simple-list-perl, perlmagick, libpdf-api2-perl, liblocale-gettext-perl (>= 1.05), libsane, sane-utils, libtiff-tools.

The help will require Gtk2::Ex::PodViewer. The scanadf frontend is in sane. For Email as PDF, you need xdg-utils. OCR requires gocr, or better tesseract. Having installed gscan2pdf, locate the gscan2pdf entry in Synaptic, right-click it and you can install them under "Recommends".

If anybody fancies translating gscan2pdf into any other languages, they are welcome to do so on Rosetta ([https://launchpad.net/products/gscan2pdf/trunk/+pots/gscan2pdf](https://launchpad.net/products/gscan2pdf/trunk/+pots/gscan2pdf))[/QUOTE]

---

### Post by bmt on 2008-05-14
> **JeffreyRatcliffe said:**
> Just add the following line to your /etc/apt/sources.list: ...

It's all gone horribly wrong! ;-)

Synaptic can't see your new repository; downloading from //ppa.launchpad.net/... goes into all sorts of dependency stuff.

Incidentally, Update Manager reports:```
W: Failed to fetch http://ppa.launchpad.net/jeffreyratcliffe/ubuntu/pool/main/
libg/libgtk2-ex-simple-list-perl/libgtk2-ex-simple-list-perl_0.50-1.1_all.deb
  404 Not Found
``` (my line break) which may be related.

Edit to add: there's no .deb in that location, so it's not directly related to the failure to find the gscan2pdf .deb.

To cap it all, [www.keyserver.net](www.keyserver.net) times out.

Sorry to bear these bad tidings.:(

---

### Post by JeffreyRatcliffe on 2008-05-14
> **bmt said:**
> Synaptic can't see your new repository; downloading from //ppa.launchpad.net/... goes into all sorts of dependency stuff.

grrr. I see now that when I tested it, I forgot to clean my apt cache, so that it didn't bother fetching the packages from the repository. Now I am seeing the same problem, which seems to be because Launchpad hasn't build the gtkimageview package properly for Hardy.

I have bumped the version number and uploaded it again. It has already built for amd64 and will do so for i386 in the next half hour.

I hope it will be working then. I will test it again tomorrow.

---

### Post by JeffreyRatcliffe on 2008-05-15
> **JeffreyRatcliffe said:**
> I hope it will be working then. I will test it again tomorrow.

The repository should be working for Hardy and Gutsy. Can anyone confirm this?

---

### Post by harunaga on 2008-05-16
Synaptic reports no problem with the repository; but tells me that 0.9.23 is the latest version, so I haven't been able to install the shiny new 0.9.24...

Harunaga Isaacson

---

### Post by harunaga on 2008-05-16
Forgot to mention that that's under Gutsy. HI

---

### Post by JeffreyRatcliffe on 2008-05-16
> **harunaga said:**
> Synaptic reports no problem with the repository; but tells me that 0.9.23 is the latest version, so I haven't been able to install the shiny new 0.9.24...

Have you updated the repository information to point at the new ppa repository in your /etc/apt/sources.list (or in the repository dialog in Synaptic)?

---

### Post by harunaga on 2008-05-16
> **JeffreyRatcliffe said:**
> Have you updated the repository information to point at the new ppa repository in your /etc/apt/sources.list (or in the repository dialog in Synaptic)?
Yes, I added 
deb [http://ppa.launchpad.net/jeffreyratcliffe/ubuntu](http://ppa.launchpad.net/jeffreyratcliffe/ubuntu) gutsy main
to /etc/apt/sources.list (and deleted the repository information for the
old repository).

HI

---

### Post by harunaga on 2008-05-16
And reloaded package information in Synaptic... HI

---

### Post by JeffreyRatcliffe on 2008-05-16
> **harunaga said:**
> Yes, I added 
deb [http://ppa.launchpad.net/jeffreyratcliffe/ubuntu](http://ppa.launchpad.net/jeffreyratcliffe/ubuntu) gutsy main
to /etc/apt/sources.list (and deleted the repository information for the
old repository).

In that case, I have no explanation of why you can't see the new version. Which architecture are you using? i386? amd64? ppa doesn't support any others.

---

### Post by snobel on 2008-05-16
0.9.24 installed fine on hardy. However, the packages gscan2pdf and libgtk2-imageview-perl could not be authenticated.
I added your key months ago, so just in case something had gone wrong in the gutsy-to-hardy upgrade, I tried to add the key again, from the suggested servers:

[www.keyserver.net:](www.keyserver.net:) (hangs)
keyring.debian.org: "key 4DD7CC93 not found on keyserver"
subkeys.pgp.net: "not changed"

...so I guess the key is actually present and OK?

---

### Post by JeffreyRatcliffe on 2008-05-16
> **snobel said:**
> 0.9.24 installed fine on hardy. However, the packages gscan2pdf and libgtk2-imageview-perl could not be authenticated.
I added your key months ago, so just in case something had gone wrong in the gutsy-to-hardy upgrade, I tried to add the key again, from the suggested servers:

[www.keyserver.net:](www.keyserver.net:) (hangs)
keyring.debian.org: "key 4DD7CC93 not found on keyserver"
subkeys.pgp.net: "not changed"

...so I guess the key is actually present and OK?

Yes. But the PPA repos are not signed at the moment. This has been discussed for some time. See
[https://bugs.launchpad.net/soyuz/+bug/125103](https://bugs.launchpad.net/soyuz/+bug/125103)

I'll take the stuff about my key out of the docs to prevent confusion.

---

### Post by harunaga on 2008-05-16
i386. Mysterious. Trying to install by hand from your .deb file at [http://ppa.launchpad.net/jeffreyratcliffe/ubuntu/pool/main/g/gscan2pdf/](http://ppa.launchpad.net/jeffreyratcliffe/ubuntu/pool/main/g/gscan2pdf/)
has also not worked for me (Error: Dependency is not satisfiable: libgtk2-imageview-perl ; was also unsuccessful in attempting to install libgtk2-imageview-perl). HI

---

### Post by JeffreyRatcliffe on 2008-05-16
> **harunaga said:**
> i386. Mysterious. Trying to install by hand from your .deb file at [http://ppa.launchpad.net/jeffreyratcliffe/ubuntu/pool/main/g/gscan2pdf/](http://ppa.launchpad.net/jeffreyratcliffe/ubuntu/pool/main/g/gscan2pdf/)
has also not worked for me (Error: Dependency is not satisfiable: libgtk2-imageview-perl ; was also unsuccessful in attempting to install libgtk2-imageview-perl). HI

You will have to install gtkimageview first, followed by libgtk2-imageview-perl, and then gscan2pdf.

---

### Post by harunaga on 2008-05-16
Well, I am still baffled. I have installed 
[http://ppa.launchpad.net/jeffreyratcliffe/ubuntu/pool/main/g/gtkimageview/libgtkimageview0_1.6.1-2gutsy1_i386.deb](http://ppa.launchpad.net/jeffreyratcliffe/ubuntu/pool/main/g/gtkimageview/libgtkimageview0_1.6.1-2gutsy1_i386.deb)
apparently successfully. But attempting to install gscan2pdf gives still
Error: Dependency is not satisfiable: libgtk2-imageview-perl
(or if running dkpg -i from the commmandlinegscan2pdf depends on libgtk2-imageview-perl; however:
  Package libgtk2-imageview-perl is not installed.
)
Is then libgtk2-imageview-perl different from libgtk2imageview-perl,
and if so where do I find the right package that gscan2pdf wants?

Thanks for your patience and help, Harunaga

---

### Post by JeffreyRatcliffe on 2008-05-16
> **harunaga said:**
> Well, I am still baffled. I have installed 
[http://ppa.launchpad.net/jeffreyratcliffe/ubuntu/pool/main/g/gtkimageview/libgtkimageview0_1.6.1-2gutsy1_i386.deb](http://ppa.launchpad.net/jeffreyratcliffe/ubuntu/pool/main/g/gtkimageview/libgtkimageview0_1.6.1-2gutsy1_i386.deb)
apparently successfully. But attempting to install gscan2pdf gives still
Error: Dependency is not satisfiable: libgtk2-imageview-perl
(or if running dkpg -i from the commmandlinegscan2pdf depends on libgtk2-imageview-perl; however:
  Package libgtk2-imageview-perl is not installed.
)
Is then libgtk2-imageview-perl different from libgtk2imageview-perl,
and if so where do I find the right package that gscan2pdf wants?

[http://ppa.launchpad.net/jeffreyratcliffe/ubuntu/pool/main/libg/libgtk2-imageview-perl/libgtk2-imageview-perl_0.04-1_i386.deb](http://ppa.launchpad.net/jeffreyratcliffe/ubuntu/pool/main/libg/libgtk2-imageview-perl/libgtk2-imageview-perl_0.04-1_i386.deb)

---

### Post by bmt on 2008-05-16
> **JeffreyRatcliffe said:**
> You will have to install gtkimageview first, followed by libgtk2-imageview-perl, and then gscan2pdf.
On i386 gutsy:

gtkimageview installs fine.
libgtk2-imageview-perl_0.04-1_i386 throws an error -- 'Dependency is not satisfiable: base-files'.  Needless to say, base-files *is* there. (Standard Ubuntu v4.0.0ubuntu5.)

This is all downloading and installing manually: Synaptic still cannot see any of the files in the ppa repository.

---

### Post by harunaga on 2008-05-16
Thank you. 

libgtk2-imageview-perl depends on base-files (>= 4.0.1); however:
  Version of base-files on system is 4.0.0ubuntu5.
 libgtk2-imageview-perl depends on perl (>= 5.8.8-12); however:
  Version of perl on system is 5.8.8-7ubuntu3.1.

Is there a way to get this up without switching to Hardy? HI

---

### Post by harunaga on 2008-05-16
This seems to be the same problem bmt has. HI

---

### Post by JeffreyRatcliffe on 2008-05-16
> **harunaga said:**
> Thank you. 

libgtk2-imageview-perl depends on base-files (>= 4.0.1); however:
  Version of base-files on system is 4.0.0ubuntu5.
 libgtk2-imageview-perl depends on perl (>= 5.8.8-12); however:
  Version of perl on system is 5.8.8-7ubuntu3.1.

Is there a way to get this up without switching to Hardy? HI

Ah. The penny drops. I uploaded the *source* to the Hardy repository, and use the copy function in the ppa to copy it to the others, but it hasn't built against gutsy properly. I'll upload a gutsy-specific version now.

---

### Post by harunaga on 2008-05-16
Great! I'm eagerly awaiting it. (I noticed that you have added a crop-utility, one of the things I had been missing most in your very useful application.) 
Harunaga

---

### Post by JeffreyRatcliffe on 2008-05-16
> **harunaga said:**
> Great! I'm eagerly awaiting it. (I noticed that you have added a crop-utility, one of the things I had been missing most in your very useful application.) 
Harunaga

Try now.

---

### Post by bmt on 2008-05-16
> **JeffreyRatcliffe said:**
> Try now.

libgtk2-imageview-perl_0.04-1gutsy1_i386 now shows up in Synaptic, but is still dependent on base-files >=4.0.1.

(i386 gutsy)

---

### Post by JeffreyRatcliffe on 2008-05-16
> **bmt said:**
> libgtk2-imageview-perl_0.04-1gutsy1_i386 now shows up in Synaptic, but is still dependent on base-files >=4.0.1.

(i386 gutsy)

And now?

---

### Post by harunaga on 2008-05-16
> **JeffreyRatcliffe said:**
> And now?
Yes! Thank you very much. 0.9.24 is now installed properly, and though testing has to wait for now, from a quick look all seems well. Thanks very much.

---

### Post by bmt on 2008-05-17
> **JeffreyRatcliffe said:**
> And now?

All's well with libgtk2-imageview-perl (0.04-1gutsy2) and libgtkimageview0 (1.6.1-2gutsy1), they both appear in Synaptic and install without drama.

gscan2pdf 0.9.24 does not appear in Synaptic, but a manually downloaded copy installs correctly.

Incidentally, are you going to publicise the change of repository?  I would normally have just seen a new version appear in Update Manager, but that wouldn't have happened this time.  Fortunately, I saw it in the GnomeFiles.org feed otherwise it could have been months before I came looking in this thread again -- I usually pop in when Update Manager prompts, to catch up with the news.

As a more casual user, or first-timer, if I had just seen the notice on GnomeFiles, I'd have been stuffed, with no way of knowing where to get the dependencies.  I might have downloaded the source tarball for more clues, but that contains no README and the INSTALL file give instructions for compiling and installing v0.8.3, with references to the Sourceforge repos.

(Written to be constructive, not as a criticism -- you're a braver man than me! ;-) )

---

### Post by JeffreyRatcliffe on 2008-05-17
> **bmt said:**
> gscan2pdf 0.9.24 does not appear in Synaptic, but a manually downloaded copy installs correctly.

Strange. I probably need a gutsy specific gscan2pdf build as well - although the package will be identical. The launchpad ppas certainly have some bugs to iron out.

> **bmt said:**
> Incidentally, are you going to publicise the change of repository?

It was on the website and on this thread. It is only interesting for Ubuntu users, as I upload to Debian Sid myself. I'll make it clearer in the news section of the website.

> **bmt said:**
> the INSTALL file give instructions for compiling and installing v0.8.3, with references to the Sourceforge repos.

Thanks for pointing that out - I have updated the INSTALL file for the next version.

---

### Post by bmt on 2008-05-17
> **JeffreyRatcliffe said:**
> Strange. I probably need a gutsy specific gscan2pdf build as well - although the package will be identical. The launchpad ppas certainly have some bugs to iron out.
I'm not a repository expert ;-) but Launchpad page ...ubuntu/dists/gutsy/main/binary-i386/Packages does not contain information about the gscan2pdf package, only to the dependencies.  Compare to the corresponding Hardy file, which does contain an entry for gscan2pdf.

Sorry if my previous post came across as a bit terse -- not intended -- and I should have looked deeper into the Sourceforge pages; apologies too for this thread noise (you have no PM, which I can understand!).

---

### Post by JeffreyRatcliffe on 2008-05-17
> **bmt said:**
> I'm not a repository expert ;-) but Launchpad page ...ubuntu/dists/gutsy/main/binary-i386/Packages does not contain information about the gscan2pdf package, only to the dependencies.  Compare to the corresponding Hardy file, which does contain an entry for gscan2pdf.

You are quite right. I tried uploading a gutsy-specific version, but still no dice, so I've reported it as a bug:

[https://bugs.launchpad.net/soyuz/+bug/231422](https://bugs.launchpad.net/soyuz/+bug/231422)

Thanks for the feedback

---

### Post by JeffreyRatcliffe on 2008-05-18
> **JeffreyRatcliffe said:**
> You are quite right. I tried uploading a gutsy-specific version, but still no dice, so I've reported it as a bug

Now the gutsy packages are there. Can a gutsy user confirm that the repo is working OK?

---

### Post by bmt on 2008-05-18
> **JeffreyRatcliffe said:**
> Can a gutsy user confirm that the repo is working OK?
Yes, it came straight up on the Update Manager and Synaptic is fine.

Thanks for your efforts.

---

### Post by harunaga on 2008-05-18
Second confirmation here. Thanks again.

---

### Post by Hudy on 2008-06-15
OK, even though this thread is very long, I see it's still active!

I had gscan2pdf in Gutsy, and it worked.  Now, on two separate computers running Hardy, it does not work.

A color scan, 150 dpi, export to PDF with no compression works, but the file (of course) is huge.  With any compression scheme, it fails.

I tried this with the default/stock Hardy version of gscan2pdf (0.9.21-1ubuntu4) and with the one Jeffrey has made available via Launchpad (0.9.24).  The later version at least gives a better error message. Here's the text of one such message: "Error embedding file image in tif format to PDF: Wrong TIFF id '' (should be 42) at /usr/share/perl5/PDF/API2/Resource/XObject/Image/TIFF.pm line 414".

Hopefully I've successfully attached a gzipped log resulting from using '--debug'.

TIA,

/Bill

---

### Post by JeffreyRatcliffe on 2008-06-15
> **Hudy said:**
> I had gscan2pdf in Gutsy, and it worked.  Now, on two separate computers running Hardy, it does not work.

A color scan, 150 dpi, export to PDF with no compression works, but the file (of course) is huge.  With any compression scheme, it fails.

I tried this with the default/stock Hardy version of gscan2pdf (0.9.21-1ubuntu4) and with the one Jeffrey has made available via Launchpad (0.9.24).  The later version at least gives a better error message. Here's the text of one such message: "Error embedding file image in tif format to PDF: Wrong TIFF id '' (should be 42) at /usr/share/perl5/PDF/API2/Resource/XObject/Image/TIFF.pm line 414".

Hopefully I've successfully attached a gzipped log resulting from using '--debug'.

This seems to be a problem with the new version of libsane. The file does not seem to get saved properly.

You will see that when gscan2pdf starts, it creates a temporary directory where all the scans, etc. are initially saved. This directory is then deleted when gscan2pdf is closed. Scan one page, list the contents of this directory, and see if you can open the image with another program.

Regards

Jeff

---

### Post by cattin on 2008-06-27
> **JeffreyRatcliffe said:**
> This seems to be a problem with the new version of libsane. The file does not seem to get saved properly.

You will see that when gscan2pdf starts, it creates a temporary directory where all the scans, etc. are initially saved. This directory is then deleted when gscan2pdf is closed. Scan one page, list the contents of this directory, and see if you can open the image with another program.

Regards

Jeff

Dear Jeff,

I have the same problem on my hardy installation and the newest gscan2pdf version 0.9.24 that I install from your PPA.

In my case I'm using gscan2pdf to add the OCR text to a scanned PDF document. For this I'm loading the PDF (BTW: b/w gets inverted with every import - but thats another problem). When I then try to save the new PDF document I get the same error. Looking at the pages in the /tmp directory I have no problems opening the pnm files what so ever (using imagemagick)

gscan2pdf 0.9.21 on the other side was working with the same libsane (1.0.19-1ubuntu3) version.

thanks, Philippe

---

### Post by JeffreyRatcliffe on 2008-06-27
> **cattin said:**
> In my case I'm using gscan2pdf to add the OCR text to a scanned PDF document. For this I'm loading the PDF (BTW: b/w gets inverted with every import - but thats another problem). When I then try to save the new PDF document I get the same error. Looking at the pages in the /tmp directory I have no problems opening the pnm files what so ever (using imagemagick)

Are you saying that importing a PDF gives you something similar to:

```
"Error embedding file image in tif format to PDF: Wrong TIFF id (should be 42) at /usr/share/perl5/PDF/API2/Resource/XObject/Image/TIFF.pm line 414"
```

Can you post an example PDF here (or email it to me) and give me the exact error message?

---

### Post by JeffreyRatcliffe on 2008-07-05
Following the open source edict of "Release early, release often", I have uploaded version 0.9.25 of my utility gscan2pdf to [http://sourceforge.net/projects/gscan2pdf](http://sourceforge.net/projects/gscan2pdf).

Changes:
- current page selection as not intuitive for some people, and anyway not
  strictly necessary.
  Closes Debian bug #480947 (Defaults for pages are weird now)
+ support for unpaper option --output-pages
  Closes Launchpad bug #215683
   (gscan2pdf should offer an option to split a scanned page)
+ Check for device before caching.
+ Checkbox to disable option cache
  Closes 1980762 (Second Start Failure)
+ Check {Pseudo|Direct}Class for pnm and convert to pbm in necessary for djvu
  Closes Debian bug #486553 (gscan2pdf: unable to save as DjVu)
+ Correct DjVu text zones
  Closes Debian bug #486680 (gscan2pdf: bizarre DjVu text zones)
+ Save resolution information with TIFF. Closes Debian bug #485641:
  (gscan2pdf: No longer saves resolution in TIFF files)
+ fixed unsharp mask tool
+ prefix option to preferences
  Closes Debian bug #484641 (gscan2pdf: prefix option for scanimage command)
+ Bulgarian translation (thanks to Emil Pavlov)
+ Update to Danish translation (thanks to Jacob Nielsen)
+ Update to Dutch translation (thanks to Lodder)
+ Update to French translation (thanks to Simon Leblanc)
+ Update to German translation (thanks to Kim Linoh)
+ Update to Italian translation (thanks to Milo Casagrande)
+ Update to Polish translation (thanks to Wojtek Jamrozy)
+ Update to Russian translation (thanks to Igor Zubarev)
+ Update to Spanish translation (thanks to Alejandro Rochette)

Just add the following line to your /etc/apt/sources.list:```
deb http://ppa.launchpad.net/jeffreyratcliffe/ubuntu <release> main
deb-src http://ppa.launchpad.net/jeffreyratcliffe/ubuntu <release> main
```

where <release> is the version of Ubuntu you are using. hardy & gutsy are
supported at the time of writing. intrepid, feisty and dapper will follow as soon as I get gtkimageview to build against those distros.

If you are you are using Synaptic, then use menu Edit/Reload Package Information, search for gscan2pdf in the package list, and lo and behold, you can install the nice shiny new version automatically.

From the command line:```
sudo apt-get update
sudo apt-get install gscan2pdf
```

The dependencies are libgtk2-imagevew-perl, libgtk2-ex-simple-list-perl, perlmagick, libpdf-api2-perl, liblocale-gettext-perl (>= 1.05), libsane, sane-utils, libtiff-tools.

The help will require Gtk2::Ex::PodViewer. The scanadf frontend is in sane. For Email as PDF, you need xdg-utils. OCR requires gocr, or better tesseract. Having installed gscan2pdf, locate the gscan2pdf entry in Synaptic, right-click it and you can install them under "Recommends".

If anybody fancies translating gscan2pdf into any other languages, they are welcome to do so on Rosetta ([https://launchpad.net/products/gscan2pdf/trunk/+pots/gscan2pdf](https://launchpad.net/products/gscan2pdf/trunk/+pots/gscan2pdf))

---

### Post by harunaga on 2008-07-05
It is always very welcome when a new version of gscan2pdf appears. Unfortunately
0.9.25 does not work for me (running Ubuntu 7.10). Output
of gscan2pdf --debug :

gscan2pdf 0.9.25
Using en_US.UTF-8 locale
Config::General: Block "<cache>" has no EndBlock statement (level: 2, chunk 170)!
 at /usr/bin/gscan2pdf line 212

Harunaga

---

### Post by JeffreyRatcliffe on 2008-07-05
> **harunaga said:**
> Unfortunately
0.9.25 does not work for me (running Ubuntu 7.10). Output
of gscan2pdf --debug :

gscan2pdf 0.9.25
Using en_US.UTF-8 locale
Config::General: Block "<cache>" has no EndBlock statement (level: 2, chunk 170)!
 at /usr/bin/gscan2pdf line 212

Delete ~/.gscan2pdf and try again.

---

### Post by harunaga on 2008-07-05
Thank you! All is now well...

HI

---

### Post by sybille on 2008-07-06
Thank you very much for adding the option to have unpaper split double page scans into two separate pages! It's a great addition that really helps streamline book scanning with a flatbed scanner.

Otherwise, all seems well with the new release for me on Hardy (updated to hardy-proposed).

Thanks again for your continued work on this most excellent project.

---

### Post by kafkaian on 2008-07-22
For some reason, and since I noticed yesterday, when clicking on "scan options" I have lost all the options under the "device-dependent options" header.

It was working fine a few days ago, so I don't know if any of the native updates have affected this application:

gscan2pdf 0.9.25

Linux ubuntu 2.6.24-19-386 #1 Fri Jul 11 22:45:14 UTC 2008 i686 GNU/Linux

---

### Post by JeffreyRatcliffe on 2008-07-22
> **kafkaian said:**
> For some reason, and since I noticed yesterday, when clicking on "scan options" I have lost all the options under the "device-dependent options" header.

Try clearing the cache in the preferences menu. If that doesn't work, try deleting ~/.gscan2pdf. If that doesn't help, start gscan2pdf with --debug and send me the output after you have opened the scan dialog

---

### Post by kafkaian on 2008-07-22
> **JeffreyRatcliffe said:**
> Try clearing the cache in the preferences menu. If that doesn't work, try deleting ~/.gscan2pdf. If that doesn't help, start gscan2pdf with --debug and send me the output after you have opened the scan dialog Cleared the cache in preferences and back to normal.

Many thanks

---

### Post by JeffreyRatcliffe on 2008-07-23
> **kafkaian said:**
> Cleared the cache in preferences and back to normal.

Hmmm. If this happens again, please see if you can reproduce it. That caching code is new, and there is evidently a bug in there somewhere.

---

