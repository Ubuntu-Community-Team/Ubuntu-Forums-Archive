---
title: "Powerpoint won't insert mpg or wmv videos"
date: 2007-06-11
forum: General Help
---

### Post by TravMan63 on 2007-06-11
I am running Powerpoint 2003 in xubuntu 7.04.

I can insert photos (png) files fine - but when I try to insert a wmv or mpg file - it reports 'it cannot insert a movie from the selected file.  Verify that the path and file format are correct and then try again'.

I can play the videos fine in xine...

I have moved the files, renamed them ... no go...
I must also run PowerPoint as root - if I run it as the standard user, PowerPoint reports
(something to the effect of "not installed for current user, please re-run setup"


In case your're wondering why I'm not using impress... Impress had performance issues regarding the video (slide animation/ text animations were
simply too slow, and existing ppt files needed too much tweaking ))  and the files edited by impress (which I could insert the video file into) - would then not play in powerpoint (it is as if the video was never inserted)

Any help appreciated...
TM

---

### Post by reckless2k2 on 2007-06-11
hhmmm...just my 2 cents but it might be because you're running powerpoint in wine i assume. try opening it in impress, attach the video, save, then open in powerpoint and see if it works for you. it's worth a try.

---

### Post by TravMan63 on 2007-06-11
um - nope....

Impress 'breaks the file' - it will import it... but when it's saved (as ppt format) - and power point or impress opens it - it's not there - and the filesize is smaller than the original

--------edit
hmmm - is it not the 'file not found' message - but a 'I can't support that filetype" error

this from terminal
----
fixme:mci:MCI_LoadMciDriver Couldn't load driver for type L"MPEGVIDEO".
If you don't have a windows installation accessible from Wine,
you perhaps forgot to create a [mci] section in system.ini
----

do I need windows media player as well..? hmmm...
-------
2nd edit
installed wmplayer 7 - didn't help
looks like it's back to XP... and rebuilding my boot sector - whoopie

powerpoint wouldn't activate anyway and will die in about 45 more starts

---

### Post by cookies on 2007-06-11
> **TravMan63 said:**
> I am running Powerpoint 2003 in xubuntu 7.04.

I can insert photos (png) files fine - but when I try to insert a wmv or mpg file - it reports 'it cannot insert a movie from the selected file.  Verify that the path and file format are correct and then try again'.

I can play the videos fine in xine...

I have moved the files, renamed them ... no go...
[B] I must also run PowerPoint as root - if I run it as the standard user, PowerPoint reports
(something to the effect of "not installed for current user, please re-run setup"[/B]


In case your're wondering why I'm not using impress... Impress had performance issues regarding the video (slide animation/ text animations were
simply too slow, and existing ppt files needed too much tweaking ))  and the files edited by impress (which I could insert the video file into) - would then not play in powerpoint (it is as if the video was never inserted)

Any help appreciated...
TM

That tipped me off on something:

Now, go to ~/.wine/drive_c/Program Files/Microsoft Office/OFFICE11 and try to open Word. If it says you have not installed it, run the installer from the CD again, and select Repair and Repair All

Now, you have to set some DLL's, so open winecfg, and select Applications > Add Application and add PowerPoint, Word, and Excel.

Now, select Word, go to Libraries

Add the riched20.dll and set it to Native. Do this for all of the Office Apps.

Next, for the Default Settings, download and install wininet.dll:
[http://www.dll-files.com/dllindex/dl....shtml?wininet](http://www.dll-files.com/dllindex/dl....shtml?wininet)

Put it in
~/.wine/drive_c/windows/system32

There is already one there, but overwrite it.

Now for Default Settings, select wininet.dll in Libraries and set it to Native

Open Word again, and fill in the name and stuff it asks, now, for Product Registration, you have to call and follow the procedure, because Activation over the Internet doesn't work.

As for the importing, I dunno.

---

### Post by TravMan63 on 2007-06-11
Thank you cookie! - :popcorn:  that did allow me to run as user and not root...


but - the insert problem still exists... :(  anyone else have ideas on this one?

---

### Post by cookies on 2007-06-11
Glad to see that one part worked! :D <_>

You probably need Windows Media Player, but the latest version that installs is 6 something.

---

### Post by TravMan63 on 2007-06-11
I have 'one' of those versions (I think 6 or 7?) installed...
it does need a gecko install too - maybe that'll do it...

A wild workaround is to put xine with with videos on one desktop - switch to the desktop with powerpoint for a slide... then back again.... when that is performed, xine doesn't 'release' the audio channel - and the sound efx in ppt won't work... and the remote clicker won't do all that - just the keyboard...

chip chip chip chip....

still open to (requesting) ideas 

(btw - had to install with winefile - command prompt didn't actually write the files... or maybe it did as root and I looked in the /home/user dir instead of root... my head hurts... :KS)

TM
----
um - don't geckos eat bugs....

---

### Post by TravMan63 on 2007-06-12
Update...

Uninstalled windows media player 7.x - wine doesn't support it well
Uninstalled office 2003 with/from the root account (note that wine hq says to NOT run wine as root!)

Installed windows media player 6.x - it installed and runs fine ...but....
        Note - had to install with wine file - wine install exename from terminal doesn't seem to work
        Windows media player - has same errors 'director or name is incorrect' - so I'm not sure if it really plays
        or not - it did indicate that various codecs were being installed.


I moved files around to different diretories (seems that wine 'maps' the real linux system with a 'virtual' one)
-- n/c

I would also add - that powerpoint can open a ppt file - from the same directory that the media files exist in.

Wav files that are imbedded - play fine...

TM

---

### Post by TravMan63 on 2007-06-13
I ran Powerpoint from terminal...

1) It didn't prompt me to phone home to activate (still need to do that once it's up and running)

2)
Here is the output after I clicked the insert movie

