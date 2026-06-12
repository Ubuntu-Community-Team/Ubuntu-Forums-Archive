---
title: "Weird Bug With Photoshop"
date: 2007-08-14
forum: General Help
---

### Post by fppl on 2007-08-14
Hey, I got the latest version of Wine installed and I'm trying to run Photoshop.

However I get a weird bug when I try to do so...

I type in the terminal

wine "C:\Program Files\Photoshop\Portable_Photoshop.exe"

and then it appears that PS loads up very fast and then after the intro screen (loading etc) is complete I get a message:

[[IMG]http://www.images.winupload.org/1187095037-Untitled.jpg[/IMG]](http://www.winupload.org/)

And when I look in the terminal it says:

[[IMG]http://www.images.winupload.org/1187095147-Untitled2.jpg[/IMG]](http://www.winupload.org/)

I've seen a lot of people run Photoshop on Ubuntu and since Photoshop is like 80% of my computer experience I really have to get it up and running, and I'd ***hate*** to go back to Windows...!

Please save me!

---

### Post by renzokuken on 2007-08-14
did you install Photoshop through wine?

the error suggests you do not have permission to write to registry. if this is the case the sudo command is required, but your shouldnt have to do that......

---

### Post by DKnight on 2007-08-14
Try
```
sudo chown -R yourusernamehere ~/.wine
```
in a terminal.

---

### Post by fppl on 2007-08-14
Alright I changed the permissions. Though, now it freezes on "Initializing suites..." on the intro screen. Weird thing is when I click CTRL+C it continues to load, but then it gives me non-stopping messages on the terminal and the program gets stuck... Anyone know of a fix for that?

---

### Post by fppl on 2007-08-14
When I force quit terminal says

err:shell:HCR_GetFolderAttributes HCR_GetFolderAttributes should be called for simple PIDL's only!
err:shell:HCR_GetFolderAttributes HCR_GetFolderAttributes should be called for simple PIDL's only!
err:shell:HCR_GetFolderAttributes HCR_GetFolderAttributes should be called for simple PIDL's only!
err:shell:HCR_GetFolderAttributes HCR_GetFolderAttributes should be called for simple PIDL's only!
err:shell:HCR_GetFolderAttributes HCR_GetFolderAttributes should be called for simple PIDL's only!
fixme:keyboard:RegisterHotKey (0x20410,99,0x00000000,27): stub
fixme:keyboard:UnregisterHotKey (0x20410,99): stub
err:shell:HCR_GetFolderAttributes HCR_GetFolderAttributes should be called for simple PIDL's only!
err:shell:HCR_GetFolderAttributes HCR_GetFolderAttributes should be called for simple PIDL's only!
wineserver: could not save registry branch to /home/yam/.wine/system.reg : Permission denied
wineserver: could not save registry branch to /home/yam/.wine/userdef.reg : Permission denied
wineserver: could not save registry branch to /home/yam/.wine/user.reg : Permission denied

---

### Post by fppl on 2007-08-14
?

---

### Post by renzokuken on 2007-08-14
how did you install wine in the first place?

and then how did you install photoshop?

---

### Post by fppl on 2007-08-14
I installed wine via Synaptic and Photoshop is a portable edition... I just downloaded it and need to run the exe - runs fine on windows.

---

### Post by fppl on 2007-08-14
? Maybe I should reinstall wine somehow?

---

### Post by fppl on 2007-08-14
?

---

### Post by fppl on 2007-08-14
Since someone asked me and I replied can I get some more help...? :) This is REALLY REALLY important to me... I don't want to have to run damn Windows just to get one program running...

---

### Post by fppl on 2007-08-14
...

---

### Post by renzokuken on 2007-08-15
once you installed wine, did you run

```
winecfg
```

???

you have to run that command to set basic parameters before wine can be used

---

### Post by fppl on 2007-08-15
What do I have to change there? Until now I only set it on Win XP but that's all I changed there.

Should I do more there?

---

### Post by fppl on 2007-08-15
I just reinstalled wine and configured it without sudo so I can have the permissions with my normal users.

When I run photoshop it still gets stuck on the Initializing Suites and when I click CTRL+C it continues, only to crash at the tips screen.

Terminal:
fixme:keyboard:UnregisterHotKey (0x10024,99): stub
err:shell:HCR_GetFolderAttributes HCR_GetFolderAttributes should be called for simple PIDL's only!
err:shell:HCR_GetFolderAttributes HCR_GetFolderAttributes should be called for simple PIDL's only!
fixme:keyboard:RegisterHotKey (0x10024,99,0x00000000,27): stub
fixme:keyboard:UnregisterHotKey (0x10024,99): stub
fixme:keyboard:RegisterHotKey (0x10024,99,0x00000000,27): stub
fixme:keyboard:UnregisterHotKey (0x10024,99): stub
fixme:keyboard:RegisterHotKey (0x10024,99,0x00000000,27): stub
fixme:keyboard:UnregisterHotKey (0x10024,99): stub
fixme:keyboard:RegisterHotKey (0x10024,99,0x00000000,27): stub
fixme:keyboard:UnregisterHotKey (0x10024,99): stub
fixme:keyboard:RegisterHotKey (0x10024,99,0x00000000,27): stub
fixme:keyboard:UnregisterHotKey (0x10024,99): stub
fixme:keyboard:RegisterHotKey (0x10024,99,0x00000000,27): stub
fixme:keyboard:UnregisterHotKey (0x10024,99): stub
fixme:keyboard:RegisterHotKey (0x10024,99,0x00000000,27): stub
fixme:keyboard:UnregisterHotKey (0x10024,99): stub
fixme:keyboard:RegisterHotKey (0x10024,99,0x00000000,27): stub
fixme:keyboard:UnregisterHotKey (0x10024,99): stub
err:ntdll:RtlpWaitForCriticalSection section 0x1505760 "?" wait timed out in thread 000b, blocked by 0011, retrying (60 sec)

---

### Post by renzokuken on 2007-08-15
> **fppl said:**
> What do I have to change there? Until now I only set it on Win XP but that's all I changed there.

Should I do more there?

no, just running it does all the configuring. you could also try it in win200 or win98 mode. sometimes that makes a difference.

what is the exact version of photoshop you are trying to install?

---

### Post by fppl on 2007-08-15
I'm trying CS2 and CS. They are already installed, I'm just trying to run them up. (Copied their dirs from windows and their reg entries to wine regedit)

---

### Post by renzokuken on 2007-08-15
i think there are other steps involved if you copy a directory across. it is usually better just to do a clean install directly through wine

---

### Post by bogolisk on 2007-08-15
My test results with wine from winehq (and not the ubuntu package):
[LIST]
[*] wine 0.9.41: Photoshop CS2 works (tested lightly, because I'm a gimper not photoshopist)
[*] wine 0.9.42: CS2 started but many buttons don't work. Menu is ok.
[*] wine 0.9.43: CS2 started but many buttons don't work. Menu is ok.
[/LIST]

This was done with a portable version.

YMMV

---

### Post by fppl on 2007-08-15
Thanks I will test with wine 0.9.41 and post back.

---

### Post by bogolisk on 2007-08-15
The easiest way to launch photoshop is:
[LIST]
[*]to transform your Photoshop into a portable version (or download a portable version providing you have a legal license.)
[*]start photoshop like this:
```

wine explorer /desktop=Photoshop_CS2,1200x900 PhotoshopPortable.exe

```
[*]for make a shell script (e.g. photoshop.sh) containing
```

dir=`dirname $0`
cd ${dir} && wine explorer /desktop=Photoshop_CS2,1200x900 PhotoshopPortable.exe 2>&1 > /dev/null

```
and put it in the same directory as PhotoshopPortable.exe file. Create a launcher with that shell script as the command.
[/LIST]

---

### Post by fppl on 2007-08-15
Ok I tested still no change... It still gets stuck. (Although now it shows a new error in the terminal because clicking the CTRL+C.

fixme:actctx:QueryActCtxW 80000010 0x4112390 (nil) 1 0x34e3d0 8 (nil)

You know, I'd use the GIMP... It's just not 1/100 as strong as Photoshop and I do graphics for a living. That's why I'm tight on running PS. ;)

---

### Post by fppl on 2007-08-15
Oh and I tried your shell script, it loaded a blank wine screen with the title Wine Desktop

---

### Post by bogolisk on 2007-08-15
Try to get a "Portable" edition. It's **much** easier to deal with.

---

### Post by fppl on 2007-08-15
I am using a portable edition (but also tried on a non portable)

---

### Post by fppl on 2007-08-15
Hey, I just read that there's this thing called VMware which lets you run Windows actually on your LInux desktop, without rebooting/etc... So yeah, I will have to install Windows for it but it's definitely worth it!

Do you think it's a good idea to do it? And **will it** run Photoshop fine?

Thanks! XD

---

### Post by fppl on 2007-08-15
Eh? :)

---

### Post by fppl on 2007-08-15
..?

---

### Post by fppl on 2007-08-15
Ok I'm going desperate here... It just looks like everything has to go wrong no matter what I try.

I tried wine's 3 latest releases.. .Didn't work. I try installing vmware-server... Error in package. I tried installing vmware-player via Synaptic - error in package... I don't know what to do anymore.

---

### Post by Shay Stephens on 2007-08-16
I am a photographer and CS2 just isn't supported yet for wine.  The only version that works really well is PS7.  I am using PS7 for my various image editing needs that require text layout.  I am also using Bibble Pro for my RAW editing needs.

I have heard people say they have CS2 running, but I have seen no proof of that actually taking place in a way that would support production, nor have I been able to get it working.

---

### Post by fppl on 2007-08-16
Well I am now running Photoshop CS2, Visual Studio 2005... Internet Explorer (yuck) all in Linux. :)

