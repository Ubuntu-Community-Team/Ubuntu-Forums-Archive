---
title: "can't  receive files via bluetooth"
date: 2008-04-29
forum: General Help
---

### Post by moonlighthd on 2008-04-29
Hi
i just can't receive files via bluetooth.

the thing i do is that i have the bluetooth icon near the clock 
i right click on it
i have send a file 
BUT no receive a file

Any suggestions???? please 
 
thanks in advanced 

note that i am using ubuntu hardy

---

### Post by GCoffee on 2008-04-29
Do you have a bluetooth adapter inserted into your pc? If not, you need one.

---

### Post by robbie75 on 2008-04-30
> **moonlighthd said:**
> Hi
i just can't receive files via bluetooth.

the thing i do is that i have the bluetooth icon near the clock 
i right click on it
i have send a file 
BUT no receive a file

Any suggestions???? please 
 
thanks in advanced 

note that i am using ubuntu hardy

I'm having a similar issue: when on gutsy i was able to send/receive files by bluetooth, then after upgrading to hardy,
i can send files but receiving always fails...
Double checked my setup and everything seems ok...very weird :-?

---

### Post by The AlGorenator on 2008-04-30
I always found the the default bluetooth applet couldn't recieve at alll, so installed a program from the repos to do it. Ran that program and the computer became visible and was able to recieve files.

Not on my main comp now so i can't tell you what it's called, but go through add/remove programs and the icon looks vaugely like a ble wifi logo and it no doubt will come up when you filter for bluetooth.

---

### Post by Timbothecat on 2008-05-01
How did you guys set up your virtual serial port? I'm assuming you had to do this in order to receive and send files via bluetooth but I can't figure out hoe to do this in order to sync my PDA (Palm Tungsten E2).

I have posted a thread asking about this but have had no responses so I thought I might ask you guys how you managed to do it.

If you can help out here it would be greatly appreciated.

All the best,

Tim.

---

