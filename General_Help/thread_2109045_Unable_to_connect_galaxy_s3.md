---
title: "Unable to connect galaxy s3"
date: 2012-08-20
forum: General Help
---

### Post by JazzPotato on 2012-08-20
Hi there forums,
Is there any way for me to mount the samsung galaxy s3 phone in ubuntu so I can transfer music? I tried in Rhythmbox but Rhyhmbox crashes when I try to do anything involving the phone. 
Thanks in advance,
Gary

---

### Post by JazzPotato on 2012-08-20
Ok, I figured it out, so for future finders of this thread, you mount it as stp instead of mtp. Happy days :-)

---

### Post by Neutronst4r on 2012-08-25
Can you please tell us how exactly you did it? I was yet unable to successfully mount my S3 Galaxy.

---

### Post by MADDSNIPER on 2012-08-25
i noticed a great guide for doing it on an s2 for android versions past 2.3 that would also have worked for the s3 but i cant seem to find the link :/

---

### Post by Neutronst4r on 2012-08-25
The S2 and S3 are  very different. Android Icecream Sandwhich uses a new System of using the RAM. That is also why there is no UMS. MTP and PTP is all there is... 

Although I am able to get Access to the Musik folder through PTP mode, Banshee or any other Player won't recognize it as an MP3 player.

There has to be a way for Ubuntu make use of MTP mode...

It is really frustrating having a top notch phone and not being able to put some music on it.

---

### Post by MADDSNIPER on 2012-08-26
my s2 has 2.3 installed on it but i was under the impression all the new s2s come with ice cream sandwich

---

### Post by Three Tables on 2012-08-27
I would LOVE to know as well.  Can some kind soul help us newbies?  On my old HTC EVO all I had to do is plug it into ubuntu and up popped a dialog box that let one choose whether to make it only charge, or to let the pc connect to the phone as a USB storage device. Now, I am reading about that way of connecting is gone with the new technology and some people are saying they are  use FTP just to transfer photos from phone to laptops.  Seems like a royal pain compared to what an older phone can already do.

:p

---

### Post by Mark Phelps on 2012-08-27
The "problem" is actually due to Google changing filesystem mounting options with ICS.  Previously, up through Gingerbread, you could mount the filesystem as USB Mass Storage -- which, in Linux, gave you complete access to the filesystem.  When you connected an Android phone, it popped up a screen with options, one of which let you mount the filesystem as a disk "drive".

With ICS, Google has removed this option -- which is a real PAIN to me, because me S3 spontaneously overheated Friday and thrashed the default thumbnails in the phone filesystem.  They are stored in a "hidden" .thumbnails folder -- which I can't access because ICS won't let me see it.

Have heard nothing about this being "fixed" in Jellybean.

---

### Post by atomicspin on 2012-11-06
So, I know it's a semi-pain in the ***, but I did it via ES File Explorer.  I just shared the drives on my laptop that had the stuff I wanted on it (Music, pictures) and then just transferred everything across the network inside of ES File Explorer.  A bit slower but it worked 100% of the time.  

Hope this helps.

---

### Post by 1clue on 2012-12-12
So while there seem to be a couple people who know how to exchange files between SGS3 and Ubuntu, nobody has yet shown how to do it.

Could somebody remedy that?

---

