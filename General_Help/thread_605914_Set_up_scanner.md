---
title: "Set up scanner"
date: 2007-11-07
forum: General Help
---

### Post by Dave Otter on 2007-11-07
I am trying to set up a Medion MD9458 flatbed scanner in Feisty.
     I have found the firmware .
What are the next steps I require?
    Please make it simple for one orf little brain
                  Thanks

---

### Post by ajgreeny on 2007-11-07
Go to xsane in the Graphics menu and open it.  It will then search for your scanner.  Or have you already tried that and wonder where to go from there?

---

### Post by Dave Otter on 2007-11-07
Have been to Xsane-lists my scanner as Mustek Bearpaw 1200-which it isn't
                          Thanks for your reply

---

### Post by geraldm on 2007-11-07
The USB vendor and product numbers are the same for both scanners, and both use the 
same sane backend sane-gt68xx.  It is fairly common for one vendor to re-badge another
vendor's scanner.

Gerald

---

### Post by Dave Otter on 2007-11-07
When I select the scanner in Xsane I get  error message:-Failed to open device gt68xx:libusb:005:004':invalid argument.

                             Any help appreciated.

---

### Post by Bablefish on 2007-11-07
I know what they say here but I haven't came across not one person that Xsane even works for them, I incude myself.

---

### Post by Dave Otter on 2007-11-08
In structions I have been given are to dind firmware,which I have done and putit in /usr/share sane/gt68xx
    HOW DO I DO THAT.  that file does not exist!
  How do I create it

---

### Post by Michael Matthews on 2007-11-12
:~$ ls /usr/share/sane
gt68xx  xsane

Ubuntu 7.10. I think you need to re-install xsane.

Though I find the interface a little confusing I have had no real problems with a Canon U686. Be sure to install the docs.

---

### Post by bodycoach2 on 2007-11-12
Unless I miss read your post, you've now come across someone who's yet to find a scanner that Xsane DIDN'T work. I've used it on about 15 different scanners, testing them before our Free Geek Central Florida chapter gave them out. Most were Epson, HP, and Canon.

We had a few times when Xsane didn't see the scanner right away, but restarting the computer with the scanner plugged up fixed that.

If I come across a scanner that doesn't work for us, I'll post it.

> **Bablefish said:**
> I know what they say here but I haven't came across not one person that Xsane even works for them, I incude myself.

---

### Post by LeftyMills on 2007-11-13
I have the same problem with my BearPaw Mustek 2400CU Plus.  I dual boot Ubuntu 7.10 and WinXP.  Scanner works perfectly in XP, so I assume the USB is plugged into the right place.
In Ubuntu 7.10 - GIMP - acquire - XSane image scanner - device dialog -   "X Failed to open device 'gt68xx:libusb:001:002':  invalid argument.  close"

Can someone confirm that it is possible to get a Mustek BearPaw 2400 scanner working in Ubuntu 7.10.  If so, how did you do it?

Thanks.
Lefty

---

### Post by Dave Otter on 2007-11-13
Am unable to get this scanner working-even though it is said to be supported

                      Thanks to all who have replied


   ANYNEWIDEASWELCOMED  just keep it simpler

---

### Post by ferd on 2007-11-13
> **bodycoach2 said:**
> Unless I miss read your post, you've now come across someone who's yet to find a scanner that Xsane DIDN'T work. I've used it on about 15 different scanners, testing them before our Free Geek Central Florida chapter gave them out. Most were Epson, HP, and Canon.

We had a few times when Xsane didn't see the scanner right away, but restarting the computer with the scanner plugged up fixed that.

If I come across a scanner that doesn't work for us, I'll post it.

Canon D1250 U2F does not work.

---

### Post by tulpie on 2007-12-24
my post replays to the entry question. (MD 9458 ) 

Step by Step