### Post by cosminb on 2008-05-01
I believe the program is gnome-obex-server, appearing as "Bluetooth File Sharing" under Applications->Accessories. I have the same problem, cannot receive files, I have attached a hcidump at [http://ubuntuforums.org/showthread.php?t=777330](http://ubuntuforums.org/showthread.php?t=777330). It seems the connection is performed, the phone queries the laptop for supported services, doesn't find support, then disconnects. But I don't know why this happens, sending works, receiving doesn't work...

---

### Post by cosminb on 2008-05-01
Also, some say there might be a bug in bluez-utils 3.26. I'm trying to figure this one out, maybe it will work.

---

### Post by robbie75 on 2008-05-08
Same issue for me too: send/receive worked when on gutsy, now on hardy i can only send from pc to phone but not viceversa.
I can even browse my phone files....weird

---

### Post by cosminb on 2008-05-09
Indeed, the problem is the faulty bluez. Please see the thread I mentioned earlier for the solution I found (downgrade).

---

### Post by tanas on 2008-05-09
Downgrading did it for me!

(So my problem was that AFTER the upgrade to Hardy, I could no longer send files from the phone to the computer.. but the other way around was ok)-

I downgraded the bluez-utils in synaptic to the gutsy version (3.19, just add 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main
to the repositories list) and now my computer is again able to receive files from the mobile phone.

---

### Post by cszikszoy on 2008-06-15
Anyone have any idea on when an updated bluez-utils will be pushed out to Hardy users?

---

### Post by cosminb on 2008-06-16
No updates for hardy yet (I don't know about other distributions though). Still hanging with 4 pending updates, it's quite annoying...

---

### Post by cszikszoy on 2008-06-16
Kind of sad that this is *supposed* to be a LTS release.  I feel like Gutsy was more stable and feature-complete.

---

### Post by speedsix on 2008-06-20
Bump for the same problem

---

### Post by pjalegria on 2008-07-05
same problem:(

---

### Post by fragos on 2008-07-05
You may find "blueman" helpful in the future. It performs many bluetooth management functions as a GUI. This includes pairing with headsets.

---

### Post by darkworld on 2008-07-06
Hi

I have the same problem, is there a bug running in launchpad? Im getting quiet down about Hardy, I run fiesty for a year and was fine, now ive had loads of broken apps that used to work.

I tried adding the gusty repo as suggested and its been added to synaptic but theres no sign of the bluez util 3.19 ??? Am I doing something wrong?

The app " Bluetooth file sharing" used to work and thats bust too, for me anyway. Does that use bluez-utils???

Edit: I got 3.19 manually and it didnt sort. Reloaded utils 3.26 and waiting for fix....i need to get pics off phone onto pc.

---

### Post by darkworld on 2008-07-06
Can somebody please advise me.

I have loaded Blueman, I can transfer from my PC to my phone but every time I try to transfer photos to PC it says transfer failed.

Blueman bluetooth manager shows my phone and shows two way communication symbols, its bonded and trusted. Im ripping my hair out!

Any help would be very appreciated.

The only other solution I can think of is to down grade to gusty!

---

### Post by fragos on 2008-07-06
My phone has a micro-SD card so I use a card reader. I do the same with my digital camera -- saves camera battery. Even in Gutsy, bluetooth file transfer for me was one way. I do send file to my PDA with bluetooth.

---

### Post by issih on 2008-07-06
Um, I risk upsetting you all if you have already tried this, but have you tried right clicking on the bluetooth icon, and opening up preferences.

In there if you go to the general tab there is a file transfer section. If you tick the "Recieve files from remote devices" box you should find everything suddenly works.

It did for me anyway, no need for the bluetooth file sharing program anymore either.

I think I did need to reboot however, not sure about that though.

Hope that helps.

---

### Post by darkworld on 2008-07-07
> In there if you go to the general tab there is a file transfer section. If you tick the "Recieve files from remote devices" box you should find everything suddenly works.

Been there tried that. This is very frustrating, fiesty works, Hardy doesnt.

I get sending failed from phone. I get the same in Blueman. If I go browse device in either gnome bluetooth or Blueman Bluetooth manager I then get the my phone Icon on desktop and window opens. It seems to be a window which is the root of my phone. Its empty, no files no folders.

Properties of phone capacity 0 bytes. so its seen the phone but no phone memory/flash memory???

I then tried dragging a jpeg into the browse phone window and get this:> There was an error copying the file into obex://[00:19:79:85:19:49]/. more details: operation not supported by backend 



Next I open Blueman GUI and do inquiry then browse device, 2 way comms is established. Phone at 0 bytes icon on desktop again, same error as above if I drag a jpeg onto device window. 

If I do send file from PC it sends to phone. I have it set as trusted and bonded. Try to send from phone even though the phone is clearly connected, sending failed.

Nokia N70, 1 Gb flash. No probs in fiesty with this hardware.

Ok the info which says 'operation not supported by backend might be related or maybe just saying you cant place a jpeg in a 0 byte memory area.

Any ideas???? (thanks for the suggestion of using flash reader, that gets me out of immediate problem :KS but hey I want my bluetooth back! :()

edit: I found this link [http://jonramvi.wordpress.com/2008/02/26/how-to-transfer-pictures-music-and-videos-from-and-to-your-nokia-phone-using-bluetooth-in-ubuntu/]("http://jonramvi.wordpress.com/2008/02/26/how-to-transfer-pictures-music-and-videos-from-and-to-your-nokia-phone-using-bluetooth-in-ubuntu/") i also found another user on Blueman with similar problem. Note at bottom of this page a user states S60 3rd edition is not supported. I think N70 is 2nd edition. Could it be my phone is not supported?????

---

### Post by darkworld on 2008-07-09
Ok I found this bug report and it seems a patch is available, I dont know how you apply this patch if someone could help me i would be very grateful, this is what was posted on launchpad.


Bug 211252 in bluez-utils


> 

    * debdiff (1.4 KiB, text/plain)

Hi,

please find attached a debdiff which includes the upstream patch from [http://bluez.cvs.sourceforge.net/bluez/utils/sdpd/request.c?r1=1.22&r2=1.23&view=patch](http://bluez.cvs.sourceforge.net/bluez/utils/sdpd/request.c?r1=1.22&r2=1.23&view=patch) (comment 59).




---

### Post by espmartin on 2008-08-14
Any answers?

---

### Post by cszikszoy on 2008-08-14
> **espmartin said:**
> Any answers?

If a patch is available, and this issue has been fixed upstream, why hasn't ubuntu made this patch available via the repositories?!

---

### Post by fragos on 2008-08-14
Bluetooth file transfer with my Palm E2 and Ubuntu is one way but works in both directions with my newly purchased Nokia N810.

---

### Post by sayakb on 2008-08-14
This works perfectly:
Activate bluetooth on your laptop/desktop as well as your mobile device. Now right click on the bluetooth icon in the notification area and click [B]Browse Device...
[/B]Select your phone from the list and press Connect. You will be prompted on your phone to accept the connection from your laptop and you may be asked for passkey. After you allow the connection (by entering passkey if asked for), the phone will open up as a folder in your laptop and you can browse and copy items from it.

---

### Post by cszikszoy on 2008-08-14
> **LinuxIsInnovation said:**
> This works perfectly:
Activate bluetooth on your laptop/desktop as well as your mobile device. Now right click on the bluetooth icon in the notification area and click [B]Browse Device...
[/B]Select your phone from the list and press Connect. You will be prompted on your phone to accept the connection from your laptop and you may be asked for passkey. After you allow the connection (by entering passkey if asked for), the phone will open up as a folder in your laptop and you can browse and copy items from it.

Thanks for the reply, but what all of us (in this thread) have an issue with is Hardy refusing to accept files that are SENT from a mobile device.  Browsing works fine for me.  But, in Gutsy, I was able to select an item on my phone, and on my phone, select "send via bluetooth", then select my laptop.

On Hardy, this fails instantly and the phone reports that the recipient cannot receive files.

---

### Post by espmartin on 2008-08-14
I agree with cszikszoy,

I can browse fine, but can't transfer. I get that "operation not supported" error

---

### Post by ragflan on 2008-08-14
Bluetooth works both ways for me. Try these few steps and see if it works for you. 

1.) Check if Bluetooth applet is running (there should be a Bluetooth icon in your system tray). If not, press ALT+F2. **bluetooth-applet**
2.) There should be a bluetooth icon in your system tray/notification area.
3.) Right-click it --> Preferences. Set the options just like the screenshots below. 

[IMG]http://ramipage.googlepages.com/Screenshot-BluetoothPreferences-1.png[/IMG] [IMG]http://ramipage.googlepages.com/Screenshot-BluetoothPreferences-2.png[/IMG]


4.) Now try sending a file from your phone or bluetooth device. It should work. 

If it doesn't work:

1.) Open up Add/Remove from Applications. Search for bluetooth and mark **bluetooth file sharing** for installation. 
2.) After it's installed, open it from Applications --> Accessories --> Bluetooth File Sharing. There should be an icon in the system tray/notification area. 
3.) Try sending again from your bluetooth device to your computer.

