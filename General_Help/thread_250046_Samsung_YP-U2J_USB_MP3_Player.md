---
title: "Samsung YP-U2J USB MP3 Player"
date: 2006-09-03
forum: General Help
---

### Post by lemix on 2006-09-03
I just got a Samsung YP-U2J USB mp3 player but i cant seem to upload or download files from it. 

dmesg|grep usb   shows this...
> [17179580.500000] usbcore: registered new driver usbfs
[17179580.500000] usbcore: registered new driver hub
[17179581.872000] usb 3-1: new low speed USB device using ohci_hcd and address 2
[17179594.524000] usbcore: registered new driver hiddev
[17179594.532000] input: USB HID v1.10 Mouse [Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)] on usb-0000:00:03.2-1
[17179594.532000] usbcore: registered new driver usbhid
[17179594.532000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17226873.496000] usb 4-2: new high speed USB device using ehci_hcd and address 3
[17226873.696000] usb-storage: device found at 3
[17226873.696000] usb-storage: waiting for device to settle before scanning
[17226873.696000] usbcore: registered new driver usb-storage
[17226878.912000] usb-storage: device scan complete
[17227210.924000] usb 4-1: new high speed USB device using ehci_hcd and address 4
[17227211.056000] usb-storage: device found at 4
[17227211.056000] usb-storage: waiting for device to settle before scanning
[17227216.280000] usb 4-1: USB disconnect, address 4
[17227216.280000] usb-storage: device scan complete
[17228211.364000] usb 4-1: new high speed USB device using ehci_hcd and address 5
[17228211.496000] usb-storage: device found at 5
[17228211.496000] usb-storage: waiting for device to settle before scanning
[17228216.720000] usb 4-1: USB disconnect, address 5
[17228216.720000] usb-storage: device scan complete
[17228409.448000] usb 4-2: USB disconnect, address 3
dom@dom-Area-51m:~$ dmesg|grep usb
[17179580.500000] usbcore: registered new driver usbfs
[17179580.500000] usbcore: registered new driver hub
[17179581.872000] usb 3-1: new low speed USB device using ohci_hcd and address 2
[17179594.524000] usbcore: registered new driver hiddev
[17179594.532000] input: USB HID v1.10 Mouse [Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)] on usb-0000:00:03.2-1
[17179594.532000] usbcore: registered new driver usbhid
[17179594.532000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17226873.496000] usb 4-2: new high speed USB device using ehci_hcd and address 3
[17226873.696000] usb-storage: device found at 3
[17226873.696000] usb-storage: waiting for device to settle before scanning
[17226873.696000] usbcore: registered new driver usb-storage
[17226878.912000] usb-storage: device scan complete
[17227210.924000] usb 4-1: new high speed USB device using ehci_hcd and address 4
[17227211.056000] usb-storage: device found at 4
[17227211.056000] usb-storage: waiting for device to settle before scanning
[17227216.280000] usb 4-1: USB disconnect, address 4
[17227216.280000] usb-storage: device scan complete
[17228211.364000] usb 4-1: new high speed USB device using ehci_hcd and address 5
[17228211.496000] usb-storage: device found at 5
[17228211.496000] usb-storage: waiting for device to settle before scanning
[17228216.720000] usb 4-1: USB disconnect, address 5
[17228216.720000] usb-storage: device scan complete
[17228409.448000] usb 4-2: USB disconnect, address 3


Does anyone know the solution to this problem?
Thx in advance.

---

### Post by Apples on 2006-09-19
I have the exact same problem! If anyone could help, I'd be really glad!

---

### Post by compuguy1088 on 2006-09-19
I'm guessing this is just a player that when its plugged in is supposed to mount like, say a flash drive?

---

### Post by veruca on 2006-10-02
yes it is SUPPOSED to but the yp-u2j doesn't, if you aren't going to help, don't post.

I just bought one and it isn't working for me either. Working on a fix.

---

### Post by orb9220 on 2006-10-02
> yes it is SUPPOSED to but the yp-u2j doesn't, if you aren't going to help, don't post.

**veruca** the guy just asked a question to clarify is understanding what kink  of mp3 player since not all are not reconized as a usb device. The community here is quite helpful to problems that new user's are having. However the community does frown on new people coming in and being rude to someone asking a questions.

Now from my experience some mp3 players use their own kinda of formating, Some who had these problems booted into a windows machine and did a reformat of the device and then it was seen in linux fine.

