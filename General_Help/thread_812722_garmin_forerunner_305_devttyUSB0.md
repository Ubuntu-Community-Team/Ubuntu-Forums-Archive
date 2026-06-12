---
title: "garmin forerunner 305 /dev/ttyUSB0"
date: 2008-05-30
forum: General Help
---

### Post by Anilael on 2008-05-30
Hello All!

Reading the threads regarding the Garmin issue, I took the advice given in the following thread:

[http://ubuntuforums.org/showthread.php?t=404075&highlight=garmin_gps&page=2]("http://ubuntuforums.org/showthread.php?t=404075&highlight=garmin_gps&page=2")

which is:
> I have got Pytrainer working with the Forerunner 305 (including heart rate) on Ubuntu 8.04.

The correct device setting for Garmin Heart Rate is /dev/ttyUSB0

However to get the Forerunner to appear as ttyUSB0 you need to edit /etc/modprobe.d/blacklist. Comment out the line that says 'blacklist garmin_gps' and then reboot.

After that Pytrainer should work with the Forerunner 305, it is a great piece of software.

I hope this helps.

 I removed the entry 'blacklist garmin_gps' and rebooted, but the device still doesn't appear as /dev/ttyUSB0

I get the following messages upon inserting the device:
> May 30 13:03:52 temani-desktop kernel: [  132.195974] usb 2-3.2: new full speed USB device using ehci_hcd and address 6
May 30 13:03:52 temani-desktop kernel: [  132.360908] usb 2-3.2: new full speed USB device using ehci_hcd and address 7
May 30 13:03:52 temani-desktop kernel: [  132.453625] usb 2-3.2: configuration #1 chosen from 1 choice


I worked with the device and pytrainer in gutsy without any problem.

Can anyone help me to solve the problem?


thanks,
Anilael

---

### Post by Anilael on 2008-06-06
Hello!

I solved it by doing the following:

* removed graming_usb from the black list (don't know if that is needed).
* Then I located garmin_gps module in:
 /lib/modules/2.6.24-17-generic/kernel/drivers/usb/serial/garmin_gps.ko
 (it can be located by running locate garmin_gps)

* finally I run sudo modprobe /lib/modules/2.6.24-17-generic/kernel/drivers /usb/serial/garmin_gps.ko

when I inserted my garmin it received a /dev/ttyUSB0.

Anilael

---

### Post by Chuwawa on 2008-06-23
I succeeded in receiving a /dev/ttyUSB0.
I had to use the comman "sudo modprobe garmin_gps" the modprobe command posted by Anilael gave me an error.

But I still cannot read the data with my Pytrainer. When I run Pytrainer from the terminal I get the following:

> /usr/share/pytrainer//plugins/garmin-hr/main.py  --device /dev/ttyUSB0
[ERROR] GPS_Packet_Read: Timeout.  No data received.
GARMIN:Can't init /dev/ttyUSB0

I am using the garmin forerunner 50 by the way.

cheers
Chuwawa

---

### Post by fep1343 on 2009-04-12
Hi 
Connect to your GPS via "usb:"
see this post to know how to run a forerunner 305 under ubuntu

[http://www.gpspassion.com/forumsen/topic.asp?TOPIC_ID=124627]("http://www.gpspassion.com/forumsen/topic.asp?TOPIC_ID=124627")

---

### Post by Bateluer on 2009-04-26
Sorry to dig this up, but I tried this, updating the 2.6.24-17 to 2.6.28-11 for my Jaunty install, and my 305 still isn't being seen as /dev/ttyUSB0. 

When I attempt to connect to the Forerunner in MyTourbook, it says the path is invalid. I've also commented out the blacklist garmin_gps line in blacklist.conf. 

What am I missing to get this to work? 

> **Anilael said:**
> Hello!

I solved it by doing the following:

* removed graming_usb from the black list (don't know if that is needed).
* Then I located garmin_gps module in:
 /lib/modules/2.6.24-17-generic/kernel/drivers/usb/serial/garmin_gps.ko
 (it can be located by running locate garmin_gps)

* finally I run sudo modprobe /lib/modules/2.6.24-17-generic/kernel/drivers /usb/serial/garmin_gps.ko

when I inserted my garmin it received a /dev/ttyUSB0.

Anilael

---

### Post by Bateluer on 2009-04-26
Anyone?

---

### Post by fep1343 on 2009-04-27
Hi
I Keep the garmin_gps blacklisted & load manually this driver whenever I run Mytourbook to create a serial port /dev/ttyUSB0.
I use usb: for other appications with no problem.

---

### Post by Bateluer on 2009-04-28
> **fep1343 said:**
> Hi
I Keep the garmin_gps blacklisted & load manually this driver whenever I run Mytourbook to create a serial port /dev/ttyUSB0.
I use usb: for other appications with no problem.

Um, am I misreading your post? What driver?

---

### Post by fep1343 on 2009-04-29
The Garmin_gps driver. This driver creates a serial port as /dev/ttyUSB0 & has been correctly blacklisted since Ubuntu Hardy because it blocks usb: port. I keep the Garmin_gps driver blacklisted & use usb: to talk to my Garmin Gps devices. I didn't change the directory of the Garmin_gps driver. Mytourbook is the only application I use to talk to my forerunner 305 via /dev/ttyUSB0. I use a simple script to load manually the Garmin_gps driver in order to create a serial port as /dev/ttyUSB0. I am under Ubuntu Hardy & my forerunner 305 works fine. I dont know Ubuntu Jaunty. See this updated post to find how to run a forerunner & mytourbook scripts under Ubuntu Hardy. This should work also under Ubuntu jaunty.

[http://www.gpspassion.com/forumsen/topic.asp?TOPIC_ID=124627](http://www.gpspassion.com/forumsen/topic.asp?TOPIC_ID=124627)

---

### Post by lars.modig on 2009-05-05
Hi

I also tried the Mytourbook. If I run the modprobe garmin_gps (your script) the app freeze when I try to sync with the device. Before I run the modprobe it saud that I miss the com port, so something happens, but unfortentley it doesn't import anything. Any clue what I should do? Also tried the Garmin rules as I seen in the GPSpassion tree as well without sucess. Hope that someone can help me due to that I also have problem to get pytrainer running as I used before.

Br,

Lars

---

### Post by fep1343 on 2009-05-06
Hi
Concerning Mytourbook, the USB plug must be connected with the computer before the transfer dialog is opened. When the transfer dialog is opened and a serial port is not available, the data transfer can not be performed. Com ports are serial ports under Winows, in Linux they are as /dev/tty/USBx. see this post:

[http://mytourbook.sourceforge.net/mytourbook/index.php?option=com_content&task=view&id=15&Itemid=29]("http://mytourbook.sourceforge.net/mytourbook/index.php?option=com_content&task=view&id=15&Itemid=29")

I plug my forerunner 305, then, I load Garmin_gps with the script, as indicated in the gpspassion tree, to create a serial port & then I open Mytourbook application.  after transfering my tours, I unload the Garmin_gps driver. This works fine for me.
If this dosen't work for you, try GpsBabel as usb: to save your gps data on your pc & then import your tours in tcx format to Mytourbook. You must keep the Garmin_gps driver blacklisted, if not your usb: port doesn't work. Now there is a graphical interface for GpsBabel in Linux. Pytrainer is very unstable. In my opinion Mytourbook is the best one. see also this post:

[http://www.gpspassion.com/forumsen/topic.asp?TOPIC_ID=121878]("http://www.gpspassion.com/forumsen/topic.asp?TOPIC_ID=121878")

---

### Post by lars.modig on 2009-05-08
Hi fep1343,

Well, Mytourbook still freeze when I try the scripts, when I google around that seams to be "normal" with the modprobe way... But with GpsBabbel it works fine and I can download the data. BUT the problem remains... If I import an gpx file to my tour book ```
gpsbabel -t -i garmin -f usb: -o gpx -F ~/file.gpx
```
it can show everything except the heartbeats... and if I import a tcx file. ```
gpsbabel -t -i garmin -f usb: -o gtrnctr -F ~/file.tcx
```
I got the altitude and the heartrate but not the speed (but still it shows right location on the map ? But not the track...

Can you explain ? Or best of all come back with correct gpsbabbel "syntax"

Thanks, (I really need an training log :-( )

Lars

---

### Post by fep1343 on 2009-05-09
Hi Lars,

Mytourbook can download directly all of data from gps, including heart rate, altitude, speed, gradients, etc.
The gpsbabbel "syntax" is correct. In fact, Gpsbabel supports tcx format but only heart rate & altitude, no other data in the tcx file created by Gpsbabel.
Gpx format doesn't support heart rate.
You can create easily  a tcx file with all of your gps data including heart rate, altitude, speed, gradients, etc, by using TCXConverter, a free application, & import it to Mytourbook or any other application supporting tcx format & enjoy. 
For more information about TCXConverter, & to know how to install it under Linux see the updated gpspassion tutorial:

[http://www.gpspassion.com/forumsen/topic.asp?TOPIC_ID=124627]("http://www.gpspassion.com/forumsen/topic.asp?TOPIC_ID=124627")

---

### Post by Bateluer on 2009-06-10
Is there any further information on getting the Forerunner 305 to work? I've been unable to get it to under Mint 6, 7, Intrepid, and Jaunty, nor have I been able to get it to work in an XP virtual box. Furthest I can get with the virtual machine is XP seeing a Garmin USB device, but I can't get the Garmin Training Center to see the device. 

I'm assuming I'd probably run into the same problems if I bought a Forerunner 310.

---

### Post by Richard Mathie on 2009-06-24
Hello fp1343 my tour book may well work under hardy, however it is defiantly freezing under jaunty, It looks like a fantastic piece of software, and it would be nice if it work properly , however it is not working under jaunty, now lets be get to the reason why. when I run mytourbook in the terminal, (after Pluging in the switched on unit and modprobe garmin_gps) and trying to sync with the 305 the program freezes on the output (from the terminal):
```
01:13:22,449  INFO SettingsFactory:221 - Query language substitutions: {}
01:13:22,450  INFO SettingsFactory:226 - JPA-QL strict compliance: enabled
01:13:22,451  INFO SettingsFactory:231 - Second-level cache: enabled
01:13:22,452  INFO SettingsFactory:235 - Query cache: disabled
01:13:22,453  INFO SettingsFactory:369 - Cache provider: org.hibernate.cache.NoCacheProvider
01:13:22,454  INFO SettingsFactory:250 - Optimize cache for minimal puts: disabled
01:13:22,463  INFO SettingsFactory:259 - Structured second-level cache entries: disabled
01:13:22,468  INFO SettingsFactory:286 - Statistics: disabled
01:13:22,469  INFO SettingsFactory:290 - Deleted entity synthetic identifier rollback: disabled
01:13:22,471  INFO SettingsFactory:305 - Default entity-mode: pojo
01:13:22,472  INFO SettingsFactory:309 - Named query checking : enabled
01:13:22,563  INFO SessionFactoryImpl:161 - building session factory
01:13:23,531  INFO SessionFactoryObjectFactory:82 - Not binding factory to JNDI, no JNDI name configured
Experimental:  JNI_OnLoad called.
Stable Library
=========================================
Native lib Version = RXTX-2.1-7
Java lib Version   = RXTX-2.1-7

```

I think something has changed in the way jaunty installs and interfaces with the IO libery: RXTX-2.1-7 can you confirm what version of libRXTX you have I think this may be the problem
All the Best

---

### Post by Bateluer on 2009-07-06
This needs a bump. If I can get this working, I can drop Windows from my main desktop. 

I'm going try getting it to work with Virtual Box 3.0, released recently, see how that works with my XP Virtual machine.

---

### Post by jwshale on 2009-08-13
I would also really like to see mytourbook working with the Garmin 305 - it's a really promising bit of software.

Could mytourbook make use of garmintools perhaps?

For the time being, Sporttracks seems to run ok under mono, though suffers similar problems with importing from the Forerunner.

---

### Post by nilsgn on 2009-08-14
jwshale:
How do You do to run SportTracks under mono? :confused:

I hawe ubuntu 8.04. Installed mono. A downloaded SportTracks binaries.

---

### Post by fep1343 on 2009-08-29
Hi
The garmin_gps module stopped working & is buggy since updating to kernel 2.6.26 or later (ubuntu jaunty). It freezes gpsbabel, mytourbook, the terminal & even the computer. Here is a PATCH may fix the bug (I've not tested):

[http://sourceforge.net/tracker/?func=detail&aid=2821531&group_id=115375&atid=671991](http://sourceforge.net/tracker/?func=detail&aid=2821531&group_id=115375&atid=671991)

I use "garmin sync", another free tool,that communicates & saves data from Forerunner 305 in Tcx.You can download it here then run "garmin-sync" file.

[https://launchpad.net/garmin-sync/]("https://launchpad.net/garmin-sync/")

Here is a link how to install sporttracks in Ubuntu Jaunty:

[http://www.gpspassion.com/forumsen/topic.asp?TOPIC_ID=124627]("http://www.gpspassion.com/forumsen/topic.asp?TOPIC_ID=124627")

---

### Post by Bateluer on 2009-10-12
Curious, has anyone tested their Forerunners under the 9.10 Beta?

---

### Post by lars.modig on 2009-11-15
Hi Bateluer

I've not tried it under the Beta but now I upgrade to 9.10 and facing some problems...

I've running Mytourbook since ubuntu 8.10 and it has worked like a charm at every upgrade...

However now when upgrading to 9.10 the graph has disaper. I can view the statistics the tour but the altitude heartbeat and so on is invisible except where the slider is. There you see one point of the graph. So if I drag it through the time slide I can see the graph going up and down, but ...

Is there anyone that have had the same issue? Anyone who has an idea how to correct this. I really would like to stick to this software as I see as the best GPL software for GPS logging.

A second question, do someone know if you could sync the database file with UbuntuOne so that you could run Mytourbook from different computers?

Thanks,

Lars

---

### Post by fep1343 on 2009-11-21
Hi Lars

I had the same problem with Mytourbook & sporttrack under ubuntu 9.10. The problem comes from an intel driver in some notebooks. I updated to the latest intel-driver found in Tormod Voldens PPA repository & it worked for me.

Tech details:

1-Add this 

```
ppa:xorg-edgers/ppa 
```

to your system's Software Sources via synaptic package manager & reload repository in synaptic.

2- In synaptic package manager find & mark libdrm-intel1 and xserver-xorg-video-intel for update. Install them only by synaptic package manager. 
Dont use update manager for this operation if not other unnecessary packages will be also installed. 3. restart

fep1343

---

### Post by fep1343 on 2010-05-03
After upgrading to Ubuntu 10.04, garmin_gps driver works fine again & MyTourbook can talk again to Forerunner 305 via serial port dev/ttyUSB0.

---

### Post by lars.modig on 2010-05-15
Hi, I don't get it to work... When pressing the "sync button" in Mytourbook, Nothing happens... Earlier it freezed but now nothing happen even if I can see that garmin has been added to ttyUSB1. And sadly I got errors now when trying TCXConverter also...

Br,

Lars

Using Ubuntu 10.04 64bit

---