```

fixme:win:UpdateLayeredWindow (0x10086,0x504,0x33d264,0x33d284,0x2d0c,0x33d26c,0x00000000,0x33d2d8,2): stub!
fixme:shell:DllGetClassObject failed for CLSID=
        {208d2c60-3aea-1069-a2d7-08002b30309d} (My Network Places)
err:shell:SHCoCreateInstance LoadFromShell failed for CLSID=
        {208d2c60-3aea-1069-a2d7-08002b30309d} (My Network Places)
fixme:shell:DllGetClassObject failed for CLSID=
        {208d2c60-3aea-1069-a2d7-08002b30309d} (My Network Places)
err:shell:SHCoCreateInstance LoadFromShell failed for CLSID=
        {208d2c60-3aea-1069-a2d7-08002b30309d} (My Network Places)
fixme:shell:DllGetClassObject failed for CLSID=
        {208d2c60-3aea-1069-a2d7-08002b30309d} (My Network Places)
err:shell:SHCoCreateInstance LoadFromShell failed for CLSID=
        {208d2c60-3aea-1069-a2d7-08002b30309d} (My Network Places)
fixme:imm:ImmReleaseContext (0x100aa, 0x16d8b0): stub
fixme:imm:ImmReleaseContext (0x100aa, 0x16d8b0): stub
fixme:imm:ImmGetDefaultIMEWnd (0x100aa - (nil) 0x16d8b0 ): semi-stub
fixme:shell:SHGetFileInfoW SHGFI_OVERLAYINDEX unhandled
fixme:shell:DllGetClassObject failed for CLSID=
        {208d2c60-3aea-1069-a2d7-08002b30309d} (My Network Places)
err:shell:SHCoCreateInstance LoadFromShell failed for CLSID=
        {208d2c60-3aea-1069-a2d7-08002b30309d} (My Network Places)
fixme:ole:OleQueryLinkFromData (0x17d2a0),stub!
fixme:imm:ImmGetDefaultIMEWnd (0x100aa - 0x100b6 0x16d8b0 ): semi-stub
fixme:imm:ImmReleaseContext (0x10098, 0x16d8b0): stub
fixme:shell:IShellView_fnSaveViewState (0xd1acb0) stub
fixme:imm:ImmReleaseContext (0x10098, 0x16d8b0): stub
fixme:imm:ImmReleaseContext (0x10098, 0x16d8b0): stub
fixme:imm:ImmReleaseContext (0x10098, 0x16d8b0): stub
fixme:imm:ImmReleaseContext (0x10098, 0x16d8b0): stub
fixme:imm:ImmGetDefaultIMEWnd ((nil) - 0x100b6 0x16d8b0 ): semi-stub
fixme:mci:MCI_LoadMciDriver Couldn't load driver for type L"MPEGVIDEO".
If you don't have a windows installation accessible from Wine,
you perhaps forgot to create a [mci] section in system.ini
fixme:mci:MCI_LoadMciDriver Couldn't load driver for type L"MPEGVIDEO".
If you don't have a windows installation accessible from Wine,
you perhaps forgot to create a [mci] section in system.ini
err:msi:MsiQueryFeatureStateW L""
fixme:ole:OleQueryLinkFromData (0x17d2a0),stub!
fixme:ole:OleQueryLinkFromData (0x17d2a0),stub!

```