---

### Post by cszikszoy on 2008-08-14
> **ragflan said:**
> 1.) Open up Add/Remove from Applications. Search for bluetooth and mark **bluetooth file sharing** for installation. 
2.) After it's installed, open it from Applications --> Accessories --> Bluetooth File Sharing. There should be an icon in the system tray/notification area. 
3.) Try sending again from your bluetooth device to your computer.

This worked in Gutsy, but *not* Hardy.

---

### Post by olavjunior on 2008-08-16
I'm having the same issue. Can't receive files from n95 or macbook air. This worked in Gutsy. But what about the fix, how do we apply the patch?

---

### Post by hansie99 on 2008-09-12
Hi, 

I have exactly the opposite problem and can't find any solutions.

Using Hardy, if I right click on the bluetooth applet and click on Browse device I can browse my Treo (Which is paired with my pc). I then can copy files from my treo to my pc. Works fine! ( I am not running bluetooth file sharing / obex-server. Since Hardy this is not necessary any more. )

But I can't send files from my pc to my mobile. I get a "This operation is not supported by the back-end" error when I try to drag & drop a file from pc to the browse window. The Send to... option gives me the same error. 

I have read somewhere that it is not yet implemented. Is this correct? 

Then I try Nautilus' send to..  but I get an "unknown error" dialog when I try to send a file. When I click on OK a new dialog appears saying that the "connection is closed" although the connections is still open according to the bluetooth-applet.

Any suggestions? Has this something to do with config options for my Palm treo? Treo to other mobile sending/receiving does work (no pairing). 

Any help is greatly appreciated.

---

### Post by cszikszoy on 2008-09-12
> **hansie99 said:**
> I have exactly the opposite problem and can't find any solutions.

You don't have exactly the opposite problem.  Reread the entire thread.  You are having exactly the **same** problem that we are all having.

---

### Post by fragos on 2008-09-12
> **hansie99 said:**
> Hi, 

I have exactly the opposite problem and can't find any solutions.

Using Hardy, if I right click on the bluetooth applet and click on Browse device I can browse my Treo (Which is paired with my pc). I then can copy files from my treo to my pc. Works fine! ( I am not running bluetooth file sharing / obex-server. Since Hardy this is not necessary any more. )

But I can't send files from my pc to my mobile. I get a "This operation is not supported by the back-end" error when I try to drag & drop a file from pc to the browse window. The Send to... option gives me the same error. 

I have read somewhere that it is not yet implemented. Is this correct? 

Then I try Nautilus' send to..  but I get an "unknown error" dialog when I try to send a file. When I click on OK a new dialog appears saying that the "connection is closed" although the connections is still open according to the bluetooth-applet.

