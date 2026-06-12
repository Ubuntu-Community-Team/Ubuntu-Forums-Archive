---
title: "Yet Another Wine Question"
date: 2007-01-18
forum: General Help
---

### Post by drs305 on 2007-01-18
I am new to Linux and am trying to get a specific windows program to run (bestpractice - an audio program with variable speed capabilities). I have installed Wine and rut the apps setup program through Wine (successfully, I think) and it has placed files in:

/home/test/.wine/drive_c/program files/BestPractice/   the file I want to run is bp.exe

I don't have any PATH statements. The original program is in my C drive.If I type:  wine "C:\Program Files\Best Practice\bp.exe"  I get the following result after about 15 seconds:

libGL warning: 3D driver claims to not suport visual 0x4b
err:module:LdrInitializeThunk "AKRIP32.DLL" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L "C:\\Program Files\\BestPractice\\bp.exe" failed, status c0000142

AKRIP32.DLL is located within the BestPractice folder.

Am I using the wrong command, need something else installed, or will this app simply not run with Wine?

Thanks for your help.

---

### Post by zanglang on 2007-01-18
Odd, I tried downloading the program from Sourceforge and installing it, started without any problems at all. (Although the sound tweaking didn't work... either unimplemented Wine features or sound driver configuration) Try upgrading to the latest Wine (0.9-29)? YMMV.

On the other hand I think you'll be able to find a native Linux app with similar functionality if you check the repositories. ;)

---

### Post by graigsmith on 2007-01-18
put that akrip32.dll file in the windows system 32 folder under .wine/drive_c/windows/system32/

then run winecfg, and override that dll. just type the name of the dll in.

then try it.

---

### Post by drs305 on 2007-01-18
zanglang, I suspect I don't have Wine installed properly. Even with all the threads about it I don't think I found a reference that told a complete idiot how to install it :(  . I have looked at several Linux apps but most don't have the speed slider I am looking for.  You said you got BestPractice to partially work - can you speed up the playback? That is what I want it for. If you can't (and since you know how to use Wine) then I guess I don't need to pursue it.

graigsmith, I tried what you suggested but get the same message. I suspect it's related to my Wine installation (see above).

Thank you both for your help.

Later:  I just installed and ran another windows app successfully so perhaps I installed Wine correctly after all (at least partially).
And is there something I can install to prevent the "libGL warning: 3D driver claims to not support visual 0x4b" ?  I get that a lot.

---

### Post by zanglang on 2007-01-18
Follow the instructions here to set up WineHQ's apt repository:
[http://winehq.org/site/download-deb](http://winehq.org/site/download-deb)
then apt-get update and upgrade wine. ;)

And no, the controls didn't work for me, probably either because my Wine audio settings wasn't set properly or the functions weren't supported. Anyway, try Audacity (which is pretty powerful), or Jokosher (which i've not personally tried, but seems to be quite awesome) on the repositories. ;)

---

