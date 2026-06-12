---
title: "Boot repair disk not worked. “Select proper boot device”.HDD: UB 14.10, 15.04 &amp; XP"
date: 2017-10-23
forum: General Help
---

### Post by greenewbie on 2017-10-23
An HDD developed this bootup problem nearly 2 years ago. Resolving the problem, despite the lapse of time, is still very important to me, to recover some data on it before I do a fresh installation.

My machine says in the BIOS that it’s present and that its status is OK (PS it’s “SMART”-enabled, whatever that means!); BIOS also correctly reads its 360GB capacity. Instead of loading up the normal GRUB bootup menu (ie listing Ubuntu & Windows versions to choose from), all that eventually appears is this message on a black screen:

[COLOR=#000080]“**Rebootand select proper boot device or insert boot media in selected bootdevice and press a key”**[/COLOR] 

[FONT=Liberation Serif]I tried to fix the problem on numerous occasions when it happened but nothing I’ve done so far has worked. In my BIOS menu, pressing F11 to select my HDD manually hasn’t made any difference. The disk diagnosis checks I’ve done so far have said that there are either no faults on it at all, or just one file which is faulty. I’ve seen, during sessions on live USB sticks, that all my stuff is apparently still there: indeed I’ve been able to open some files &pictures but not yet on my master account I want to access. You’ll see from the boot reports below that the HDD has multiple OSs [COLOR=#ff0000](UB 14.10, 15.04 &XP)[/COLOR] which is no doubt hugely complicating the matter . From what I can understand the boot (¿the “Grub2” I believe?) is installed in [COLOR=#ff0000]**sda1**[/COLOR], the partition I have [COLOR=#ff0000]**XP**[/COLOR] on. Although it would be potentially useful to me to keep that partition (I just use Windows sometimes to test an accessory I’m having problems with on Ubuntu), my priority by far is to solve this bootup problem as quickly as possible. So if you guys think that (especially in my case, as I am still alas VERY technically unaware), I would be best off trying to delete the XP partition first, then I’d do just that. In which case, I imagine I could do this by using the OS uninstaller I’ve seen in live sessions?[/FONT]
[LEFT]
[COLOR=#00000a]I suspect now that the following complication is the crux of the problem: I [/COLOR]**[COLOR=#00000a][FONT=Liberation Serif]used[/FONT][/COLOR]**[COLOR=#00000a][FONT=Liberation Serif] to use the above HDD on a [/FONT][/COLOR]**[COLOR=#00000a][FONT=Liberation Serif]32-bit[/FONT][/COLOR]**[COLOR=#00000a][FONT=Liberation Serif] PC(NB which went wrong not long after the above bootup problem appeared: all this PC does now is make a beeping alarm sound when I turn it on!). My “new” [/FONT][/COLOR]**[COLOR=#00000a][FONT=Liberation Serif]64-bit [/FONT][/COLOR]**[COLOR=#00000a][FONT=Liberation Serif]machine [/FONT][/COLOR]**[COLOR=#00000a][FONT=Liberation Serif]never[/FONT][/COLOR]**[COLOR=#00000a][FONT=Liberation Serif] had XP on it before (although it used to have Vista on a different HDD),so I wonder if dear Microsoft is putting a spanner in the works?!! [IMG]https://ubuntuforums.org/image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABAAAAAVCAMAAAB44J7gAAABtlBMVEUAAAARFRsRGBkoKisoMjc2Njs6Oj4ePHswPUI7O0AlRlQ8VFY3Z3xERElMTFBBUlZEVGdFVWxGXWFkcHspTpolTKYqUbMrU7s3W6c2YoU0Ys87aOBDepBIfZBFcL9OfrVRcKZec6Nfd7NjcYhYdcNSf ZrgYthlZdqm51xmZtlhrJlmaB8o7t6qb53tbV7ubtPit9TiMJYiM9VhNJOg/RTg/lWj/dbi/1flP9lgMVgmcFwiMZgk/9gnfxho8BppsFmpddkoNlooNJnstlruNlwqtVpoP95u J4uOl2tP94tvt6vP97w V/wv9 zvGIiI Tk5qYmJ bm6OMr7 AtreDtbiep6 ZpL2kqbGoqLCor76isb2KtcmPuc6Uo8eWptGsuNm8vMS/v8iHwsKJwsKJ0t SxceQxsqcycuCxv Fy/ G2P K1PaK1P N2v2T4v W6v a7/ c8f 0zN28y9em7Oys6Omk/P r// z// 68/S6///Av8fJy9PLz9zb2 TB8fLE///L///W4Ove4PDT///c///l5e7m6vXr6vTt7vjg///v8Prw7/n09P78A/sAAAD///9x9w7uAAAAkHRSTlP//////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////wADZeeHAAABMklEQVR4nGPo76/n5G1vZwXj v5 hv5 /65OtqC Tr6grk5msEB/PydQhhWKQQKJgUAc0N8fFdQPEYhMBAoAcVANVKCzr7 vrravv7cPKtDfrGPl4GSoVdcPEejTcc4uKMzP8zZQ6AIJ9Nn5lVdXVlZUVOTZSvQBBWL9yitDyxobS/UKc82U hk6XIqq0xj429qEGPTLvaVaGIqBGhozGlqbqtIrCjNN4hlicoACra1NQFBZmGVjyaCbU17Z2tbd3dbaVF2UZaPCEOxTVKnJz8rCwsqtnp9pas1QYpefyqShl5Ksr83o6imdwNAl455fXg10SGV5vre5WCdDf7SMR25efn5 bqanuXgcyOlqPE6e3pnenm6qoooQz4Vx8cgbGcuJsIfDfNsZISwgqBzVCWIDAB 6g3BLN5S4AAAAAElFTkSuQmCC[/IMG] I also don’t know if it’s relevant to mention that my problem HDD is the older-type IDE / ATA and the motherboard on my “new”machine is designed to use SATAII HDDs (having said that, I’m able to use another functioning IDE HDD on this machine with no problem [IMG]https://ubuntuforums.org/image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAA8AAAAPCAMAAAAMCGV4AAAAMFBMVEUAAAAzMzNFRUX nQD/tAD/ywD/5QD/6gD//RP//pP//8f// v////8A/sAAAD///8AljErAAAADnRSTlP/////////////////AEXA3MgAAABlSURBVHicVY9BEsAgCAMRpait//9uSdDOdE9uMgrKAgp4Eto9xzAm4WG9u7tVhescIqEiCMIHSmLhOkPZ84awPt7g/kHvXrYWusXLG9xfCB4gZpxndmWb8xEkuR/2b0E9 // 9wLDvQWnkfau2QAAAABJRU5ErkJggg==[/IMG]).[/FONT][/COLOR][/LEFT]

Here’s the URL for the last boot repair I tried using a **16.04.3-amd64 **live USB stick on my “new” machine:
[COLOR=#000080]_[http://paste.ubuntu.com/25796472/](http://paste.ubuntu.com/25796472/)_[/COLOR]

As instructed in Ubuntu help notes, I opened Terminal in this live session to enter the boot repair commands [COLOR=#ff3333]**(I’ve highlighted in red)**[/COLOR].  You can see these and the results I’ve pasted into the document attached below.

PS I tried Yannbuntu’s boot repair on several occasions. I’m pasting below the URLs of two reports, just in case there is something important that doesn’t appear in the one above.

**After USB key 32-bit Boot Repair:**
_[http://paste.ubuntu.com/25747045/](http://paste.ubuntu.com/25747045/)_


**After USB key 64-bit Boot Repair:**
_[http://paste.ubuntu.com/25784631/]("http://paste.ubuntu.com/25774196/")_

Many thanks in advance for any help...but please try to bear in mind that I’m a tech-dummy!! :)

---

### Post by oldfred on 2017-10-23
You show encrypted swap in sda5, that is why it shows errors on that partition as it cannot see it since encrypted.
But that indicates you have encrypted /home in install in sda6. You need that passphase to be able to mount your /home folders in each install. 
You second install seems to be mounting same swap but not encrypted? That could be part of issue.

But installs are both totally obsolete and now difficult to repair. If you want an install you do not have to regularly update you should use the LTS - long term support versions like 14.04 or 16.04 LTS.

You also have a very old nVidia card. Is it working with the nouveau open source driver? Or do you need nomodeset boot parameter?

Since now old system, you may need one of the lightweight flavors of Ubuntu.
       Lightweight flavors
Lubuntu, xubuntu, Ubuntu mate, Budgie
[https://wiki.ubuntu.com/UbuntuFlavors](https://wiki.ubuntu.com/UbuntuFlavors)

---