Any suggestions? Has this something to do with config options for my Palm treo? Treo to other mobile sending/receiving does work (no pairing). 

Any help is greatly appreciated.

I run the bits you claim aren't necessary and my Nokia N810 both sends and receives files via bluetooth. My Palm E2 which I no longer use could receive via bluetooth but send to PC never worked.

---

### Post by hansie99 on 2008-09-13
> **cszikszoy said:**
> You don't have exactly the opposite problem.  Reread the entire thread.  You are having exactly the **same** problem that we are all having.

You are right! I have misread... sorry. I felt like I had an opposite problem because I thought that everyone here *could* send files from pc to bluetooth device, but *not* receive them. I realise now I have indeed the same problem... 

But what about the error I get when using Nautilus right click > Send to..?  For some people that seems as a working alternative, but not for me. Can I conclude that its not the same error as the "not supported by the back-end" error? Meaning, they are two different (but highly related) problems?

Anyone any ideas? Thanks!

---

### Post by cszikszoy on 2008-09-13
> **hansie99 said:**
> Can I conclude that its not the same error as the "not supported by the back-end" error?

Yes, this appears to be a separate issue you are having.  Using nautilus to send files to my mobile works fine.  Perhaps do some looking around, and if you can't find anything similar, file a bug report in launchpad.

---

### Post by flowbot on 2008-09-13
Um, has anyone filed a bug on this? Might be an idea to link to it in the thread. I'm having the same problem on my s60 3rd edition phone ... is there a workaround that doesn't involve adding the gutsy repos?

---

### Post by hansie99 on 2008-09-14
> **flowbot said:**
> Um, has anyone filed a bug on this? Might be an idea to link to it in the thread. I'm having the same problem on my s60 3rd edition phone ... is there a workaround that doesn't involve adding the gutsy repos?


