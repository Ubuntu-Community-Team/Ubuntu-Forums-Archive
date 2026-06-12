---
title: "WINE goes BETA!!"
date: 2005-10-25
forum: General Help
---

### Post by jecos on 2005-10-25
Go get it! installations work now on almost every win32 app.

[http://www.winehq.org/pipermail/wine-announce/2005-October/000064.html](http://www.winehq.org/pipermail/wine-announce/2005-October/000064.html)

---

### Post by Muffe on 2005-10-25
Intresting. Maybe I should install it and try it on some of my windows-only applications?

What experiences do you have with wine?

---

### Post by RayH on 2005-10-25
Darn, tried it with my baseball game but still no go :o(  It is a directx app though.  Is there a forum where troubleshooting directx games in Wine would be covered?

---

### Post by glug101 on 2005-10-25
[QUOTE=Muffe]Intresting. Maybe I should install it and try it on some of my windows-only applications?

What experiences do you have with wine?[/QUOTE]
My expereiences a couple years ago were so bad that I never tried using it again.  However, the program has great promise for those of us running linux/x86.  I'm really happy that they finally have a version number instead of those discouraging cvs builds.  Maybe I'll give it a try tonight and report back.....

---

### Post by acascianelli on 2005-10-25
Has anybody tried WINE 0.9 on Breezy yet?

---

### Post by flower on 2005-10-25
wow .. even has deb repository : 

sources.list

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/

I'm with breezy and I'm gonna install it now,
hm... 15MB and it's 2AM already ... so maybe 
tommorow I'll post some tests outcome
=============================
look at what's in the new features :  Joystick force feedback support.
would that work also for my logitech wheel ?

---

### Post by flower on 2005-10-25
hm .. here's first outcome with breezy/wine0.9

m$ excel - IOPL not enabled error
m$ word - IOPL not enabled error
m$ IE - IE needs to close now error 

:) still way to much DLLs in Win :)

anyway - I tested with some smaller programs like -
Emeditor - works good
FileZilla - way better than previous versions of Wine

they implemented also a nice gui to configure and use wine : xwine - looks really nice, but crashes every 20secs tough... 

also they have made nice feature - by default the started application sees the linux file structure ... this way you really can use it (before it was like going and editing the config files to map folders .... blah )

so... as overall ... still super buggy, but you can see super progress

---

### Post by MetalMusicAddict on 2005-10-25
Wow. Nice. Audiograbber works for me now but DVD Decrypter cant find a drive. Probally just the config. ;)

I used the repo not the .deb. Heres the lines to add:
```
deb http://wine.sourceforge.net/apt/ binary/
deb-src http://wine.sourceforge.net/apt/ source/
```
I must also say the one in the Breezy didnt work at all for me. This did.

---

### Post by tman_ubuntu on 2005-10-25
I installed wine using the instructions for Ubuntu at wineHQ.  When I ran wine at the commandline, I got this error message:

