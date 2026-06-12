---
title: "File transfer to/from Android phone"
date: 2021-12-08
forum: General Help
---

### Post by nought2 on 2021-12-08
When trying to transfer data from my old Samsung Galaxy S6 Edge to my new Google Pixel 6 I've hit a snag.

Data transfer between my Ubuntu 20.04 system and Samsung S6 has always been straightforward. Connect phone to PC via USB cable; Nautilus detects phone immediately; touch 'allow' on phone's screen to give permission for PC to access phone; after which I could freely transfer files to and from phone and modify files on phone. Once job was done I hit the Nautilus eject button beside S6 listing and all was good.

Same process is not working with Pixel 6. After connecting phone to Ubuntu system the phone gives a haptic buzz and nautilus lists Pixel 6 in its left margin. But I cannot access phone's files.

Notification appears at top of PC screen listing Pixel 6; moving mouse cursor over it causes 'Open with Files' notice to appear; clicking it opens Nautilus window displaying 'Folder is empty' notice. Same notice is seen if I select Pixel 6 listing in Nautilus left margin.

The phone does not display a notice asking for PC to be allowed to access its files.

I've tried to find a remedy via phone's settings...
Settings > Connected devices > USB ... lists the following options:
--USB conrolled by:
Connected device
This device    (radio button checked)
--Use USB for:
File transfer/Android Auto
USB tethering
MIDI
PTP
No data transfer   (defaults to this radio button checked soon after plugging in USB cable)

Selecting 'File transfer/Android Auto' doesn't work either.

I thought the job of moving data to new phone was going to be super easy. Have I missed something?

Pixel 6 is running Android 12.

---

### Post by T6&amp;sfpER35% on 2021-12-09
seems it's a cable problem
[https://askubuntu.com/questions/1378047/file-transfer-from-pixel-6-android-12-to-ubuntu]("https://askubuntu.com/questions/1378047/file-transfer-from-pixel-6-android-12-to-ubuntu")

---

### Post by nought2 on 2021-12-09
Hmm. I'm using USB-A to USB-C cable bought new yesterday for this task.

PC has only USB 2.x and USB 3.x sockets fitted; they accept USB-A male plugs. 

Might need to look for USB-A (male) to USB-C (female) adaptor. That would permit me to use supplied USB-C to USB-C cable.

---

### Post by T6&amp;sfpER35% on 2021-12-09
> Might need to look for USB-A (male) to USB-C (female) adaptor
don't think that'll make a difference , it's still gonna be usb-a to usb-c .
when i posted my 1st reply i still thought now how one suppose to connect usb-c to a pc , i don't know of any pc that has a port like that , they're all usb-a
maybe try a cable like mentioned in the link ..."Perhaps another good solution, in general, is to choose a cable that is designed for fast data transfer."
might not even be the cable , but that's all i could find in a search, all other solutions i found , you already tried.
could aslo use **kdeconnect**,but i found it to be a bit of a hassle, cable works much easier .

---

### Post by tea for one on 2021-12-09
Have you considered the gnome-extension [https://extensions.gnome.org/extension/1319/gsconnect/](https://extensions.gnome.org/extension/1319/gsconnect/)

More info here [https://www.omgubuntu.co.uk/2018/11/connect-android-ubuntu-gsconnect](https://www.omgubuntu.co.uk/2018/11/connect-android-ubuntu-gsconnect)

---

### Post by T6&amp;sfpER35% on 2021-12-09
**gsconnect** , so i learn something new everyday lol
wish i knew this before the days i battled with kdeconnect to ...well,connect 
:eek:
also ,if you do try kdeconnect (maybe gsconnect has same issue) , one has to disable firewall 1st time you want to connect. 
that was basically the 1st obstacle i encountered trying to connect

---

### Post by tea for one on 2021-12-09
@3nd 
As you mentioned in post 4, I also use a USB A to USB C cable to connect Ubuntu to Android.
I used gsconnect for a few months but found that the cable connection was easier than an application.

My current phone (and previous phone) has a removable SD card because that is always a reliable transfer method when applications disappear and cables fail.

---

### Post by nought2 on 2021-12-09
Bought another USB 3.x A-to-C cable today. First one was 2m and admittedly el cheapo. Second one is 1m, arguably better quality but not primo by any stretch. 

Minutes later tried out 1m cable with PC. Uh oh, not working. Computer parts shop is nearby, went back with thoughts of returning 1m A-to-C cable. To my very good fortune the guy serving was super familiar with Android phones having worked in retail for a big Aus telco flogging phones et al. Wow, he could gallop through Android 12 interface at an astonishing pace.

His first move was to prove cable worked with my Pixel 6 handset - yes, cable supplied power. OK, I'd already got that far myself. How about data transfer? His route to same settings I had adjusted was via notifications menu pulled down from top of home screen...

Relevant small tile reads: Charging this device via USB
&#8594;select V (down arrow) to expand
&#8594;Tap for more options
&#8594;this opens 'USB Preferences' menu within Settings
Then select 'File transfer/Android Auto' radio button
In Nautilus window for Pixel 6 'Internal shared storage' folder appears. Hooray!

After that we could explore Pixel's files, at least on his Win 10 machine. 

Maybe problem was with Linux or Ubuntu? Tried same technique on my Ubuntu 20.04 system and it worked. Phone is happy with 2m cable bought yesterday too. Both cables are good after all.

The detail of Android navigation (from notifications menu, not via apps >  settings > connected devices > USB) is important. Weird though.

Mentioned to guy in shop that I was exasperated by process of migrating data from old phone to new. He had more sage advice there: try Samsung Smart Switch. It can do transfer via wifi or cable. USB A-to-micro Cables that have worked happily with Samsung S6 for yonks are not accepted by fussy Pixel 6. Will go on excursion soon to a venue with wifi to search for further success. Edit: SSS did not work at wifi place, sigh. Cable transfer it is.

Re: KDE connect. I have tried it in the past with same S6 phone and a couple of Ubuntu systems. It works but is a bit flaky, and using the wifi hotspot from my phone it's slow. Cable is fast and reliable.

---

### Post by T6&amp;sfpER35% on 2021-12-10
> this opens 'USB Preferences' menu within Settings
Then select 'File transfer/Android Auto' radio button
i saw that when i searched , but thought you tried it already 
> Selecting 'File transfer/Android Auto' doesn't work either.
glad your'e sorted though
:)

---

