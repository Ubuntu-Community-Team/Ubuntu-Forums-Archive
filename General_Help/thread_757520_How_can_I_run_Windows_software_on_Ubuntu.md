---
title: "How can I run Windows software on Ubuntu?"
date: 2008-04-17
forum: General Help
---

### Post by YMS_1975 on 2008-04-17
Before I get blasted....YES, I have searched (and read) the previous posts on this topic, but  I do require some more clarification and some specifics.

I have a TomTom GO920(T) GPS unit.  There was [another post about this]("http://ubuntuforums.org/showthread.php?t=644657&highlight=TomTom") however it wasn't very helpful, so I'm posting this.
TomTom utilizes a Windows oriented program called "[COLOR="Red"]TomTom Home[/COLOR]." TomTom Home will allow me to connect my GPS unit to my PC via a USB cradle.

Long story short, from what I can make it is possible to run this software however WINE is not the best option since it's more geared towards older MS applications. This is definitely a newer application (Vista).

My other option as I understand it, is a software called "VMWARE". Unless I'm mistaken, utilizing VMWARE, I'd have to install both VMWARE & a copy of MS VISTA. _Please correct me if I'm wrong._ The upside to VMWARE is that I'd be able to run multiple OS's/applications without having to partition and/or format my drive. The downside is the fact that I'm taking up valuable hard drive space for only one program.

Is there any way for me to run an MS program without installing a virtual machine? If not, is there a Ubuntu (Linux) oriented program that is KNOWN to work with TomTom products?
I am not opposed to using software other than TomTom Home, as long as it works.

Any thoughts?    =D>

---

### Post by Tews on 2008-04-17
While going the VM route would probably a solution, I'd recommend setting up a dual boot configuration for the time being.

---

### Post by ryanhaigh on 2008-04-17
Because you need the windows program to communicate witht the hardware (usb) it is very unlikely that wine will  be any good to you. Using vmware(never personally used for usb access)/virtualbox (puel licensed version from their website has usb support) or qemu (again no idea if it can connect to usb) is probably your best bet besides dual booting. I assume that this application would run under windows XP, if so it would probably be better to use that as it uses less disk space and is generally less demanding.

---

### Post by nicedude on 2008-04-17
I googled around for a minute and it looks like there are no Linux based softwares that would replace your tomtom home software, also I saw someone saying they couldn't get their 920t to work with wine (windows emulator). I think you might be left having to use the virtual machine method for the moment. You don't have to use Vista VM though you could instead use a virtual XP machine, it might save you a little bit of space over the Vista and should be a bit faster since there is less bloat and DRM in XP. 

I did see these links that should be of interest to you, the first is a tomtom fan page with lots of info about different tomtom modding stuff & tricks. The second is for a laugh as its a story from last year where tomtom 910's were shipped out with a virus preinstalled, funny part was they mention that since the tomtom runs linux itself it was immune but when you connected it to a Windows PC it would be infected. Maybe the virtual machine isn't a bad way to go after all :-)

[http://www.opentom.org/](http://www.opentom.org/)
[http://www.gpsmagazine.com/2007/01/tomtoms_910_ships_with_virus.php](http://www.gpsmagazine.com/2007/01/tomtoms_910_ships_with_virus.php)

---

### Post by YMS_1975 on 2008-04-18
Well,

I received a response from TomTom's technical support department today. They advised that Linux is NOT supported & that there was no way to update my GPS unit without connecting it to my PC via the USB cradle. But there is an option on one of the menu's of my GPS unit to update it however it has to utilize my cellphone's connection but I just can't seem to get that to work. The update(s) I'm referring to is : 1) GPS QuickFix and 2) Downloading Map Corrections. 

Both options appear on the GPS's menu. To update the GPS unit via the PC/USB cradle you do not access these updates via those menu's. It's done via the software (TomTom HOME).  So either TomTom rep's don't know what they're talking about or I'm confused on something here. 

Judging by the looks of this situation the only way I can go is to either dual boot or set up VMWARE. Either way....a Windows OS has to be on my hard drive.  :(

I'm sick of Windows & have been for quite some time; I really am. It's too costly, it's a resource hog & is always crashing. I've gone back and forth between Ubuntu & Windows and to be honest...the only reason I've switched back to Windows each time was because I had an application that needed Windows (I.E: My GPS unit).

This time I've resolved not to crack under the pressure. Ubuntu is the greatest thing since sliced bread. I'm so happy with it. Load times (bootup and application launch) are blazing fast and hello?! It's free! :guitar:

Long live Ubuntu! Bring on 8.04!

---