1. Read this [http://www.sane-project.org/man/sane-gt68xx.5.html](http://www.sane-project.org/man/sane-gt68xx.5.html)

2.install wine and install this, because in this *.exe is the working Firmware.
Homepage:
[http://www.treiberupdate.de/treiber-download/download-34771-treiber-Artec-ArtecUSBScannerUltima2000E+.html](http://www.treiberupdate.de/treiber-download/download-34771-treiber-Artec-ArtecUSBScannerUltima2000E+.html)
Direkt link:
[http://www.treiberupdate.de/treiber-download/z-dltreiber/download_treiber_999_1007.php?load=34771&extern=1&vendor=Artec&sys=WindowsXP](http://www.treiberupdate.de/treiber-download/z-dltreiber/download_treiber_999_1007.php?load=34771&extern=1&vendor=Artec&sys=WindowsXP)

3. In this Folder is the Firmware:
/home/seestern/.wine/drive_c/windows/system32/drivers/ePlus2k.usb

4. sudo nautilus
and copy this Firmware "ePlus2k.usb" in this Folder, called:
/usr/share/sane/gt68xx
This Folder can also found by Seach-engine in Main-Menu

5.Configure this File and insert the highlighted Text, at the same position.

/etc/san[COLOR="Red"]e[/COLOR].d/gt68xx.conf   [COLOR="Red"]            
*PATH  EDITED..... thanks to joris1977*[/COLOR]

> 
.
.
.
##############################################################################
# Autodetect Mustek BearPaw 1200 CU, 2400 CU, Mustek ScanExpress 1200 UB Plus,
# Artec Ultima 2000, and several other GT-6801-based scanners
usb 0x05d8 0x4002

[B]# Medion/Lifetec/Tevion/Cytron MD 9458:
override "artec-ultima-2000"
vendor "Medion"
model "MD 9458"
firmware "ePlus2k.usb"
[/B]
# Mustek BearPaw 1200 CU doesn't need any manual override
.
.
.

Because Vid and Vendor is corect, because in Sacanner is this Numbers programmed.


Tipp: XSANE work only at the first try correct. After Closing it, it dosn't work anymore :confused:

typ in Terminal 

xscanimage 

and check this little Programm. 

Here you can see a list, what USB-Scanners will be supported be gt68xx Chip's.
Also You Can see the Pid and Vid, which came before the PC does not find the USB scanner.

[http://meier-geinitz.de/sane/gt68xx-backend/](http://meier-geinitz.de/sane/gt68xx-backend/)

Happy Christmas from Germany

PS: At the end of this projekt i found nummers of Tipps in internet. :lolflag:

---

### Post by joris1977 on 2008-01-06
Wow tulpie thanks for this how too -> \\:D/

I just got this scanner for free and with your howto it took me two minutes to get it working!

It is still not plug and play, but it comes close.

two small things:

this must be a typo:
/etc/sand.d/gt68xx.conf

should be:
/etc/sane.d/gt68xx.conf

and 
Wine gave me trouble installing/extracting the driver: just a blue screen with the name of the driver-> with pressing alt tab i could scroll to the pop up and agree with the questions.

still really easy

---

### Post by _Stevie_ on 2008-02-13
LeftyMills, all you have to do is:

download this file [http://www.meier-geinitz.de/sane/gt68xx-backend/firmware/PS2Dfw.usb](http://www.meier-geinitz.de/sane/gt68xx-backend/firmware/PS2Dfw.usb)
and put it into /usr/share/sane/gt68xx/

launch Xsane and you can scan :)

---

### Post by tulpie on 2008-03-10
_Stevie_

You get it :guitar:
Today i had tryed the same procedere as i discribe, but yours is the "mp3" version :lolflag:
*Sorry _Stevie_ your firmeware does not work with my Scanner*
Anyway... the only aim is to get it work in any way.... :D

---

### Post by _Stevie_ on 2008-03-13
mp3 version? lol, sorry i cant follow :)

---