---

### Post by bogolisk on 2007-08-16
> **fppl said:**
> Hey, I just read that there's this thing called VMware which lets you run Windows actually on your LInux desktop, without rebooting/etc... So yeah, I will have to install Windows for it but it's definitely worth it!

Do you think it's a good idea to do it? And **will it** run Photoshop fine?

Thanks! XD

It will run Photoshop perfectly but *slow*! Wine emulates the win32 ABI, VMWare emulates the x86 machine.

Sorry to hear that you have troubles getting CS2 up. All I needed to do was:
[list]
[*] download (from the net) 2 dlls, msvcp71.dll and msvcr71.dll, 
[*] put them in the same directory as PhotoshopPortable.exe
[*] start PhotoshopPortable.exe inside a wine desktop, i.e.:
```

wine /desktop=CS2,1200x800 PhotoshopPortable.exe

```
[/list]

That's all! wine 0.9.41 works, 0.9.42 and 0.9.43 are buggy!

---

### Post by bogolisk on 2007-08-16
> **Shay Stephens said:**
> I am a photographer and CS2 just isn't supported yet for wine.  The only version that works really well is PS7.  I am using PS7 for my various image editing needs that require text layout.  I am also using Bibble Pro for my RAW editing needs.


How about starting a "Ubuntu and photography" thread so we can share our experiences, hints and tips using Ubuntu for digital photography (post-processing, denoising, sharpening, printing, etc.) I've never done any text manip in gimp but I've heard that gimp-2.3.x has greatly improved the text tool.

> 
I have heard people say they have CS2 running, but I have seen no proof of that actually taking place in a way that would support production, nor have I been able to get it working.

It's true that I use CS2 very little. I only use it to:
[list]
[*] run 8li plug-ins (like PhotoKit Sharpener). For 8bf plug-ins, I use Irfanview, because it's lighter and faster to start than CS2. I've yet managed to get Elements to run in wine (mainly becase the lack of a portable edition.)
[*] when I *really* need shadow-highlight recovery and couldn't get the job done with curves or filter-pack in gimp.
[/list]

Cheers

---

### Post by fppl on 2007-08-16
Actually everything runs really really fast.

---

### Post by fppl on 2007-08-16
I have a very strong machine, though. (Intel Core2Duo E6600, 2GB 800mhz Dual, 16mb SATA II, Radeon 2900XT - ER no drivers for linux but it's a beast)

---