output from successfully inserting an image:
```

fixme:shell:DllGetClassObject failed for CLSID=
        {208d2c60-3aea-1069-a2d7-08002b30309d} (My Network Places)
err:shell:SHCoCreateInstance LoadFromShell failed for CLSID=
        {208d2c60-3aea-1069-a2d7-08002b30309d} (My Network Places)
fixme:shell:DllGetClassObject failed for CLSID=
        {208d2c60-3aea-1069-a2d7-08002b30309d} (My Network Places)
err:shell:SHCoCreateInstance LoadFromShell failed for CLSID=
        {208d2c60-3aea-1069-a2d7-08002b30309d} (My Network Places)
fixme:imm:ImmReleaseContext (0x4009e, 0x16d8b0): stub
fixme:imm:ImmReleaseContext (0x4009e, 0x16d8b0): stub
fixme:imm:ImmGetDefaultIMEWnd (0x4009e - 0x100b6 0x16d8b0 ): semi-stub
fixme:shell:SHGetFileInfoW SHGFI_OVERLAYINDEX unhandled
fixme:shell:DllGetClassObject failed for CLSID=
        {208d2c60-3aea-1069-a2d7-08002b30309d} (My Network Places)
err:shell:SHCoCreateInstance LoadFromShell failed for CLSID=
        {208d2c60-3aea-1069-a2d7-08002b30309d} (My Network Places)
fixme:ole:OleQueryLinkFromData (0x17d2a0),stub!
fixme:imm:ImmGetDefaultIMEWnd (0x4009e - 0x100b6 0x16d8b0 ): semi-stub
fixme:imm:ImmReleaseContext (0x300b8, 0x16d8b0): stub
fixme:shell:IShellView_fnSaveViewState (0xd153f0) stub
fixme:imm:ImmReleaseContext (0x300b8, 0x16d8b0): stub
fixme:imm:ImmReleaseContext (0x300b8, 0x16d8b0): stub
fixme:imm:ImmReleaseContext (0x300b8, 0x16d8b0): stub
fixme:imm:ImmReleaseContext (0x300b8, 0x16d8b0): stub
fixme:imm:ImmGetDefaultIMEWnd ((nil) - 0x100b6 0x16d8b0 ): semi-stub
fixme:ole:OleQueryLinkFromData (0x17d2a0),stub!

```

This is what windows media player spits out in terminal (same error reported as powerpoint - but the code is quite different:)
```


fixme:quartz:FilterGraphNoThread_create CLSID_FilterGraphNoThread partially implemented - Forwarding to CLSID_FilterGraph
fixme:quartz:Filtergraph_QueryInterface unknown interface {8e1c39a1-de53-11cf-aa63-0080c744528d}
fixme:quartz:Filtergraph_QueryInterface unknown interface {fc4801a3-2ba9-11cf-a229-00aa003d7352}
fixme:wininet:InternetCanonicalizeUrlW Unhandled flags 0x20000000
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found


```

From all that - it appears a clue may lie in this output:

```

fixme:mci:MCI_LoadMciDriver Couldn't load driver for type L"MPEGVIDEO".
If you don't have a windows installation accessible from Wine,
you perhaps forgot to create a [mci] section in system.ini
fixme:mci:MCI_LoadMciDriver Couldn't load driver for type L"MPEGVIDEO".
If you don't have a windows installation accessible from Wine,
you perhaps forgot to create a [mci] section in system.ini
err:msi:MsiQueryFeatureStateW L""

```

](*,) Thanks for all your brain cell activity!  Hopefully someone out there can break this wall down...](*,)

TM

---

