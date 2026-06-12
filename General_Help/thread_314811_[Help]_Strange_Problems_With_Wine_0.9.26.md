---
title: "[Help] Strange Problems With Wine 0.9.26"
date: 2006-12-08
forum: General Help
---

### Post by KucingKelabu on 2006-12-08
Hello folks :)

It's been the 4th week of me running fully on Ubuntu and it have been great. I manage to get most of my task done without much hassle - and now I'm willing to dive in further and start fiddling with WINE.

Note: I did try Wine (installed using apt-get, i think was 0.9.22) a few weeks back and it works pretty much without much issues (Was running photoshop on it)

However, recently I've installed Cedega, and plays my favorite game on it - StarCraft. It runs perfectly and successfully brings back all those nostalgic memories, anyways, I'm trying to install a game, an online game, Ragnarok Online). Here's where the weirdness start:

1) I can never connect no matter what, and which edition I installed (I tried a few private ones just to check, even though I'm playing the official ones). It always said "Connecting to server" for a while, and then it will prompt "Failed to connect to server"

2) Confused, I opened the Gecko browser in wine (using "wine iexplore.exe") and then it prompted me to install the gecko browser, i pressed install, and it said "downloading". Then after about 5 seconds, it errored out (and leave an empty window):

```

$ wine iexplore.exe
fixme:shdocvw:IEWinMain "" 1
fixme:ole:CoResumeClassObjects stub
err:ole:CoGetClassObject apartment not initialised
err:cabinet:FDICopy FDIIsCabinet failed.
err:mshtml:InstallCallback_OnStopBinding Could not extract package: 80004005
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
Could not load Mozilla. HTML rendering will be disabled.
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x184594)->((null) 1 0x33faec (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x184594)->((null) 25 2 0x33fb00 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x184594)->((null) 26 2 0x33fb00 (nil))
fixme:shdocvw:ClDispatch_Invoke (0x184594)->(-709 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33fa44 0x33fa90 (nil) 0x33fa54)
fixme:shdocvw:ClDispatch_Invoke (0x184594)->(-5512 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33fa04 0x33fa50 (nil) 0x33fa14)
fixme:shdocvw:ClDispatch_Invoke (0x184594)->(-5501 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33fa44 0x33fa90 (nil) 0x33fa54)
fixme:shdocvw:ClDispatch_Invoke (0x184594)->(-5512 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33fa04 0x33fa50 (nil) 0x33fa14)
fixme:shdocvw:ClDispatch_Invoke (0x184594)->(-5502 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33fa44 0x33fa90 (nil) 0x33fa54)
fixme:shdocvw:ClDispatch_Invoke (0x184594)->(-5513 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33fa44 0x33fa90 (nil) 0x33fa54)
fixme:shdocvw:ClDispatch_Invoke (0x184594)->(-726 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33fa44 0x33fa90 (nil) 0x33fa54)
fixme:shdocvw:ClientSite_GetContainer (0x184594)->(0x33fb2c)
fixme:shdocvw:ClOleCommandTarget_Exec (0x184594)->({000214d1-0000-0000-c000-000000000046} 37 0 0x33fc08 (nil))
fixme:shdocvw:ClDispatch_Invoke (0x184594)->(-5502 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33fb14 0x33fbf8 (nil) 0x33fb24)
fixme:shdocvw:ClDispatch_Invoke (0x184594)->(-5501 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33fb14 0x33fbe8 (nil) 0x33fb24)
err:urlmon:URLMonikerImpl_BindToStorage InternetCrackUrl failed: 87
fixme:shdocvw:ClOleCommandTarget_Exec (0x184594)->((null) 29 2 0x33fca0 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x184594)

```

[[IMG]http://img136.imageshack.us/img136/7267/wine01ua1.th.png[/IMG]](http://img136.imageshack.us/my.php?image=wine01ua1.png)
(here's the screenshot of Wine when this happens)

3) I rebooted into windows and try this game there. It works flawlessly

4) Rebooted into ubuntu again, and I run WireShark, captured the packet sent in and out during the connecting process to see if any connection was made after all (to see if my Wine is able to connect).

Here's where another weird thing:

The client is configured to connect to a server located at this ip (example - i cant remember exact): **72.14.122.36** on port **6900**

However, when wireshark sniffs the packet from Wine, it appears to be (this one exactly): **54.0.0.0** on port **6900**

This is indeed ODD. the ports are connected correctly, but on a totally different IP, thus makes me wonder why its not connecting at all. I run a few more internet apps and none of them connects at all.

EXCEPT

My Internet Explorer 6.0 installed via IEs4Linux.

I tried installing this game on Cedega and it gives the same result - nothing can connect.

Could someone enlighten me on where should I look?

Note:
- I'm using Ubuntu Edgy Eft 6.10 32 bit
- Wine 0.9.26 (compiled from source)

---

### Post by weetabix on 2006-12-21
I had similar error with browser while installing Sam & Max demo.
I ran regedit and searched for "gecko".
In HKEY_CURRENT_USER/Software/Wine/MSHTML there is GeckoPath and it's value tell's where the folder should be.
So I loaded wine_gecko.cab from sourceforge:
[http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=195269](http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=195269)
and unpack it with some software that supports cab -files (i used winrar which I had in my laptop, rarsoft.com).

Now my Sam & Max start fine atleast to the first screen..

Oh, using Wine 0.9.27 compiled from source and Ubuntu 6.10 (compiled kernel).

---

