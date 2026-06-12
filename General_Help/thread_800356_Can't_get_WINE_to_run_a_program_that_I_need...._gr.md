---
title: "Can't get WINE to run a program that I need.... grrr"
date: 2008-05-19
forum: General Help
---

### Post by DJSchmidty on 2008-05-19
the program is to view remote cameras at a place of business, and my dad uses it all the time to watch his place.  I want to convert him over to ubuntu, but I can't even get this program to run on my own computer.   The location of the demo program (which is actually what I really do use, I just change the IP number) is here:

[http://www.silicor.com/downloads.html](http://www.silicor.com/downloads.html)

its called:
  	

WindowVision Remote Pro (5.16)
(9.92 Mb)

when I dl it, it givesd me the option to run it with wine, and it appears to install just fine, but when I restart the computer, and run the program from applications>wine>programs>windows vision remote> , the loader (hour glass) animation appears like its loading the program, but nothing.  Nothing appears...  I try to run the notepad program that came with wine, and it works fine...

can someone clue me in?
Thnx!!

---

### Post by ibuclaw on 2008-05-19
1) This is WINE. Restarting the computer isn't necessary because there is no Operating System running! (at least, for the Windows executables)

2) Open up a terminal, "cd" to the location of the executable and type in: ```
wine winvision.exe
```
Or whatever the name of the binary is...

What is the app doing when it appears to hang?

[EDIT]
Also, please note that WINE is an emulation layer for Windows Binaries, **not Windows Drivers**. Sorry for the emphasis, but I'd thought that I'd just point that out first before finding out later. (I looked at the site and the first thing I saw was a server, so it just came to mind).

Regards
Iain

---

### Post by DJSchmidty on 2008-05-19
uhm i know i'm gonna sound like a TOTAL noob right now, so forgive me...

I can't seem to change directory "cd" into the program files folder, i guess because theres a space??

I know, I sound like such a noob, but atleast i'm willing to learn, right?

---

### Post by Zacariaz on 2008-05-19
just write:
```
cd Prog [dont press enter!]
```
and the press TAB, this should autocomplete.

Also it might be at good idea to alter the suggested wine command a bit:
```
wine ./winvision.exe
```
I don't know if the ./ is needed for you, but it is for me (I think)

---

### Post by ibuclaw on 2008-05-19
> **DJSchmidty said:**
> uhm i know i'm gonna sound like a TOTAL noob right now, so forgive me...

I can't seem to change directory "cd" into the program files folder, i guess because theres a space??

I know, I sound like such a noob, but atleast i'm willing to learn, right?

Also, BASH has build in wildcards too. (* = match any string, ? = match any char, "" = treat as one string).

So the following are legal ways of doing this too:
```
cd Program*
```
```
cd Program?Files
```
```
cd "Program Files"
```

Regards
Iain

---

### Post by DJSchmidty on 2008-05-19
```
SSSSS@SSSSS-desktop:~/.wine/drive_c/Program Files/Silicor Technologies/Window Vision Demo$ wine WinVisRemote.exe
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
wine: could not load L"C:\\windows\\system32\\WinVisRemote.exe": Module not found
SSS@SSS-desktop:~/.wine/drive_c/Program Files/Silicor Technologies/Window Vision Demo$ err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
```



Thats the error i'm getting

---

### Post by Zach_the_Lizard on 2008-05-19
Try running the following:
$ sudo sysctl -w vm.mmap_min_addr=0

After this, then cd into whatever directory the program is in and type:

$ wine name_of_program.exe

This might help. Bear in mind, however, that this command works only for the current session. That is, if you reboot, you must do it again.


This, taken from the WineHQ page, is how you make it permanent *if* executing the above command allows you to run your program.

$ sudo gedit /etc/sysctl.conf

and change the line that reads:

vm.mmap_min_addr = 65536

to:

vm.mmap_min_addr = 0

---

### Post by ibuclaw on 2008-05-19
Hmmm.... Looks like a memory failure.

First, try upgrading to the most recent WINE version from the wine site. ([instructions here.]("http://www.winehq.org/site/download-deb"))

Second, try downgrading (or upgrading) the emulation.
Type in "**winecfg**" in the terminal and change the Windows OS from "WinXP" to a different model.

[EDIT]
Also, try what Zach said. Sounds very interesting...

Though, in general. If it fails to start, there's not much that you can do really. Report a bug to the Wine Devs about the "[err]" lines and hope that they fix it promptly.

Either that, or try and find a piece of software that will do the exact same job, except that it is compiled as native binary to Linux.

Regards
Iain

---