### Post by TravMan63 on 2007-06-13
update...
I placed a mciqtz.drv file in the system 32 folder...
(as suggested here [http://support.microsoft.com/kb/178291](http://support.microsoft.com/kb/178291)) - my error I received was different that any here ...)

edited the system and win ini files (no change to the reference of the mciqtz.drv; that was 'correct' system.ini - win.ini added more filetypes - no wmv though...)

and now ...
powerpoint now hangs while trying to load the video

](*,)

Is there a way to make powerpoint use xine? (if that is the problem here - ](*,)

---

### Post by TravMan63 on 2007-06-15
update....
I'm attempting an install of ies4linux .... but I think microsofts site is down

I also downloaded the ie6xxxx.exe and tried to run that in wine as well - same error 'can't connect'

Hoping maybe there is 'dependancy' in this 'package' from Microsoft that will fix this problem...
[http://ubuntuforums.org/showthread.php?t=372011](http://ubuntuforums.org/showthread.php?t=372011)
[http://ubuntuforums.org/showthread.php?t=466342](http://ubuntuforums.org/showthread.php?t=466342)

Any other ideas?
TM
---edit---
IE4SLinux installed and running ! :)
Didn't fix the problem with ppt :(
oh well - anyone?

---

### Post by TravMan63 on 2007-07-19
I've worked on this issue some more, and have made some progress, but it's still not working 100%.

I did NOT actually test inserting movies (but I would guess I could), but - before when I attempted to
open a .ppt file - powerpoint would hang.  Now it does not.

The fix : insert a mciqtz32.dll into the system32 folder.

I can now open the file and play the presentation.  However, the movies show up as all black.


It seems I may have 2 wine installations... in the .wine folder "c_drive" appears - as well as "Program Files" and "Windows" --- I had been working in the "Windows" folder - when I should have been in "c_drive\windows"

--
Here is the output from Terminal now:
```


fixme:icon:DrawIconEx no flags set? setting to DI_NORMAL
fixme:system:SystemParametersInfoW Unimplemented action: 8202 (SPI_GETFONTSMOOTHINGTYPE)
fixme:icon:DrawIconEx no flags set? setting to DI_NORMAL
fixme:hlink:IHlink_fnGetStringReference (0x1789f0) -> (0 0x33dc14 0x33dc18)
fixme:hlink:IHlink_fnGetStringReference Unhandled case, no set Target and no moniker
fixme:hlink:IHlink_fnSetMonikerReference (0x20a440)->(0 0x17d328 L"1")
fixme:hlink:IHlink_fnGetStringReference (0x20a440) -> (0 0x33dac0 0x33dac4)
fixme:hlink:IHlinkBC_SetInitialHlink (0x17d328)->(0x18f918 L"256,1,Slide 1" L"Slide 1")
fixme:hlink:IHlink_fnSetMonikerReference (0x20a440)->(0 0x18f918 L"256,1,Slide 1")
fixme:hlink:IHlinkBC_Register (0x17d328)->(0 0x3bce954 0x18fb10 0x3bce968)
fixme:ole:ItemMonikerImpl_Construct lpszDelim is NULL. Using empty string which is possibly wrong.
fixme:hlink:IHlink_fnNavigate Semi-Stub:(0x1789f0)->(0 (nil) 0x3bcd304 0x17d328)
fixme:hlink:IHlinkBC_OnNavigateHlink (0x17d328)->(0 0x20a678 L"257,2,Slide 2" L"Slide 2" (nil))
fixme:hlink:IHlinkBC_Revoke (0x17d328)->(10)
fixme:icon:DrawIconEx no flags set? setting to DI_NORMAL
fixme:system:SystemParametersInfoW Unimplemented action: 8202 (SPI_GETFONTSMOOTHINGTYPE)
fixme:icon:DrawIconEx no flags set? setting to DI_NORMAL


```

These all appear to be wine related?

The info that set me off to the mciqtz.dll was this output:
```

err:rundll32:main Unable to load L"mciqtz32.dll"

```
(That appears to be the only difference in the output from terminal now - the mciqtz error was at the very end of the output)

On a side note: Windows Media Player 6.4 still can not find files, and it's output is

```

fixme:quartz:DBToAmpFactor (-10000) Stub!
fixme:quartz:DBToAmpFactor (0) Stub!
fixme:quartz:AmpFactorToDB (0) Stub!
fixme:quartz:DBToAmpFactor (-10000) Stub!
fixme:quartz:DBToAmpFactor (0) Stub!
fixme:quartz:AmpFactorToDB (100) Stub!
fixme:quartz:FilterGraphNoThread_create CLSID_FilterGraphNoThread partially implemented - Forwarding to CLSID_FilterGraph
fixme:quartz:Filtergraph_QueryInterface unknown interface {8e1c39a1-de53-11cf-aa63-0080c744528d}
fixme:quartz:Filtergraph_QueryInterface unknown interface {fc4801a3-2ba9-11cf-a229-00aa003d7352}
fixme:wininet:InternetCanonicalizeUrlW Unhandled flags 0x20000000
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found

```

I'm guessing the two errors may be related.

See also post:
[http://ubuntuforums.org/showthread.php?t=482178](http://ubuntuforums.org/showthread.php?t=482178)

---

### Post by gmatht on 2008-04-13
> I placed a mciqtz.drv file in the system 32 folder...

Try copying mciqtz32.dll from your windows installation into 
 ~/.wine/drive_c/windows/system32/

Then edit
  ~/.wine/drive_c/windows/system.ini

Replace the line
   MPEGVideo=mciqtz.drv

with 
 MPEGVideo=mciqtz32.dll

---

