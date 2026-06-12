---
title: "Ubuntu with GPS / Base Camp / Viking / Wine?"
date: 2015-03-16
forum: General Help
---

### Post by arnicainthemembrane on 2015-03-16
Hi, I'm bike touring Europe with my Asus Eeepc running Ubuntu 14.04 and a Garmin Etrex 30 GPS.

I'm accustomed to using my GPS with Garmin BaseCamp on a Win7 machine. 

Thus far I have been able to use  Viking to upload and download tracks to/from the GPS and OSM cycle map, but I can't upload waypoints to the GPS, also Viking can't download the entire OSM cycle map (useful as I am frequently offline). 

So I would like to try to use an emulator such as Wine to run Garmin Base Camp, which has the functions of uploading waypoints to the GPS and can hold the whole OSM fietsmap in its memory.

Any advice? Workarounds? Issues? Suggestions for other apps which might do the same thing without having to use an emulator?

Thanks!

eddie

---

### Post by Mark Phelps on 2015-03-16
> without having to use an emulator?FYI ... Wine is NOT an emulator, if that is what you were thinking.  Wine is a hack in which some Windows DLL files were rewritten to replace Windows OS kernel calls with Linux OS kernel calls.  To the degree that a Windows app uses on these replaced DLLs, the app works well -- but in recent years, Windows apps have shifted over to using different middleware and some apps even use their own custom DLLs, and in those cases the apps work poorly or not at all.

---

### Post by arnicainthemembrane on 2015-03-16
I will gladly use an emulator, can you suggest a good one? I just need to run Garmin Base Camp... hopefully with full functionality.

---

### Post by ian-weisser on 2015-03-16
There is no 'Windows emulator.' Windows is a full-featured, closed-source, wholly proprietary, commercial operating system. Anyone creating an 'emulator' would be promptly sued by the owner.
Linux is not a free clone of Windows. It's something quite different.

You are asking how to use a Windows application that uses Windows-specific system calls and Windows-specific features on a non-Windows system. [It might work, it might not]("https://appdb.winehq.org/objectManager.php?sClass=version&iId=27222"). 
Rather like going into an ice cream store and asking for their seafood menu. They are both food, and you might get lucky. 

Basecamp is explicitly Windows and Mac only.

If you wish to use Linux, then you should:
1) Complain to Garmin for their lack of Linux support.
2) Ask "what Linux applications have comparable features and are compatible with my GPS?"

---

### Post by QIII on 2015-03-16
... or run Windows in a virtual machine such as VirtualBox.

Be aware that using an OEM disk to install Windows in a VM would likely be a violation of the EULAs of both the OEM and Microsoft - assuming it would even work.

You can certainly use a retail version to install in a virtual machine, but remember that the Windows EULA allows you to only install it on one machine.  You can't use the same media that has been used on a physical machine to install on a VM.

---

### Post by arnicainthemembrane on 2015-03-16
From what I can tell there aren't any Linux (specifically Ubuntu 14.04 LTS) compatible mapping applications which are capable of:

1. working with the Garmin Etrex 30 GPS
2. loading whole  OSM "cycle" maps on my hard drive and accessing them when I'm not online
3. transferring waypoints to and from the GPS

Having had quite a bit of luck with Garmin Base Camp, I'm trying to find some way to use it with a Linux machine. I've heard there are ways to make use of applications which are designed to work with Windows, by emulators or virtualbox or Wine or whatever.

I have no interest in pirating anything, or illegally emulating anything, or doing anything sketchy or illegal here, I'm just curious as per how I might find a way to use Base Camp on this machine. If it's impossible i can accept that as well.

So... if anyone would like to give me advice on the matter, shoot some URLs my way & in any way constructively explain the situation so's I might be able to attain my goals, I really appreciate it. 

Everyone else... I'd rather not hear from.

thanks.

---

### Post by QIII on 2015-03-16
Again:

1.  You may try to use Wine, but you will have to consult the app database at winehq to see if it will work.

2.  You may use Windows in a virtual machine.

Those are pretty much your choices for running applications designed for Windows on a Linux box.

That is about the only constructive advice available.

---

### Post by ian-weisser on 2015-03-16
A quick search of this forum turned up [this thread about eTrex 30]("http://ubuntuforums.org/showthread.php?t=2059248") that seemed to turn out happily.

---

### Post by arnicainthemembrane on 2015-04-15
Hey, thanks for the advice, I am attempting to run win7 on virtual box. Another idea is to run Map Source (similar to basecamp) on Play on Linux, as suggested on this forum, a little ways down the thread: [http://www.4x4community.co.za/forum/showthread.php?t=132856](http://www.4x4community.co.za/forum/showthread.php?t=132856)

See what happens...:p

---

### Post by filipe-110 on 2016-03-08
With QLandKartGT or QMapShack you can do it all.
QLandKartGt is avaliable on software center

---

### Post by QIII on 2016-03-08
The OP has not been back to this in nearly a year.

RIP.

---

