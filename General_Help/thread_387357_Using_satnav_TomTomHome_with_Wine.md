---
title: "Using satnav TomTomHome with Wine"
date: 2007-03-18
forum: General Help
---

### Post by Handssolow on 2007-03-18
Just wanted to share how I got TomTom HOME running under Wine. Initially I used the CD that came with my new satnav but although it ran under Wine I couldn't get the TT Home update nor any satnav updates. A Google search suggested that othere had found this. Next I downloaded and installed the latest TomTom Home (V1.5 Build 104 March ) from my Ubuntu desktop and was able download satnav updates but rather messed up my Applications>Wine>TomTom Home menu because of my previous install of the older software. I went for a fresh install.

After removing Wine but  I couldn't clean up the Application Menu using System>Preferences>Menu Layout with a delete. A Forum member suggested right click on Application>Edit Menus and this worked after a reboot. I was then able to delete and clean up the menu and reinstall Wine and then TomTom Home with
wine /home/Handssolow/Desktop/TomTomHOMEwinlatest.exe.

I wanted to launch TT Home from Applications Menu>Internet I found a TomTom icon which I'd saved from my original CD install but had to use gksudo natilus to move it to where the other icons are kept. The command I used to launch TomTom Home was
wine "/home/Handssolow/.wine/drive_c/Program Files/TomTom HOME/TomTomHOME.exe"


However the application was running in a small window. Forum searches and lots of my changes to winecfg  didn't help me. I realised that my problem was more about the window that wine was running in than the window the TomTom Home application was running in. In winecfg Applications tab I removed the application, selected Graphics,Emulate Virtual desktop and in my case 1023 x 768 size. Using winecfg then I added the TomTom Home application and was able to stretch the windows to fill my monitor screen.

It's early days but it seems to be working.

---

### Post by Handssolow on 2007-03-22
I felt I had to add that TomTom Home running under Wine, downloads updates satisfactorily.
However, it is then awkward to upload these updates to my TomTom 910 satnav. 

This is explained further [ Here](http://www.winehq.com/pipermail/wine-users/2007-January/024338.html)

Apparently there's no support for Linux with TomTom HOME despite the satnav running under Linux. TomTom haven't replied to my email when I told them I used a Linux based system.

If we Linux and Ubuntu user don't make a noise then they'll think everyone uses windoze or a fruit based PC. I think I'll send them a few more emails until they reply and support Linux users.

---

### Post by Handssolow on 2007-08-11
I've made no progress using Ubuntu to update my TomTom 910 using TomTom Home running under Wine, if anything things are worse with Feisty. Yes I'm able to connect online to the TomTom website but  I'm unable to download any updates now. As soon as I start to download my updates almost immediately I get this error message-

This file does not exist
c:\windows\temp\xxxxxxxxx\Ephemeris.cab

Has anyone any ideas?

Updating my TomTom satnav and also the lack of webcam video feature with Linux Skype remain the only two remaining reasons I'm having to keep Windoze.

---

### Post by hoogland on 2007-12-08
The way to solve this is to find the *.cab and *.toc files  that are downloaded in the windows\temp directory and move them to the directory 

~/TomTom/HOME/Downloads/ (where ~ represent your user directory, i.e. /home/your_user_name/)

Then open the *.toc file (XML) in a text editor and change the cab file location to represent the updated location.

<Location>file://z:\home\your_user_name\TomTom\HOME\Downloads\Ephemeris.cab</Location>

Now go into TomTom Home running under Wine, go to the Manage your TomTom section, click on Install to TomTom, Select My Computer. There you'll find the local file with the updated satellite information that you can upload to the hardware without problems.

It is round about, but it works...
:)

---

### Post by Handssolow on 2007-12-08
I'm no longer able to get TomTom Home to run under Wine for reasons which are unclear. I was at least able to get it to run before I ungraded my PC to a dual core cpu and switched to an onboard soundchip and unplugged a Creative Audigy card.  I seem able to go through the install process with the supplied CD or instead using the latest version of the Home program available off the website. Either way they appear under Applications>Wine>Programs but when I select TomTom Home, it appears on the lower toolbar for about 15 seconds but then disappears and in the end  nothing loads.

I tried also with my wife's PC which has only one cpu but got the same results and I made no progress here either. At one stage I was hopeful when installing from the CD it downloaded the latest version but I was still unable to launch any Home program from any source.

Any suggestions?

---

### Post by Handssolow on 2007-12-09
hoogland, how did you install TomTom Home with Wine, which version and how do you launch your TomTom Home application? After various installs mine appeared under Applications>Wine sometimes Applications>Other and earlier when I had Feisty, under Applications>Internet.

