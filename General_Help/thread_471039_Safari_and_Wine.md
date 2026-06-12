---
title: "Safari and Wine"
date: 2007-06-11
forum: General Help
---

### Post by ThinkBuntu on 2007-06-11
Safari (the default Mac browser) was released today for Windows, which means us web designers can finally test on it without some crazy WebKit installation, or trusting Konqueror's rendering to be close. Of course, Wine couldn't install it.

Any Wine gurus in here who can figure out how to install Safari?

---

### Post by flavioamieiro on 2007-06-11
Well, I'm certainly not a Wine guru but, as far as I can tell, the safari is Beta an reaaally uninstable even for windows (things like not showing some links, or non-functioning functionalities).
I think this should be corrected soon enough, but for now it will be hard to use it, on windows or via Wine.

---

### Post by Bablefish on 2007-06-11
Heres on ALT [http://mac-on-linux.sourceforge.net/news.php](http://mac-on-linux.sourceforge.net/news.php)

---

### Post by Hendrixski on 2007-06-11
Umm... guys
Safari is just Konqueror with a proprietary interface that you can't modify.  you already have safari on your system, just install konqueror.

P.S. apparently apple does a piss-poor job of sending their modifications upstream, why should we reward them for trying to steal open source software for proprietary profit.

---

### Post by neorou on 2007-06-11
ThinkBuntu,

Would this:
[http://www.browsrcamp.com/](http://www.browsrcamp.com/)

help you out?

---

### Post by flavioamieiro on 2007-06-11
@neorou
Yes, this browsrcamp.com site is good, but sometimes, when developing a website, you need more than that. For example: when you have dinamic content, or even simple css stuff that happens when the mouse goes over some object.

@hendrixski
I must confess my ignorance. I've heard safari uses konqueror engine, but never knew to what extent.
If even a minor change has been made, it may change the way a web site looks/works. And if that's the case, it's necessary for any decent web developer to do a test on it. 
The idea - at least for me (and I'm not even a web dev.) - is to test my stuff in all the browsers I can get my hands on.

---

### Post by firephoto on 2007-06-11
> **ThinkBuntu said:**
> 
Any Wine gurus in here who can figure out how to install Safari?
Back to your original question...

It uses .net and that doesn't seem to work with wine.

Here's the error I get after it's installed and I try to run it.
```

$ wine Safari.exe 
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Safari\\icuuc36.dll") not found 
err:module:import_dll Library icuuc36.dll (which is needed by L"C:\\Program Files\\Safari\\icuin36.dll") not found 
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Safari\\icuin36.dll") not found 
err:module:import_dll Library icuin36.dll (which is needed by L"C:\\Program Files\\Safari\\CoreFoundation.dll") not found 
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Safari\\icuuc36.dll") not found 
err:module:import_dll Library icuuc36.dll (which is needed by L"C:\\Program Files\\Safari\\CoreFoundation.dll") not found 
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Safari\\CoreFoundation.dll") not found 
err:module:import_dll Library CoreFoundation.dll (which is needed by L"C:\\Program Files\\Safari\\Safari.exe") not found 
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Safari\\icuuc36.dll") not found 
err:module:import_dll Library icuuc36.dll (which is needed by L"C:\\Program Files\\Safari\\icuin36.dll") not found 
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Safari\\icuin36.dll") not found 
err:module:import_dll Library icuin36.dll (which is needed by L"C:\\Program Files\\Safari\\CoreFoundation.dll") not found 
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Safari\\icuuc36.dll") not found 
err:module:import_dll Library icuuc36.dll (which is needed by L"C:\\Program Files\\Safari\\CoreFoundation.dll") not found 
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Safari\\CoreFoundation.dll") not found 
err:module:import_dll Library CoreFoundation.dll (which is needed by L"C:\\Program Files\\Safari\\CFNetwork.dll") not found 
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Safari\\pthreadVC2.dll") not found 
err:module:import_dll Library pthreadVC2.dll (which is needed by L"C:\\Program Files\\Safari\\CFNetwork.dll") not found 
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Safari\\SQLite3.dll") not found 
err:module:import_dll Library SQLite3.dll (which is needed by L"C:\\Program Files\\Safari\\CFNetwork.dll") not found 
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Safari\\CFNetwork.dll") not found 
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Safari\\CFNetwork.dll") not found 
err:module:import_dll Library CFNetwork.dll (which is needed by L"C:\\Program Files\\Safari\\Safari.exe") not found 
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Safari\\icuuc36.dll") not found 
err:module:import_dll Library icuuc36.dll (which is needed by L"C:\\Program Files\\Safari\\icuin36.dll") not found 
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Safari\\icuin36.dll") not found 
err:module:import_dll Library icuin36.dll (which is needed by L"C:\\Program Files\\Safari\\CoreFoundation.dll") not found 
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Safari\\icuuc36.dll") not found 
err:module:import_dll Library icuuc36.dll (which is needed by L"C:\\Program Files\\Safari\\CoreFoundation.dll") not found 
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Safari\\CoreFoundation.dll") not found 
err:module:import_dll Library CoreFoundation.dll (which is needed by L"C:\\Program Files\\Safari\\CoreGraphics.dll") not found 
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Safari\\zlib1.dll") not found 
err:module:import_dll Library zlib1.dll (which is needed by L"C:\\Program Files\\Safari\\CoreGraphics.dll") not found 
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Safari\\CoreGraphics.dll") not found 
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Safari\\CoreGraphics.dll") not found 
err:module:import_dll Library CoreGraphics.dll (which is needed by L"C:\\Program Files\\Safari\\Safari.exe") not found 
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Safari\\Safari.exe") not found 
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Safari\\Safari.exe") not found 
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Safari\\Safari.exe" failed, status c0000135 

```

---

### Post by Hendrixski on 2007-06-11
> **flavioamieiro said:**
> @neorou
I must confess my ignorance. I've heard safari uses konqueror engine, but never knew to what extent.
If even a minor change has been made, it may change the way a web site looks/works. And if that's the case, it's necessary for any decent web developer to do a test on it. 
The idea - at least for me (and I'm not even a web dev.) - is to test my stuff in all the browsers I can get my hands on.

Hey, I just learned about that today when I went to the wikipedia page for safari.  The part of the browser that does the heavy lifting t(the HTML rendering and the javascript interpreting) is already available to you without a proprietary interface.

However, you *should* contact Apple and tell them to make their non-customizable interface available for other Unixes (like linux... because Mac OS X is a UNIX) so that people see just how non-customizable and terrible it really is.

---

### Post by neorou on 2007-06-11
Flavioameiro,

Maybe it's time to use a virtualization agent.  I myself am thinking of trying kvm, but do not yet hav the chance.

Good luck...

---

### Post by flavioamieiro on 2007-06-11
Neorou,
Shure, that's the best way we can test things in Safari for now. Even though your solution is engough in most cases.

Hendrixski,
I understand perfectly what you're saying, and I'm not (hell no!!) telling you that I want to use Safari as my web browser. All I'm saying is that I like to have as many browsers as I can avayable for testing proposes only. If there is no change AT ALL in the rendering (from Konqueror to Safari), than that's not necessary. On the other hand, if there's any discrepancy between both apps's way of dealing with content, than I'd like to get a copy of the (highly-proprietary-non-customizable) Safari.

---

### Post by firephoto on 2007-06-11
Safari stable in 10.4.9 and Konqueror in 3.5.7 both render things in their own way. The way javascript is used is the source of a lot of problems with Konqueror until they fix the reported problems by returning a "yes" to an "are you gecko" question which was essentially the latest fix for google changing something with gmail.

The nightly webkit builds for mac os x work on a lot of the fancy java stuff better than current releases of webkit/khtml.

---

### Post by deadlikeoscar on 2007-06-12
Here's what I got when I dll overrode all of the files that were posted before during setup. I don't know much about dll overrides but I thought it might be funny try it anyway. Maybe having some different output will be good to help people to get it running in wine.

```
deadlikeoscar@Network:~/.wine/drive_c/Program Files/Safari$ wine Safari.exe
err:module:LdrInitializeThunk "MSVCR80.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Safari\\Safari.exe" failed, status c0000142
```

And this Microsoft Visual C++ Runtime Library text box appears and says:

```
Runtime Error!

Program C:\Program Files\Safari\Safari.exe

R6034
An application has made an attempt to load the C runtime library
incorrectly.
Please contact the application's support team for more information.
```

---

### Post by smiley2billion on 2007-06-12
I tried copying over the MSVCR80.dll file to Wines /windows/system32 folder and still get the same error.

I also attempted to install the "Microsoft Visual C++ 2005 Redistributable Package" which I read will install the proper runtimes but still with no luck.  Also, attempting to run it in "Windows XP" or "Windows Vista" mode using winecfg only angers it further, with it crashing with the same error message.

---

### Post by lw5 on 2007-06-12
Apparently it helps to copy the msvcr.dll and the msvcp.dll from the drive_c/windows/winsxs/x86_Microsoft.VC80.CRT_* directory  to the safari program folder. 
After that I get a (very) incomplete window (see attached file) and these messages:

```
> wine Safari.exe
fixme:actctx:FindActCtxSectionStringW 00000000 (null) 2 L"msvcr80.dll" 0x337aec
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:toolbar:TOOLBAR_SetExtendedStyle Unknown Toolbar Extended Style 0x00000080. Please report.
fixme:shell:URL_ParseUrl failed to parse L""
fixme:menu:SetMenuInfo MNS_NOTIFYBYPOS partially implemented
fixme:menu:SetMenuInfo MNS_NOTIFYBYPOS partially implemented
fixme:menu:SetMenuInfo MNS_NOTIFYBYPOS partially implemented
fixme:menu:SetMenuInfo MNS_NOTIFYBYPOS partially implemented
fixme:menu:SetMenuInfo MNS_NOTIFYBYPOS partially implemented
fixme:menu:SetMenuInfo MNS_NOTIFYBYPOS partially implemented
fixme:menu:SetMenuInfo MNS_NOTIFYBYPOS partially implemented
fixme:menu:SetMenuInfo MNS_NOTIFYBYPOS partially implemented

```

when I switch from the Safari window my terminal window I get:

```

err:bitmap:DIB_GetBitmapInfo (44): unknown/wrong size for header
wine: Unhandled page fault on read access to 0x00230000 at address 0x6b262e97 (thread 0009), starting debugger...
WineDbg starting on pid 0008
Unhandled exception: page fault on read access to 0x00230000 in 32-bit code (0x6b262e97).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:6b262e97 ESP:0033eba0 EBP:0033ed38 EFLAGS:00010206(   - 00      - RIP1)
 EAX:00230000 EBX:0033ed78 ECX:00000000 EDX:00000000
 ESI:25003d40 EDI:007755d0
Stack dump:
0x0033eba0:  6dccd8ff 6b0ef4d3 007755d0 00000006
0x0033ebb0:  0000000b 0033f09c 00000000 00000000
0x0033ebc0:  00000000 00000000 00000000 0000000a
0x0033ebd0:  0033f09a 00000000 00000000 00000000
0x0033ebe0:  00000000 00000000 00000000 00000000
0x0033ebf0:  00000000 00000000 00000000 0033ed20
Backtrace:
=>1 0x6b262e97 in coregraphics (+0x262e97) (0x0033ed38)
  2 0x6b0f9da4 in coregraphics (+0xf9da4) (0x0033f31c)
  3 0x6b1e0fff in coregraphics (+0x1e0fff) (0x0033f4bc)
  4 0x6b1d19ee in coregraphics (+0x1d19ee) (0x0033f578)
  5 0x00000000 (0x00000000)
0x6b262e97: testl       %eax,0x0(%eax)
Wine-dbg>

```

I'm running this on Ubuntu Feisty, Wine 0.9.33 (windows XP).


Edit:
Okay, it seems to be possible through a very nasty Wine hack. I haven't tried it yet, I'm still compiling:
in /dlls/gdi32/dib.c change
```
if (header->biSize == sizeof(BITMAPV5HEADER))
```
to 
```
if (header->biSize == sizeof(BITMAPV5HEADER) || header->biSize == 44)
```

---

### Post by lw5 on 2007-06-12
The above can be confirmed. See the screenshot.
Ubuntu Feisty Fawn, Hacked Wine 0.9.38, Safari 3 Bèta

---

### Post by ThinkBuntu on 2007-06-12
> **Hendrixski said:**
> Umm... guys
Safari is just Konqueror with a proprietary interface that you can't modify.  you already have safari on your system, just install konqueror.
I can say with certainty that I have witnessed fine differences in the layout engines of Safari and Konqueror. Safari was introduced over five years ago and was based on Konqueror back then, but since both have changed significantly.

---

### Post by Swab on 2007-06-12
> **lw5 said:**
> 
Okay, it seems to be possible through a very nasty Wine hack. I haven't tried it yet, I'm still compiling:


How long did your compile take?

---

### Post by Swab on 2007-06-12
> **lw5 said:**
> Apparently it helps to copy the msvcr.dll and the msvcp.dll from the drive_c/windows/winsxs/x86_Microsoft.VC80.CRT_* directory  to the safari program folder. 


So I made the hack, compiled and installed... but don't seem to have those dll files.

---

### Post by lw5 on 2007-06-12
I think it's also possible to get those dll's through winetricks which is linked somewhere in the [Safari discussion in the Wine newsgroups](http://groups.google.com/group/comp.emulators.ms-windows.wine/browse_thread/thread/4ad4fac5fd33648d/bafcf09669cd9104#bafcf09669cd9104)

---

### Post by Swab on 2007-06-12
> **lw5 said:**
> I think it's also possible to get those dll's through winetricks which is linked somewhere in the [Safari discussion in the Wine newsgroups](http://groups.google.com/group/comp.emulators.ms-windows.wine/browse_thread/thread/4ad4fac5fd33648d/bafcf09669cd9104#bafcf09669cd9104)

Hmmm, still not having any luck.  

Don't worry I don't have much reason to install Safari anyway, I was just bored!

---

### Post by odinfromvalhalla on 2008-01-05
You can get Safari 3 beta to run under Ubuntu (or any Linux for that mater) using wine: [Installing Safari 3 beta on Ubuntu 7.10]("http://myscienceisbetter.info/2008/01/installing-safari-3-beta-on-ub.html")

---