[https://bugs.launchpad.net/ubuntu/+source/obex-data-server/+bug/222695](https://bugs.launchpad.net/ubuntu/+source/obex-data-server/+bug/222695)

---

### Post by lagosmike on 2008-09-17
Hi all

I had the same problem. Sending a file from laptop to cell phone is ok, but sending a file from cell phone to laptop don't work.

I downgraded bluez-utils, bluez-audio and bluetooth to ver. 3.24 and wow.. it works.

I will check out the patch for 3.26 next week.

Cheers lagosmike

Ubuntu-EEE 8.04.1 Netbook remix on a Asus eeePc 900A (great..)
Nokia 6630

---

### Post by majdi on 2008-09-18
I'm a Fedora user and I searched the Fedora forum for a solution to this problem but with no luck. I saw Fedora users having the same problem though.

I can scan just fine with hcitool and it detects my phone, its showing up as running in service and my laptop can connect and send files through the GUI (Bluetooth Applet 0.26) just fine.

The problem is when I try to send files from the phone, it detects my laptop but when sending the file I get a (Sending Failed). I use a Nokia E71.

I tried disabling both selinux and the firewall just to make sure its not blocking the files being sent from my phone, I get the same result, the message on my phone says sending failed.

Same problem testing this from another phone, any idea what could be causing this or how to get it to work?

I had the following installed;
Quote:
List of suspect packages
bluez-libs-3.32-1.fc9.i386
bluez-gnome-0.26-1.fc9.i386
bluez-utils-3.32-1.fc9.i386
bluez-utils-cups-3.32-1.fc9.i386
bluez-utils-alsa-3.32-1.fc9.i386


I uninstalled the following;
Quote:
bluez-libs-3.32-1.fc9.i386
bluez-utils-3.32-1.fc9.i386


And Installed the newer versions;
Quote:
bluez-libs-3.35-1.fc9.i386
bluez-utils-3.35-3.fc9.i386


After all this, I still have the same problem? Any idea?
___________________________
Fedora 9 (Sulphur)

Kernel Linux 2.6.25-11-97.fc9.i686
GNOME 2.22.1

Dell Latitude D630
Memory: 3 GB
Intel(R) Core(TM) Duo CPU T7500 @ 2.20GHz

---

### Post by majdi on 2008-09-20
Can we get a close on this? Dose bluez-utils-3.32-1 have a bug, or is something else going on here?

---

### Post by fragos on 2008-09-20
I'm running Ubuntu 8.04 and Bluez-utils 3.26-0ubuntu8. My Nokia N810 can both send and recieve with Ubuntu.

---

### Post by chuuk on 2008-09-26
Having the same problem. Any solution found yet?

---

### Post by fragos on 2008-09-26
If your talking about a cell phone with this problem don't forget that this may have nothing to do with Ubuntu. Carriers limit and restrict the features on phones they provide. As well as send and receive, my N810 recognizes the Ubuntu home folder as a networked file system that is accessable from all applications on the N810. The N810 has Bluetooth 2.0 but I don't know how that may impact availble functionality.

---

### Post by PhilJ on 2008-10-01
Nokia phone that did work under gutsy now under hardy doesnt.  I CANNOT send a file from the phone to my pc  'no device sending failed'  I CAN acess the phone from my pc using Nautilus  but cannot view the images all I get is the ubuntu gif in place of the images in the folder  I CAN send a file to the phone using Nautilus  
Philj 
doh!!  can now see images on phone.
Preview turned off in Nautilus  [IMG]file:///tmp/moz-screenshot.jpg[/IMG]:oops:

---

### Post by pjalegria on 2009-03-03
Well, its seams that problem is not solved with Interpid...
Does any one have solution to that problem?

Thanks

---

### Post by em4mapson on 2009-03-15
> **pjalegria said:**
> Well, its seams that problem is not solved with Interpid...
Does any one have solution to that problem?

Thanks

I am running Intrepid and for me it is working just fine, you just need to:
/1/ install gnome-bluetooth (from the Repos)
/2/ run from command line: gnome-obex-server
OR
Applications > Accessories > Bluetooth File Sharing

---

### Post by espmartin on 2009-03-17
em4mapson, I did this, but still not working...

---

### Post by em4mapson on 2009-03-18
> **espmartin said:**
> em4mapson, I did this, but still not working...

Unfortunately, I do not have a direct answer for you -- my two cents are as follows:
Is it only the "receive files from device to ubuntu" part not working? (As some have said above, previously in Gutsy everything else was working just fine for me, only the from dev to Gutsy was non-functional.) 

-Can you "set up new device" and then see it at "Known devices"?
-How about "Browse files on device" (same thing as typing MAC address to location in nautilus like obex://[AA:BB:CC:DD:00:11]/)?
-And finally, send files to device?

If these are not working either, there is most likely a problem with the permission set on the device etc. (or some required 'bluez...' etc package not installed)

If you are able to do all of these, the 'feature' from the Gutsy is still haunting you...
Could the possible error message(s) help you if run the gnome-obex-server from the command line?
Then just a guess -- a bit far fetched one -- remove and then re-install all bluetooth related packages.

---

### Post by charlesopondo on 2009-11-08
I use KDE on Karmic. I had the same problem; installing gnome-user-share fixed it:

```
sudo apt-get install gnome-user-share
```

---

### Post by fragos on 2009-11-08
> **charlesopondo said:**
> I use KDE on Karmic. I had the same problem; installing gnome-user-share fixed it:

```
sudo apt-get install gnome-user-share
```

I'll bet they just renamed the obex server package. In Intrepid they referred to it as "Bluetooth File Sharing" in Add/Remove but the installed packages About name was still gnome-obex-server. I fixed my Bluetooth issues in Karmic by installing blueman which replaces the Gnome Bluetooth manager and installs the obex server from the blueman PPA as part of the package.

---

### Post by em4mapson on 2009-11-09
> **fragos said:**
> I'll bet they just renamed the obex server package...

Previously, some have used gnome-obex-server and/or
gnome-user-share to make it work.
[https://bugs.launchpad.net/ubuntu/hardy/+source/obex-data-server/+bug/211252?comments=all](https://bugs.launchpad.net/ubuntu/hardy/+source/obex-data-server/+bug/211252?comments=all)

As stated in #8 in
[https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/92995](https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/92995)
"gnome-bluetooth file reception has moved in gnome-user-share
application." Consequently, gnome-obex-server is gone in Karmic
(in Jaunty it was included in gnome-bluetooth package).

Biggest problem is that there is not a one 'simple' package,
which would install everything and magically make it work (e.g.,
gnome-bluetooth could require package gnome-user-share).

In the end, all that mater is how to make it work, right? Simple way:
In Karmic it should work by installing gnome-bluetooth along with all
recommended and suggested packages (which installs also gnome-user-share)...
...not using Karmic so I am not personally able test it, but charlesopondo in #50 said it works that way.

---

### Post by Uthanos on 2009-12-16
I finally figured it out!  I installed gnome-user-share.  Then I changed the options in System > Preferences > Personal File Sharing, in the Bluetooth section. I turned on "Receive files in Downloads folder" and "Notify about received files."

However, trying to Browse files on device still doesn't work.

---