### Post by knaveman on 2012-12-13
> **Auberg said:**
> Hi I am running “FTP Server” Android app, on my Samsung Galaxy Tab 8.9 
and from my Filezilla on my ubuntu i write what the ftp-app is telling me
[ftp://192.168.X.Z:2221](ftp://192.168.X.Z:2221) and the  user/ pw that it provide

hope it helps

I found this another thread and it works on the S3 as well. It's not usb, but it's something.

---

### Post by spegru on 2012-12-16
disappointed to have this mounting problem but i am currently getting around it using Dropbox

---

### Post by noelllll on 2012-12-26
I just installed Ubuntu about a week ago and when I plugged my phone in it wasn't working most of the time but every now and then it would show up on the computer. I was actually able to get a bunch of songs onto my phone before it stopped working. Anyways yeah, someone please post a fix for this?

---

### Post by IanW on 2012-12-27
As I stated in a previous thread, this works for me with an S2:- [How To Properly Mount Android 4.0+ Devices In Ubuntu Using Go-mtpfs]("http://www.webupd8.org/2012/12/how-to-mount-android-40-ubuntu-go-mtpfs.html")

You end up with an android launcher in unity which you right-click to mount or unmount your phone.

---

### Post by noelllll on 2012-12-27
> **IanW said:**
> As I stated in a previous thread, this works for me with an S2:- [How To Properly Mount Android 4.0+ Devices In Ubuntu Using Go-mtpfs]("http://www.webupd8.org/2012/12/how-to-mount-android-40-ubuntu-go-mtpfs.html")

You end up with an android launcher in unity which you right-click to mount or unmount your phone.

Would that work the same if i'm using Gnome Shell?

---

### Post by Mark Phelps on 2012-12-27
> **IanW said:**
> As I stated in a previous thread, this works for me with an S2:- [How To Properly Mount Android 4.0+ Devices In Ubuntu Using Go-mtpfs]("http://www.webupd8.org/2012/12/how-to-mount-android-40-ubuntu-go-mtpfs.html")

You end up with an android launcher in unity which you right-click to mount or unmount your phone.

OK ... and I installed that in UBuntu 12.10 -- and it does NOT work, at least, using a US Verizon Samsung Galaxy S3.  

The launcher does nothing, and all I get is error messages saying that the phone is "locked" -- which, as far as I know, it is not.

---

### Post by noelllll on 2012-12-27
I'm pretty surprised no one has figured out a hack to get around this little issue here. Got to be someone who knows what to play around with to get this working nice, no?

---

### Post by IanW on 2012-12-27
> **Mark Phelps said:**
> OK ... and I installed that in UBuntu 12.10 -- and it does NOT work, at least, using a US Verizon Samsung Galaxy S3.  

The launcher does nothing, and all I get is error messages saying that the phone is "locked" -- which, as far as I know, it is not.

Read the instructions. They say to unlock the phone (swipe/pin/face - whatever you've set it to) _before_ you try to mount it by _right-clicking_ on the launcher.

---

### Post by Mark Phelps on 2012-12-28
> **IanW said:**
> Read the instructions. They say to unlock the phone (swipe/pin/face - whatever you've set it to) _before_ you try to mount it by _right-clicking_ on the launcher.

Thank you -- but I READ the instructions -- BEFORE I did this!

And ... the phone IS unlocked BEFORE I connect it.

And, it STILL does not work.

---

### Post by QDR06VV9 on 2012-12-28
> **1clue said:**
> So while there seem to be a couple people who know how to exchange files between SGS3 and Ubuntu, nobody has yet shown how to do it.

Could somebody remedy that?

I just simply pull the card out and use the adapter that came with mine,
plug it in usb slot & navigate to files i want to add to or even remove
(MP3s, Pictures, PDFS, and so on).
But a Good Tutourial would be Great..

---

### Post by tea for one on 2012-12-28
Good afternoon

I have a Samsung S2 with Android 4.0.4, I followed the instructions on this website and succesfully transferred some music file.

[http://catlingmindswipe.blogspot.co.uk/2012/05/how-to-connect-android-samsung-galaxy.html](http://catlingmindswipe.blogspot.co.uk/2012/05/how-to-connect-android-samsung-galaxy.html)

Hopefully, it will work with the Samsung S3

Kind regards

---

### Post by 1clue on 2012-12-28
@tea for one:

SGS2 is different from SGS3.  I had the 2 and now have the 3.  SGS2 is extremely easy to transfer files, SGS3 is a pain in the rear.

---

### Post by tea for one on 2012-12-28
> **1clue said:**
> @tea for one:

SGS2 is different from SGS3.  I had the 2 and now have the 3.  SGS2 is extremely easy to transfer files, SGS3 is a pain in the rear.

It is surprising that Android 4.0 functions differently with two recent devices from the same stable.........?

Hopefully, somebody with more information will be able to help Samsung S3 owners' soon.

---

### Post by LinuxNubian on 2012-12-30
Android's Ice Cream Sandwich 4.x.x does not connect to Lubuntu 12.04. A workaround is to install Eclipse, a software developing application. It seems to only be in 32bit, but, after installing Eclipse & the suggested 32bit dependencies, I can transfer any file from my Android 4.0.4 to Lubuntu 12.04. Hope this helps someone...beating your head against a wall is no fun ;) cheers

---

### Post by Mark Phelps on 2012-12-31
Samsung SGS3 is running a version of Android from which the USB mass storage option has been REMOVED.  So, links to pages including menu entries for OLDER versions of the Android OS will do no good.

There is on USB Utilities option on the SGS3.

---

### Post by judedawson on 2012-12-31
Hi Guys, 

I also just 'discovered' this little inconvenience when I tried connecting my new Samsung G3 to my laptop running Kubuntu 12.04. 

After checking the web for info, I stumbled on to this thread recommending installing the 'AirDroid' app from the  'Google Play' store:

[http://askubuntu.com/questions/43086/how-to-transfer-files-from-to-an-android-device](http://askubuntu.com/questions/43086/how-to-transfer-files-from-to-an-android-device) (see 4th post in thread)

Tried it & it works well and is very easy to use. 

For quick and easy access, I find this method rather useful. 

I am not sure of the security and risk aspect of using this freeware app. 

From,
Jude

---

### Post by 1clue on 2012-12-31
Re:  AirDroid.

Why would it need to edit, read or send SMS and MMS?
Why would it need to take pictures or videos?

Seriously, I wish that rather than just listing the special permissions the software uses, the Google Play app would require the developer to justify each thing, and give you an ability to veto things you don't  want it to do.

---

### Post by shafin on 2012-12-31
> **1clue said:**
> Re:  AirDroid.

Why would it need to edit, read or send SMS and MMS?
Why would it need to take pictures or videos?

Seriously, I wish that rather than just listing the special permissions the software uses, the Google Play app would require the developer to justify each thing, and give you an ability to veto things you don't  want it to do.
Because it also lets you send sms and mms from your browser, and control your phone from the browser.

---

### Post by 1clue on 2013-01-01
> **shafin said:**
> Because it also lets you send sms and mms from your browser, and control your phone from the browser.

I don't need that. Why not make a simple tool for moving files, and another simple tool for sending sms or mms?

Adding all these features just happens to give them everything they need to suck all your account info out and send it to China.

---

### Post by judedawson on 2013-01-04
No worres, guys... I'm just waiting for the 'Ubuntuphone' to be released :D

---

### Post by pr3zident on 2013-01-05
you can install an app called gmtp, it's buggy but it works out for transferring files. google "gmtp" 

Hope this works out for you guys...

---

### Post by procras on 2013-01-05
This short HOWTO explains how to browse your Galaxy S3 from your linux
box.

Credit for these steps comes from:
[http://oliverkuster.wordpress.com/2012/07/13/galaxy-s3-access-files-in-linux/](http://oliverkuster.wordpress.com/2012/07/13/galaxy-s3-access-files-in-linux/)

1.
## On your Android device
## Download SSHDroid from google play 

2.
## On your Android device
## Run SSHDroid 
## Change settings in SSHDroid so that the root directory displayed is what 
## you might like

3.
# On your linux box
# Install adb
# In Ubuntu
$ sudo apt-get install android-tools-adb

4.
# On your linux box
# Install sshfs
# In Ubuntu
$ sudo apt-get install sshfs

5.
# On your linux box
# Check to see if your device is visible with adb
$ adb devices
# You should see something like
List of devices attached 
4df18b0453f35ff7	device

6.
# On your linux box
# Forward the remote SSHDroid port to your machine with
$ adb forward tcp:2222 tcp:2222

7.
# Use sshfs to create a file system link via ssh
# Issue this command
$ sshfs -p 2222 root@localhost:/storage/ ~/Desktop/sshfs
# This should throw back the prompt
~ root@localhost's password:
# enter admin, or whatever you have set the password on sshDroid to be.

8.
# Browse sshfs in nautilus or at the command line
# eg. ls ~/Desktop/sshfs

9.
# Unmount the directory
$ sudo umount ~/Desktop/sshfs
# or
# close all terminals etc that look at the mounted system
$ fusermount -u ~/Desktop/sshfs

I have managed to easily transfer files between my galaxy S3 and 3 different ubuntu boxes 12.10 using this method.

Hope it also works for you.

Adrian

---

### Post by mooz123 on 2013-01-24
Procras:

Hopeful but..
What do I do when I get this? 
'Unable to locate package android-tools-adb'

/Mark

---

### Post by GurkiratSingh on 2013-01-26
I am not able to transfer files from my galaxy s3 to my ubuntu based laptop. It gives the error "Unable to mount".

---

### Post by cwsnyder on 2013-01-26
You should probably read this article: [http://www.webupd8.org/2012/12/how-to-mount-android-40-ubuntu-go-mtpfs.html](http://www.webupd8.org/2012/12/how-to-mount-android-40-ubuntu-go-mtpfs.html)

This holds for all Android 4.0+ devices.

---

### Post by Toz on 2013-01-26
Just installed this on my daughter's laptop and she can now access her S3 from ubuntu. Thanks for the link.

---

### Post by mörgæs on 2013-01-26
Threads merged.

---

### Post by mrhacksalot on 2013-01-31
by the way I have a gs3, does any one know any "cool" tips tricks and what not I can do with it and my 12.04 I am about to have.

---

### Post by Mark Phelps on 2013-01-31
> **mrhacksalot said:**
> by the way I have a gs3, does any one know any "cool" tips tricks and what not I can do with it and my 12.04 I am about to have.

Presume this means Samsung Galaxy S3? If so, practically nothing with Linux.  

Google removed the historical USB Mass Storage mode from Android in versions ICS and newer.  So now, you have to connect it as a Media Device -- and that severely limits what you can do with it.

---

### Post by mörgæs on 2013-01-31
Moving your second question to the Samsung S3 thread. 

Please discuss only one topic in each thread. Makes it easier for other people to follow / comment.

---

### Post by mrhacksalot on 2013-01-31
> **Mark Phelps said:**
> Presume this means Samsung Galaxy S3? If so, practically nothing with Linux.  

Google removed the historical USB Mass Storage mode from Android in versions ICS and newer.  So now, you have to connect it as a Media Device -- and that severely limits what you can do with it.

Yes samsung galaxy s3.
yea I noticed that last night when trying to transfer pictures, I just figured you had to have debugging mode on or something? I will do some more research on that.

---

### Post by mrhacksalot on 2013-01-31
> **mrhacksalot said:**
> Yes samsung galaxy s3.
yea I noticed that last night when trying to transfer pictures, I just figured you had to have debugging mode on or something? I will do some more research on that.

that was weird .. went to comment on my thread and next thing i know i have commented on some one elses XD

so barely reading through the first page I hope I can be of some help .. an absolute noob can try and transfer the files on phone to exterior sd card and then plug the sd card into a card reader (which is what I did since my distro is crashing :'( ) or (not for beginers as far as I can tell )you can download the Android Debug Bridge [http://developer.android.com/tools/help/adb.html](http://developer.android.com/tools/help/adb.html) go to developer options in phone and enable and then enable usb debugging and you should be able to access EVERY file this way .. and I guess you could also install kies [http://www.samsung.com/us/kies/](http://www.samsung.com/us/kies/) on your phone and computer and share files over WLAN. But I dont think it comes stock available for linux (didnt do much research on kies) but you should be able to get it working if you really want. ;)

---

### Post by SeijiSensei on 2013-01-31
I spent $1.40 to install the Wifi File Transfer Pro app.  It turns your phone into a webserver that you can access with a browser for file transfers.  I've also tried a couple of SMB clients that can talk to a Linux box running samba.  The best one so far has been AndSMB.

Unfortunately you cannot mount remote shares on the S3 without rooting the phone.  Otherwise I'd be using NFS for everything.  I don't know if that is true were I to have a MicroSD installed.  From what I've read, that gives you more options than trying to save to /storage/sdcard0.

Wifi file transfers still seem slow, though.  I could get only about 0.5-0.6 megabytes/second with AndSMB on the S3, while I can can easily get three or four times that rate with a computer.

---

### Post by mrhacksalot on 2013-01-31
> **SeijiSensei said:**
> I spent $1.40 to install the Wifi File Transfer Pro app.  It turns your phone into a webserver that you can access with a browser for file transfers.  I've also tried a couple of SMB clients that can talk to a Linux box running samba.  The best one so far has been AndSMB.

Unfortunately you cannot mount remote shares on the S3 without rooting the phone.  Otherwise I'd be using NFS for everything.  I don't know if that is true were I to have a MicroSD installed.  From what I've read, that gives you more options than trying to save to /storage/sdcard0.

Wifi file transfers still seem slow, though.  I could get only about 0.5-0.6 megabytes/second with AndSMB on the S3, while I can can easily get three or four times that rate with a computer.


I have a ghetto rig with a $20 card reader/usb 2.0 hub in the back and I took my micro sd and put it in there so depending on your usb slot thats your transfer rate .. along with the rest of your computer .. processor speed and hdd what nots lol and I should be getting a blue-tooth dongle soon so that should make for another way of transferring, but as you said wireless connectivity is slow..
P.S. I dont think you have to root your phone to turn on usb debugging? at least with my s3 I dont .. idk about my revo I will check.

---

### Post by mrhacksalot on 2013-01-31
lmfao I forgot I rooted my revo XD

---

### Post by SeijiSensei on 2013-02-01
I was referring to wifi transfer rates.  The lack of good support for MTP in Linux is why this thread exists.

I also have no idea what a "ghetto rig" is, but that is not a word I would use when describing a piece of hardware, particularly in a forum with a global readership.

---

### Post by cwsnyder on 2013-02-01
Update on method to connect Ubuntu and an Android 4.0+ device:  Check out the article at [http://www.webupd8.org/2013/01/upgrade-to-gvfs-with-mtp-support-in.html](http://www.webupd8.org/2013/01/upgrade-to-gvfs-with-mtp-support-in.html) which includes a PPA link to more easily connect.

---

### Post by Brain Juice on 2013-02-13
> **cwsnyder said:**
> Update on method to connect Ubuntu and an Android 4.0+ device:  Check out the article at [http://www.webupd8.org/2013/01/upgrade-to-gvfs-with-mtp-support-in.html](http://www.webupd8.org/2013/01/upgrade-to-gvfs-with-mtp-support-in.html) which includes a PPA link to more easily connect.

Thank you!

---