Some it booted fine in the first place and they just didn't know to look in their /media/ folder for the device.

Another problem is what the player is set to mine a sansa m230 was set to auto but also has an MSC setting and scandisk site mentions an MTP setting for subscription music services.

The main solution tho is to reformat the device on windows to fat32 and try again.

Hope some of this is helpful if not sorry I tried.

And lighten up on people who ask for more info and don't post a solution for you.

---

### Post by veruca on 2006-10-02
Maybe I read into the reply too far. Apologies if thats the case.

This is what I've found so far:

The yp-u2j does NOT support OGG, that is the first important point (if it matters to anyone besides myself).

The yp-u2j doesn't seem to have any firmware upgrades, and the upgrades that were available on the samsung website were removed because microsoft had its panties in a bunch about the play for sure setup and it said that they are NOT to support OGG formats in their players. I've been looking for 3rd party firmwares but very unsuccessful. Either way you are going to need a windows machine to get you started, which I do not have (linux all the way). So, becaues I'm lazy, I'm just going to return it and get one that works. =)

---

### Post by orb9220 on 2006-10-02
Yea the sansa are cheap and work like a champ mines a sansa m230 512mb I got for $50 and works great. I don't like the ipod's tho the newer ones break compatiability on purpose which older ones work in linux fine but not the newer ones these is a big complaint even on winXP machines.

There are some recommend threads here on which player to get for linux.
Good luck and I would take it back instead of fighting with it.

---

### Post by uid0 on 2006-10-10
I did a little snooping and found that the YP-U2J uses MTP, which is a format used by the microsoft "PlaysForSure" DRM scheme.  I've compiled and installed  libmtp from sourceforge but have had limited success.  The player shows up for about 5 seconds and then disappears:

# ./detect
Autodetected device "Samsung YP-U2J (YP-U2JXB/XAA)" (VID=04e8,PID=5054) is known.
usb_claim_interface(): Device or resource busy
Connection error.
No devices.

And that's about it....

---

### Post by melvinpelvinoksi on 2006-10-17
Well I just bought the samsung YP-U2J(ZW) and it is a great little player.  But there is a little info you need to get the most out of it.  I primarily wanted an ogg player that was mass storage and small.  So when searching out a player that is how I searched so it lead me to:

[http://wiki.xiph.org/index.php/Talk:PortablePlayers#Yepp_YP-U2](http://wiki.xiph.org/index.php/Talk:PortablePlayers#Yepp_YP-U2)

This tells which firmware to flash this device with to get not only ogg but mass storage, and works after the flash in Dapper right off of the bat.  It is a pain to flash (press play, insert into usb, reset with a pin, still holding play start the updater and hold play all the way through).  After that it was done and works like a charm still trying to figure out the play lists but I mostly use it for podcasts so that is not reall an issue.

---

### Post by uid0 on 2006-10-30
Yepp (pun intended), that did it! :-D 

Just make sure you go to the global download center link at the bottom of the page.  Here's the URL I used:

[http://www.samsung.com/Support/ProductSupport/download/index.aspx](http://www.samsung.com/Support/ProductSupport/download/index.aspx)

Again, make sure you click on the blue "Global Download Center" link near the bottom of the page. 

I upgraded my firmware to 1.305 and I'm now able to see the player just fine under Dapper & Edgy and I can copy file to/from it just like a flash drive.

---

### Post by lemix on 2006-11-06
Im not sure if samsung would take a firmware upgrade down off their page. But they do not have an update to 1.3## for either the YP-U2JXB, which is mine, or the YP-U2JZW, which is yours.

Another possible alternative may be that i am blind.

---

### Post by lemix on 2006-11-06
Very good news!

The Samsung YP-U2JXB should support OGG playback for those who were interested in that!

Bad News.
The Firmware was taken off there site

GOOD NEWS!
I Put it on my site! Sorry about the large link for this file but, its gonna make you very happy in the long run...
> [www.guihacker.com/Ubuntu/20060428084921640_U2_ver1301_OC.zip](www.guihacker.com/Ubuntu/20060428084921640_U2_ver1301_OC.zip)

---

### Post by lemix on 2006-11-06
okay trying to install the firmware for SAMSUNG MP3 players i have to say is about equal to spinning three glass plays on metal rods while standing on your head on top of an aircraft carrier.

I believe that it is almost impossible, if anyone has one, before you try to install the firmware, read the instructions and realize how rediculous it is and then just accept the fact that you just wasted some of your money.

---

### Post by Vokstin on 2006-11-14
Hi, I'm new to this forum, and I wasn't sure if I post my question here. I'm wondering if anyone can help me with my Samsung YP-U2J USB MP3 Player. I got it about 3 months ago and it worked fine. But for some reason it stopped connecting to my computer through the USB. Thanks in advance if anyone can help.

---

### Post by Neobuntu on 2007-02-14
OK, I just got one (YP-U2J-ZW) and it says firmware version "1.01b" and it works just fine both in Windows XP  Pro updated and Edgy upgraded (and a test of Fiesty too).

So if I'm using MP3 why should I upgrade?

I can only guess that an upgrade between mine and version 1.351 broke mass storage. Anyone know or have a change log?

---

### Post by Neobuntu on 2007-02-15
UPDATE: Problem solved.

The problem I had was songs in a folder starting with (two digit) numbers did NOT sort numerally but alphabetically and so some CD's are meant to be heard one after the other.

At the US site I downloaded a 1.36 version and it did not work. Still it was alphabetical and NOW it wouldn't show up as a drive on Windows (XP) or Kubuntu (edgy).

So just like posts that I found, I downloaded the 1.351 version (From the Australia site)  and now everything works!

Mine is a YP-U2J with a ZW too.

The trick part was finding the html help page (unzipped download) under the /Help folder. This tells you the tricky process to get the drive to recognize.

Prepare by inserting the device, wait a good while for it to register, and IF the icon shows up in the task bar, do a "Safely Remove" process (but do not physically remove it, of course).

1. Hold down the play/on button (and keep it down the whole time. So you may want to use an extension cable and you might want to(have to) plug it into the back on the computer USB ports; directly to the motherboard.)

2. While holding the above play button still, put a pin in the reset till you feel it give, let it go but keep hold of the Play button. 

3. Now (after installing the download by running "setup" in the unzipped folder) click the update icon on the desktop.

4. Here's where it gets tricky and long. Now you might see (as I did) a dialog asking you to install new device. Click no to the Internet and WAIT for the next screen "Player Recovery Device Class". Be patient, finish that and finally you will see the next screen of the updater. 

Note: At this point (as it did with me going back to a version) you may have to erase all to do the firmware upgrade. So be sure you have copied over your music before you OK a (sometimes) required reformat of data space. FYI, my upgrade didn't require this but my downgrade did.

5. Don't let go! :P till the bars stop and it says done. Crazy. But that's how it's done.

6. Remove, turn it on, check the version number off the system/about menu. 

Enjoy!

P.S. I set the ripper "K(something)ripper" for LAME (in settings) and took out stuff in the naming string so the a song reads short like this: "01 Song name", without anything before the "01" or any number. Now I do not need play-lists (with this firmware v1.351) and my battery saving time-out light does not go out before I can read the scrolling name. I can always go back to the album folder name they are in. Yet I do not think one can put another CD from the same artist in the same main (artist) folder. Unless you want them mixed and played as one.

***ADDENDUM: I set the name string back to the default in the KDE ripper program so that it would stay working and making directories for it's output. I then used Krenamer (sp?) to fix the names (in bulk) to look best on the player.  

P.S.S By the way, I tested the wonders of Windows Media Player 11 and it was buggy as heel. It wound NOT let me find name for some of my CD's. It had screen errors. It locked up "not responding" and no matter what I did (long story like validation time wasted) It will NOT let me go back to WMP 10. I know, I know, who needs that DRM crap anyway! Bye Windows! I may not even keep it for testing; much longer. What with KMyMoney taking the place of Quicken, I'm good. The point is. Kubuntu may waste too much of our time BUT NOT AS MUCH AS WINDOWS DOES!

---

### Post by fherkobaimmora on 2007-05-29
hey, this look you know very much of this. I wanna know how to change the MTP to UMS.... Please save my life..
the model is YP-U2JZW /XAA 
plis tell my if is it possible or not and how I can get to change it

---

### Post by Jamie pratt on 2007-06-24
So ive had a YP-U2J for a while now, well siince november 5th when i got it for my birthday, and it works great, but my only problem is it goes wacky when it dies. I always have it on becuase i have to walk to swim practice in the morning then back home, and generally i have to walk to work to, so i listen to it a lot, and some times i forget to plug it into my computer to charge it. I did this recently and it died on me, and it wouldnt charge in my computer, i have a pc, during the school year, if i died id jsut take it to the library at school and stick it into one of the macs and it would charge, so basically im just wondering if anybody knows why it only charges in macs, nt in pcs, when its completly dead.
                     P.S. i have it charging right now cuase my friend happens to have a mac and i stuck it in there while i was at his house, then brought it abck home and its charging fine in my computer now that it as some amount of battery left.

---

### Post by yeshuafollower on 2007-07-09
YP-U2JQB/XAA recycling through the connecting / disconnecting / reconnecting "found new hardware" issue:

Great news about this model's issue (or maybe about the company itself). I called their 800 number and got the problem resolved by their Tier 2 customer support. She said that I needed to install the firmware updater from their site and then plug the player into a USP port that I haven't used before for this device while holding the play button. Windows then recognized the player. She then told me to launch the firmware updater and let it do its thing (telling it to format the device). My player works now.

The problem was that the YP-U2J would continually recycle through the "found new hardware" / "problem with new hardware" messages while connecting/disconnecting/reconnecting itself. It works now as it should. :)

Hope this helps someone somewhere someday.

By the way, after reading various reports about their bad customer service, it would seem that Samsung has proven those reports wrong (maybe by reading those same reports themselves). The Tier 2 support was more than ready to have me ship it in for service.
:)

