---
title: "DVD-R burns in Hedgehog, but not Badger"
date: 2005-11-02
forum: General Help
---

### Post by essexman on 2005-11-02
I have been exploring this for days now, and I know I am not alone.

I have installed an LG, DVD Rewriter on my machine, running Breezy and it will not burn data on to blank disks, because gnomebaker, k3b, and graveman do not recognise that a blank disc is inserted.  The disk shows up on the desktop and gnome-volume-manager as present, correct and mounted.

Then I wondered what would happen if I copied the files onto my old 5.04 partiotion that I was going to delete?  I booted into Hedgehog and was able to burn the files straight away, no errors at full (4x) speed.

The 1.1GB disc can be read in breezy and the mp3 files on it all play fine. play.

I had trouble with HAL not working for the USB volumes but I fixed that, (forums and bugfixes are steering people to ag plugdev group to HAL).  My Zip, Ipod (Jenny's Ipod) and usb key all read and write fine.

Even though HAL/udev seems ok, I am still suspicious because the DVD- rewriter does not get an entry added into fstab by fstab-sync.  I was going to have a go at using pmount instead but the udev setup in ubuntu is far away from the documented [guidance]("http://www.reactivated.net/writing_udev_rules.html")
or even the [5.04 Ubuntu Guide]("http://www.ubuntuguide.org/#configurepalmosdevices") that I don't want to risk it with out clear guidance.

I did a google for cdsymlinks.conf, and I think this is the way.

I would very much appreciate if an expert on HAL or udev could give me a steer with this.

Thanks in advance

---

### Post by essexman on 2005-11-03
Bumperty bump.

21 Views and no replies.

Someone knows this.

Maybe it is an upgrade in the backend DVD writing software that doesn't recognise a blank disc is mounted?

Bug 18860 is added

---

### Post by ron1n1 on 2005-11-03
I'm having the same issue.  I've tried nautilus, gnomebaker, and graveman but none of them will burn DVD-R.  CD-R burns fine.  I'll try some other DVD formats tomorrow, but this drive could burn DVD-R with warty. 

Is DVD-R supported in Breezy?

---

### Post by Lovechild on 2005-11-03
it's not supported in Breezy:

Device seems to be: Generic mmc2 DVD-R/DVD-RW.
cdrecord: Found DVD media but DVD-R/DVD-RW support code is missing.
cdrecord: If you need DVD-R/DVD-RW support, ask the Author for cdrecord-ProDVD.
cdrecord: Free test versions and free keys for personal use are at [ftp://ftp.berlios.de/pub/cdrecord/ProDVD/](ftp://ftp.berlios.de/pub/cdrecord/ProDVD/)
cdrecord: This version of cdrecord does not include DVD-R/DVD-RW support code.
cdrecord: See /usr/share/doc/cdrecord/README.DVD.Debian for details on DVD support.

---

### Post by essexman on 2005-11-04
[quote=Lovechild]it's not supported in Breezy:

Device seems to be: Generic mmc2 DVD-R/DVD-RW.
cdrecord: Found DVD media but DVD-R/DVD-RW support code is missing.
cdrecord: If you need DVD-R/DVD-RW support, ask the Author for cdrecord-ProDVD.
cdrecord: Free test versions and free keys for personal use are at [ftp://ftp.berlios.de/pub/cdrecord/ProDVD/]("ftp://ftp.berlios.de/pub/cdrecord/ProDVD/")
cdrecord: This version of cdrecord does not include DVD-R/DVD-RW support code.
cdrecord: See /usr/share/doc/cdrecord/README.DVD.Debian for details on DVD support.[/quote] 
Thanks for the reply

Unfortunately the dvdrecord fix on the readme doesn't work. The dvdrecord patch is the only simple solution given and after the fakeroot stage I get the following error:

debian/rules:16: /usr/share/dpatch/dpatch.make: No such file or directory
make: *** No rule to make target `/usr/share/dpatch/dpatch.make'.  Stop.

I will try the dvd+rw-tools method as I already have this installed but this is complex for me without a HOWto.

So can you say (or guess) why this is supported in Headghog, but not breezy badger?

---

### Post by essexman on 2005-11-04
So where is cdrtools repository?

CDRtools 2.1 was included in the Breezy freeze but I can only find the cdrtools-docs

 Do I still need [cdrtools]("http://www.fokus.fhg.de/research/cc/glone/employees/joerg.schilling/private/cdrecord.html")?   A.	Yes. It should be explicitly noted that **growisofs is a 	front-end to mkisofs,** i.e. invokes mkisofs to perform the 	actual ISO9660 file system layout. Secondly, the DVD burners 	available on the market can burn even CD-R[W] media and 	cdrecord is the tool for this job [and this job only].

---

### Post by essexman on 2005-11-25
[quote=essexman]So where is cdrtools repository?

CDRtools 2.1 was included in the Breezy freeze but I can only find the cdrtools-docs

 Do I still need [cdrtools]("http://www.fokus.fhg.de/research/cc/glone/employees/joerg.schilling/private/cdrecord.html")?   A.    Yes. It should be explicitly noted that **growisofs is a     front-end to mkisofs,** i.e. invokes mkisofs to perform the     actual ISO9660 file system layout. Secondly, the DVD burners     available on the market can burn even CD-R[W] media and     cdrecord is the tool for this job [and this job only].[/quote]

This matter is now resolved.

After a short while the LG dvd writer stopped working on Hoary as well as breezy.  Then i installed SUSE and it worked once for a burn.  Then I couldn't even read CDs  After extensive testing of every combination of setup and parameters it became 99% obvious that the LG 4163 wasn't working.

I have installed my new LITE-ON from ebuyer and backed up my girlfriends home directory (one of two key tasks that had become very overdue) over 4GB at 16x speed, on KB3 with out any set-up.

One day, when a piece of (new) hardware stops working I will instantly recognise this and not assume that it is either Linux or something I Have done wrong.

One day

---

