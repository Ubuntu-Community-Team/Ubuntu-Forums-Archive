---
title: "Windows 98 feedback"
date: 2007-07-11
forum: General Help
---

### Post by ago on 2007-07-11
If you happen to have windows 98 could you please test Wubi? In particular we are interested to know whether the uninstaller works well and config.sys is restored to its previous state.

Thx

---

### Post by acowboydave on 2007-07-12
ago, had an old gateway with a fresh 98se install so tried Wubi 7.04.02 with Xubuntu ISO this is as far as I got. Hope this helps.[ATTACH]37962[/ATTACH]

[ATTACH]37963[/ATTACH]

---

### Post by CrazyGuy123 on 2007-07-13
Same result as reported on Win 95 a few weeks back.

---

### Post by ago on 2007-07-13
I talked to Hampus (metadl author), this is an issue that has to do with the use of libcurl inside metadl.

There are 3 solutions:

1 We drop windows 98 support and stick with current downloader
2 We use another downloader (e.g. aria2 or download catalyst)
3 We fix the current the current downloader replacing libcurl calls with something like WinInet

#2 requires wrapping up the new downloader for nsis (the metdal wrapper code can be reused), the advantage is that both aria2 and download catalyst already support segmented downloads (much faster) and even bittorrent. Aria2 seems the better candidate, but it is uncertain how stable it is under windows. A segmented downloader (possibly with bittorrent support) will be the long term solution anyway, so this road brings Gutsy, and it's a road we need to walk quite soon... 

#3 should be more straightforward, I am not sure though whether Hampus will have time to do it.

I will have little spare time in the coming days, and in the time I have, I really need to work porting lupin to Ubuntu 7.10 which is more important at the moment. So if someone wants to have a go with 2 or 3, it would be much appreciated and I will postpone the final release, otherwise we will drop windows 98 support for the time being.

---

### Post by willemijns on 2007-07-13
> **ago said:**
> 
1 We drop windows 98 support and stick with current downloader

Win9x support is dead since one year...

---

### Post by ago on 2007-07-13
If anything users of MS unsupported OSes are important "clients" of ours, since such users _have_ to upgrade to something else anyway...

---

### Post by CrazyGuy123 on 2007-07-13
How about taking the middle road:

Drop auto-downloader support in Win 9x, but instead give the user a direct download link, and get them to download the file manually and re-run the installer.  Thats a bit of an inconvienience for the user, but is MUCH better than saying there's no support at all.

metadl may still be able to do it's crc checks with little modification to not require libcurl to load the dll plugin (only load libcurl when a download is required).  Alternatively, there could simply be no checks on the downloaded file on win 9x systems, although that might be too big a gamble to take, even though not many users will take that path.

---

### Post by antini on 2007-07-13
> **CrazyGuy123 said:**
> How about taking the middle road:

Drop auto-downloader support in Win 9x, but instead give the user a direct download link, and get them to download the file manually and re-run the installer.  Thats a bit of an inconvienience for the user, but is MUCH better than saying there's no support at all.

metadl may still be able to do it's crc checks with little modification to not require libcurl to load the dll plugin (only load libcurl when a download is required).  Alternatively, there could simply be no checks on the downloaded file on win 9x systems, although that might be too big a gamble to take, even though not many users will take that path.

That's a good idea. Since it's using .metalinks anyway, those on 9x systems could just use another metalink downloader (one of the download managers that runs on 9x, not sure which still do) to get the ISO. DownThemAll! is about a 350k Firefox extension and supports segmented downloads and mirror use.

It wouldn't be as convenient for users as doing everything in Wubi, so I'm not sure if that's an ok tradeoff with doing less coding to make it work for 9x people.

---

### Post by shtewe on 2007-07-13
HAHA

silly illeagl operation, i remember these days and i never understood why?

STUPID WINDOWS!

---

### Post by ago on 2007-07-14
Ok, I have disabled metadl in windows 98. You will have to download manually and if the file is not there you get a warning. Please test it out, possibly through a complete install/uninstall cycle.

[http://cutlersoftware.com/ubuntusetup/devel/minefield/Wubi-7.04-minefield-231.72.exe](http://cutlersoftware.com/ubuntusetup/devel/minefield/Wubi-7.04-minefield-231.72.exe)

---

### Post by ago on 2007-07-14
I added it to rc4. that will make the final, so I need some feedback beforehand, since I have no win98 to test with.

---

### Post by acowboydave on 2007-07-14
Ago, had another computer a compaq 7360 and reinstalled 98SE on it. Ran scandisk and defrag on it just to make right. Got to the restart and reboot, entered Ubuntu, screen went black and windows 98 flashed on screen for a second then went black with the flashing cursor. It looked good till it came to no raid disks, but that is normal for me at least, but it just freezes there. Used all the ctrl+alt+delete, and crtl+alt+backspace  so on. Had to just turn it off. Tried it one more time same thing. Back in windows again I tried the uninstall it worked but it did not save the ISO file, plus it also left the boot loader in place on start up. I have never used the automatic download and just downloaded the ISO file from one of the mirrors with a download manager which work on 9x, and then downloaded Wubi to the same folder. Note used Xubuntu thinking it might be lighter.:neutral:

---

### Post by ago on 2007-07-15
Remove "quiet splash" from c:\wubi\boot\grub\menu.lst and try to have a look at the logs in /tmp.
What did you do exactly to uninstall? It's strange that the ISO was not backed up, was the box checked?

I'll need some external help here since I have no win98 and am coding blind.

---

### Post by ago on 2007-07-15
If you have windows 98 drop me a PM and we'll do this online over a chat (jabber).

---

### Post by acowboydave on 2007-07-15
Hello, will send you a PM, I must add that I did have the save ISO checked but unchecked the save the virtual disk setup didn't need to do that since it never got that far. Note: cnet downloads is still on Wubi 7.04.01 and lists 98/nt/ as requirements. Point to ponder some of the failures could be 9x related

---

### Post by ago on 2007-07-15
If the chaps of download.com do not come here to ask for support it is difficult for me to help out. But win 98 might be a reason for the troubles some have been experiencing.

---

### Post by acowboydave on 2007-07-15
Here is what I am facing.[ATTACH]38268[/ATTACH]

[ATTACH]38270[/ATTACH]

---

### Post by ago on 2007-07-15
Hmm not much I can make up there... You may want to do a fresh installation and remove "quiet splash" from c:\wubi\boot\grub\menu.lst before rebooting.

---

### Post by acowboydave on 2007-07-16
Ago, this is far as I am getting on the compaq 98SE. Have reinstalled again win. and did run a thorough scandisk, that took 9hrs. New download of edubuntu, and xubuntu. Used minefield 231.72. Forgot to add that both installs stop at the same place.

---