---

### Post by parkr1 on 2007-08-22
I couldn't find the 1.351 firmware last night, so I used the 2.211 firmware that's on the Samsung Australia download page for the YP-U2X player ([www.samsung.com/au/support/index.asp](www.samsung.com/au/support/index.asp)).

I also had the problem where I couldn't re-use the USB  port that I used to "reset" the device. But I just rebooted XP, and then I could use the port to update the firmware. My computer's rear USB ports are tough to get to, so rebooting was less of a hassle than using the rear USB ports.

---

### Post by Aldanga on 2007-08-29
Something is either wrong with my connection or Samsung's servers because I cannot download anything from the Samsung website.

Does anybody have the firmware files still on their computers? I would really like to fix this glitchy thing.

Thanks.

*edit*

Nevermind. The site's up again.

---

### Post by jppaynesr on 2007-08-30
For what it's worth, I use the Creative MUVO V100 to listen to podcasts & mp3's. 
You can load myPodder ( podcastready.com) directly onto the device. It is OS independent and runs on my Ubuntu system with no issues. It will go out to the podcastready site, see what you have subscribed to, and synch it. I have had a few index issues when I use XP to download some podcasts, so it is better to run it from just one OS.

For music I just drag & drop what ever I have on my PC to another folder on the MUVO.

---

### Post by YoshiHNS on 2007-10-18
i have had the yp-u2 for quite some time too. There's something up with the firmware where when the battery goes completely dead, you get the connect/disconnect/connect/disconnect deal.

One resolution is to uninstall Win Media player 11, and maybe 10, and go all the way back to 9. Not sure why but that worked for me a couple times. I believe it has to do with the MTP driver. I don't believe 9 had it, and without it the computer will recognize it like any old flash drive. Just use the Samsung updater and update WMP again. Worked for me twice.

Just happened to me now, and a quicker fix was plugging it in, holding play, pressing reset, releasing play. Not sure why that worked, unless that is the hard reset procedure.

Yes, the website is useless for firmware/drivers. the program works fine. I'm updated to 1.56.876.

---

### Post by wonko the sane on 2007-12-30
arr.

I can't find any firmware more recent than 1.156 (on samsung us, canada, australia, or global, or anywhere)... am I blind? Could anyone point me to where I should be looking?

Thanks.

---

### Post by Sonja on 2008-01-16
I went in WinXP to install the new firmware from their website. Great success! But when I plug it into my computer under Ubuntu, it does not pop up or notice it. How do I mount it?

---

### Post by rare HERO on 2008-01-17
Works when I first plugged it into my system. reads like a removable drive. I shall assume that it will work for all other purposes. I originally purchased it to work as a voice recorder. If it stops working I'll repost.

I have a ZEN stone that works well with my system.

I use Ubuntu 7.10

---

### Post by TDolce on 2008-05-13
I have the lousy YP-U2JQB player and I have no problem with the player being accessible once plugged in, but my issue is how to get it to be recognized as a "STORAGE" device so I can access it with Music Recovery software? It never gets recognized as a storage device but rather is classified as "other" device. This is ridiculous. Anyone????

---