[i]
wine: creating configuration directory '/home/tman/.wine'...
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.6: cannot open shared object file: No such file or directory
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\user32.dll") failed (error c000007a).
err:module:import_dll Library user32.dll (which is needed by L"C:\\windows\\rundll32.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\rundll32.exe" failed, status c0000135
wine: wineprefixcreate failed while creating '/home/tman/.wine'.
[/i]

Can someone help me out here.  What do I do to fix?  Thanks in advance.

---

### Post by SickTwist on 2005-10-25
Are you trying to run a specific program with WINE?

You could try deleting the .wine directory to start fresh:
```

rm -r /home/tman/.wine

```
and then run the WINE configuration utility to re-create that directory:
```

winecfg

```

---

### Post by AgenT on 2005-10-25
So is wine an emulator yet? :rolleyes:

---

### Post by tman_ubuntu on 2005-10-25
[QUOTE=SickTwist]Are you trying to run a specific program with WINE?

You could try deleting the .wine directory to start fresh:
```

rm -r /home/tman/.wine

```
and then run the WINE configuration utility to re-create that directory:
```

winecfg

```[/QUOTE]

Thanks for replying.  It never could create the .wine directory.  It spit out the error from above.

I ran the winecfg and got pretty much the same error message:

> 
tman@ubuntuHusker:~$ winecfg
wine: creating configuration directory '/home/tman/.wine'...
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.6: cannot open shared object file: No such file or directory
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\user32.dll") failed (error c000007a).
err:module:import_dll Library user32.dll (which is needed by L"C:\\windows\\rundll32.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\rundll32.exe" failed, status c0000135
wine: wineprefixcreate failed while creating '/home/tman/.wine'.


---

### Post by jecos on 2005-10-26
[QUOTE=AgenT]So is wine an emulator yet? :rolleyes:[/QUOTE]


Its not an emulator and never will be, I'd consider it an interpreter for w32 API call's.  It's not running windows in the background, its reading windows os calls and converting them to native linux os calls and making the program act as native to linux as much as it can through every call conversion.

---

### Post by PsychoTrauma on 2005-10-26
I'm pretty happy with this release, I have had little problems and setup was extremely easy. Heres a  screenshot of wine running my favorite audio program foobar2000 (to which there is no match on linux (YET)).

[http://img.photobucket.com/albums/v508/PsychoTrauma/foobar2000.png]("http://img.photobucket.com/albums/v508/PsychoTrauma/foobar2000.png")

edit: changed  the picture to a link instead for people on dialup.

---

### Post by pinoyskull on 2005-10-26
ill try this later, ill post some feedback too :)

---

### Post by PatrickMay16 on 2005-10-26
[QUOTE=tman_ubuntu]Thanks for replying.  It never could create the .wine directory.  It spit out the error from above.

I ran the winecfg and got pretty much the same error message:[/QUOTE]
I've got the same problem. I had an earlier version of wine working fine, then I used the upgrade option in synaptic. After that, I was in the same situation as tman_ubuntu. I even tried doing the "complete removal" option in synaptic and deleting the .wine folder, then installing it again. Right now, it seems like it's unable to create the .wine folder for some reason. Here's what I get...

> 
patrick@ubuntu:~$ winecfg
wine: creating configuration directory '/home/patrick/.wine'...
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.6: cannot open shared object file: No such file or directory
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\user32.dll") failed (error c000007a).
err:module:import_dll Library user32.dll (which is needed by L"C:\\windows\\rundll32.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\rundll32.exe" failed, status c0000135
wine: wineprefixcreate failed while creating '/home/patrick/.wine'.
patrick@ubuntu:~$ 

I'm using Hoary, by the way.
EDIT:
Oh, man... Seems like I found out how to get it working. See it says *"err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.6: cannot open shared object file: No such file or directory"*? I figured some library it needs wasn't there, so I went into synaptic and  searched for "libstdc" and found the package "libstdc++6", which I decided to install. After that, I went to the terminal and typed "wine" and everything seemed to go OK. Right now I'm using it to run some windows application, and the application is working fine.
I hope this fixes the problem for you as well, tman_ubuntu.

---

### Post by AgenT on 2005-10-26
[quote=jecos]Its not an emulator and never will be, I'd consider it an interpreter for w32 API call's. It's not running windows in the background, its reading windows os calls and converting them to native linux os calls and making the program act as native to linux as much as it can through every call conversion.[/quote]

Yes, I know all that. It was a joke (notice the 'sarcasm' smilie).

---

### Post by Cyril on 2005-10-26
When I try to run warcraft 3 in version 0.9, I get this message asking me to insert the cd.  The cd is inside my drive and it is an original copy.  Also I have set up the cd drive using winecfg.

Since version 20050830 wine was supposed to have this securom thing which would allow checks for whether the cd is original to work.  However for this securom thing to work, wine would have to be compiled using gcc 3.4 and not 4.0.

I have run version 20050930 compliled with gcc 4.0 and 3.4 and can verify that securom only works with the later.

So my question is, is the wine 0.9 that I get when I use apt-get install wine complied with gcc 4.0?

If you wondering why don't I just comple wine 0.9 using gcc 3.4.  I have tried that and for some reason I can't get wine 0.9 to run that way.

---

### Post by GameManK on 2005-10-26
i installed the package

now how do i make a fake windows drive?
in the past i've used winetools..

---

### Post by Leigh on 2005-10-26
Run "winecfg" from the command line.

---

### Post by GameManK on 2005-10-26
when i run winecfg, click on drives, it tells me there is no c drive and i need to add one.  i click autodetect and then reconfigure some of the drives. i make C /home/yuriy/.wine/drive_c (that directory doesn't exist yet...).  Click apply. Nothing's created and this is what's printed in the konsole:

```
winecfg
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/home/yuriy/mydocs/source/amarok-1.3.5', starting in the Windows directory.
fixme:winspool:AddPrinterW DocumentPropertiesW on printer 'L"HP940c"' fails
err:winecfg:on_remove_click unixpath: /home/yuriy
err:winecfg:apply_drive_changes   unable to define devicename of 'C:', targetpath of '/home/yuriy/.wine/drive_c'
err:winecfg:apply_drive_changes   unable to define devicename of 'D:', targetpath of '/home/yuriy/mydocs'
err:winecfg:apply_drive_changes   unable to define devicename of 'E:', targetpath of '/home/yuriy/.wine'
err:winecfg:apply_drive_changes   unable to define devicename of 'F:', targetpath of '/media/hda1'
err:winecfg:apply_drive_changes   unable to define devicename of 'G:', targetpath of '/media/cdrom0'
err:winecfg:apply_drive_changes   unable to define devicename of 'H:', targetpath of '/media/cdrom1'
err:winecfg:apply_drive_changes   unable to define devicename of 'I:', targetpath of '/media/floppy0'
err:winecfg:apply_drive_changes   unable to define devicename of 'C:', targetpath of '/home/yuriy/.wine/drive_c'
err:winecfg:apply_drive_changes   unable to define devicename of 'D:', targetpath of '/home/yuriy/mydocs'
err:winecfg:apply_drive_changes   unable to define devicename of 'E:', targetpath of '/home/yuriy/.wine'
err:winecfg:apply_drive_changes   unable to define devicename of 'F:', targetpath of '/media/hda1'
err:winecfg:apply_drive_changes   unable to define devicename of 'G:', targetpath of '/media/cdrom0'
err:winecfg:apply_drive_changes   unable to define devicename of 'H:', targetpath of '/media/cdrom1'
err:winecfg:apply_drive_changes   unable to define devicename of 'I:', targetpath of '/media/floppy0'
err:winecfg:apply_drive_changes   unable to define devicename of 'C:', targetpath of '/home/yuriy/.wine/drive_c'
err:winecfg:apply_drive_changes   unable to define devicename of 'D:', targetpath of '/home/yuriy/mydocs'
err:winecfg:apply_drive_changes   unable to define devicename of 'E:', targetpath of '/home/yuriy/.wine'
err:winecfg:apply_drive_changes   unable to define devicename of 'F:', targetpath of '/media/hda1'
err:winecfg:apply_drive_changes   unable to define devicename of 'G:', targetpath of '/media/cdrom0'
err:winecfg:apply_drive_changes   unable to define devicename of 'H:', targetpath of '/media/cdrom1'
err:winecfg:apply_drive_changes   unable to define devicename of 'I:', targetpath of '/media/floppy0'
err:winecfg:apply_drive_changes   unable to define devicename of 'C:', targetpath of '/home/yuriy/.wine/drive_c'
err:winecfg:apply_drive_changes   unable to define devicename of 'D:', targetpath of '/home/yuriy/mydocs'
err:winecfg:apply_drive_changes   unable to define devicename of 'E:', targetpath of '/home/yuriy/.wine'
err:winecfg:apply_drive_changes   unable to define devicename of 'F:', targetpath of '/media/hda1'
err:winecfg:apply_drive_changes   unable to define devicename of 'G:', targetpath of '/media/cdrom0'
err:winecfg:apply_drive_changes   unable to define devicename of 'H:', targetpath of '/media/cdrom1'
err:winecfg:apply_drive_changes   unable to define devicename of 'I:', targetpath of '/media/floppy0'
err:winecfg:apply_drive_changes   unable to define devicename of 'C:', targetpath of '/home/yuriy/.wine/drive_c'
err:winecfg:apply_drive_changes   unable to define devicename of 'D:', targetpath of '/home/yuriy/mydocs'
err:winecfg:apply_drive_changes   unable to define devicename of 'E:', targetpath of '/home/yuriy/.wine'
err:winecfg:apply_drive_changes   unable to define devicename of 'F:', targetpath of '/media/hda1'
err:winecfg:apply_drive_changes   unable to define devicename of 'G:', targetpath of '/media/cdrom0'
err:winecfg:apply_drive_changes   unable to define devicename of 'H:', targetpath of '/media/cdrom1'
err:winecfg:apply_drive_changes   unable to define devicename of 'I:', targetpath of '/media/floppy0'
wine: Unhandled exception (thread 0009), starting debugger...

```

EDIT: deleted my .wine directory and it's working. i was hesitant to do this because i made a seperate partition for .wine so i had to unmount that.  i'll try to fully configure wine, rename .wine, remount the drive and move the stuff onto it

---

### Post by Emerzen on 2005-10-26
Hey, my experience has been more positive...although it's limited.  The only program I use WINE for is DVDShrink.  It worked w/ the last version in Hoary w/ some tweaking.  I couldn't get it to work in Breezy.  Since I updated to the latest version of WINE today and reinstalled DVDShrink, it has worked perfectly "out-of-the-box."  It even recognized my drives, and had the necessary DLLs.   Hope others have as much success.

---

### Post by GameManK on 2005-10-26
works and warcraft iii finally sees the cd!!

EDIT: well, actually i'm still having a problem: when i set the sound to aRts, winecfg doesn't work anymore, give debug messages..

---

### Post by drfalkor on 2005-10-26
This wine version rocks ! now, Photoshop 7.0 works faster and almoust feels like a native version of PS :D

---

### Post by jecos on 2005-10-26
[QUOTE=AgenT]Yes, I know all that. It was a joke (notice the 'sarcasm' smilie).[/QUOTE]

Yeah I kinda figured you knew. Oh well now anyone new seeing my post will understand a little better why 
WINE = Wine Is Not Emulator

---

### Post by Cyril on 2005-10-26
Gamemank, how did you install wine?  From source or repos?

---

### Post by GameManK on 2005-10-26
repos. i've done it from source before because the repos were rarely updated but i figured since the new version is there it's ok. why, is there something wrong with the repo packages?

---

### Post by drfalkor on 2005-10-26
Ugh, nevermind - everything is still freezing after awhile - So I have to do a ctrl + alt + backspace

well well, I still got my windows harddrive for Photoshoping ! ;)

---

### Post by quazi on 2005-10-26
I previously installed the most recent version of wine in the repositories and had it configured on another user (not mine).  I added the repositores for the new version of wine and did a sudo apt-get install wine, which I believe went well.  I type in "wine" and get this lovely message:
```
chris@serpent:~$ wine
wine: creating configuration directory '/home/chris/.wine'...
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  148 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Value in failed request:  0x24
  Serial number of failed request:  130
  Current serial number in output stream:  131
wine: wineprefixcreate failed while creating '/home/chris/.wine'.
chris@serpent:~$ wineserver: could not save registry branch to /home/chris/.wine-ublZO6/system.reg : No such file or directory
wineserver: could not save registry branch to /home/chris/.wine-ublZO6/user.reg : No such file or directory

```

If I create the .wine directory, wine will run but it won't have any configuration files, and winecfg is not working.  I have libsdc++6 or whatever installed already, is there something that I'm doin wrong?

---

### Post by Cyril on 2005-10-27
Gamemank:
No, nothing wrong with the repos.  If you look at my post on page 2 you'll understand my question.

Anyway thanks for the reply.

Edit:

Reinstalled for the tenth time.  Finally got it to work.  Have some issues with the cursor though.  Have to aim off.

---

### Post by acascianelli on 2005-10-27
[QUOTE=quazi]I previously installed the most recent version of wine in the repositories and had it configured on another user (not mine).  I added the repositores for the new version of wine and did a sudo apt-get install wine, which I believe went well.  I type in "wine" and get this lovely message:
```
chris@serpent:~$ wine
wine: creating configuration directory '/home/chris/.wine'...
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  148 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Value in failed request:  0x24
  Serial number of failed request:  130
  Current serial number in output stream:  131
wine: wineprefixcreate failed while creating '/home/chris/.wine'.
chris@serpent:~$ wineserver: could not save registry branch to /home/chris/.wine-ublZO6/system.reg : No such file or directory
wineserver: could not save registry branch to /home/chris/.wine-ublZO6/user.reg : No such file or directory

```

If I create the .wine directory, wine will run but it won't have any configuration files, and winecfg is not working.  I have libsdc++6 or whatever installed already, is there something that I'm doin wrong?[/QUOTE]

I'm having a similar problem...Heres what happen when I run "wine"...

```
acascianelli@ubuntu:~$ wine
wine: creating configuration directory '/home/acascianelli/.wine'...

sizeof(RADEONDRIRec) == 100, devPrivSize 100
wine: Unhandled exception (thread 0009), starting debugger...
wine: wineprefixcreate failed while creating '/home/acascianelli/.wine'.
wineserver: could not save registry branch to /home/acascianelli/.wine-AkprLw/system.reg : No such file or directory
wineserver: could not save registry branch to /home/acascianelli/.wine-AkprLw/user.reg : No such file or directory

```

It pops up a windows that asks to debug, if I click yes, it will create the .wine folder and wine and winecfg will run ok.  But I'm getting strange errors when running and installing programs.

---