Today I eventually got TomTom Home running under Wine but with too many bugs, regrettably I'll have to continue to use windoze to update my satnav - my last essential need for a msoft product. I can download updates for the Home program which don't install and also  download satnav data updates. There are several messages about missing files during these processes though at one stage I did manage to download over 100 .cab and .toc files to /home/Handssolow/TomTom/HOME/Downloads. Also no Ephemeris file seems to be created. I wouldn't want to have to manually edit large numbers of files every time I download an update from their website.
I'm now going to have to boot up XP.

---

### Post by Keith_Beef on 2007-12-25
My wife gave me a GO 920 for Christmas... I wish I could get this to work with Linux.

My attempts at running the bundled Windows software with Wine came to naught. I installed Wine, and a Wine entry appeared in my Applications menu. I ran wine config from the menu, tested sound, checked the default drive settings; I thought things were set up correctly. But when I run autoplay.exe or setup;exe from the CD, nothing seems to happen.

The TomTom site is unbearably slow today. (I hope it will be more responsive after the Christmas rush.) I could find absolutely no Linux support on the site.

I find it strange that this is a Linux/ARM based device, yet there seems to be no support for Linux users from the TomTom company.

On the good side, the device shows up as an external disc when I connect it through its USB cradle, but I couldn't get it to bind as a Bluetooth device (that's another story... my pitiful attempts at Bluetooth with Linux).

I poked around, and found GPL and other licenses on the device. It runs MPlayer and some sort of OGG/Vorbis software. I hoped to be able to play some of my .ogg files on it, and maybe even some videos, but the bundled JukeBox doesn't want to know.




B.

---

### Post by linux4me on 2007-12-30
I'm a new TomTom owner, too, and after reading this post, I ended up installing VirtualBox with Windoze XP as the guest OS and installing TomTom Home on it. 

After some trial and error, I got TomTom Home working and recognizing my TomTom 720. I am able to update the TomTom, which was the main goal. However, I haven't been able to use the link to "manage my deviice" which is supposed to let you use your TomTom via the PC interface in TomTom Home. I get an error message that says "navigator failed to initialise" in Windows after a long (~2 minutes) delay.

I guess I can live without being able to use the TomTom from within TomTom Home as long as I can do updates. I'm going to post to see if anyone here can offer some advice about the error...

P.S. Yes, I do feel "dirty" after installing Windoze on my Ubuntu box, even if it does run in a virtual box.

---

### Post by Handssolow on 2008-01-02
Please everyone, email TomTom to encourage them to issue TomTom Home for Linux. Any satnav manufacturer who supports the increasing number of Linux users has my vote. 
I can get TomTom Home running under Wine, explore the data on my Go 910, even download my speed camera site updates (sorry, safety updates) but then not easily upload the many updates to my TomTom. Perhaps there's only a few lines of code that need to be modified, but what a difference it would make. Come on TomTom we know you can do it.

Otherwise I still need XP, Grrrrr.

---

### Post by linux4me on 2008-01-04
Here's the response I got from TomTom after requesting that they create a version of Home for Ubuntu:
> Thank you very much for taking the time to contact TomTom Support with your suggestion for the development of software for Ubuntu Linux. We frequently use customer feedback as an initiative to add or improve our navigational and usage features. Any suggestions made regarding our equipment or software will be forwarded to our product development team for review. Please let us know if you have additional suggestions or feedback.
The more of us that ask, the better. Even if you don't *have* a TomTom, you should email them and ask them; if you ever buy a GPS, you'd want one with an Ubuntu interface, right?

---

### Post by tim71 on 2008-01-18
It seems like TomTom HOME 2 can be installed without problems (version included on CD was giving an error at the end of the installation) and it can be run without errors, but I have not found a way to get TomTom HOME to recognize the device.

I looked up the device manager on the windows machine, where I operated tomtom with TomTom HOME 2, and did not found any TomTom-specific device or driver anywhere - only related things were devices like"storage volume" and "mass storage device" using Windows own drivers.

Conclusion for now: 

1. Device can be accessed like storage volume(s) straight from Linux 
2.TomTom HOME 2 runs under wine, but the device cannot be recognized by it. 

If it would be somehow related with handling USB devices by wine, then I do not know, how somebody else have made it work. If it can be related specifically to version 2.1 of TomTom HOME, then it would be making more sense...

---

### Post by jonallport on 2008-01-21
Just to throw my hat in the ring, too!

I've just been looking around the TomTom website and found that the TomToms themselves are linux machines!!! Also, the TomTom software (as run on the units) is open source and available from tomtom.com/gpl.  

I too am anxious to get my GO510 updated under Ubuntu, Then I can relegate Mr Gates's products to the bin!

---

### Post by holdup on 2008-01-21
only the linux distro is open source.  The tomtom navigation software isnt unfortunately.

---

