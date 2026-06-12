---
title: "Mad at ubuntu, unstable, no undo, suddenly nomore sound in Steamgames"
date: 2007-09-13
forum: General Help
---

### Post by thegreatbeste on 2007-09-13
Hi there.
I am running Feisty on a Sony Vaio FS315h

Ubuntu install went very well, wine install, steam install also, works right out of the box.
ALC260 soundchip in my notebook.
Cant hear sounds from two programs i.e. Teamspeak and CounterStrike.
Workarounds for esd, alsa, oss, jack, whatsoever, no idea, ten workarounds, none working. Suddenly no sound in Steamgames at all.
Winecfg started the first time, automatically selects a driver, set to emulation, still no sound.
Suddenly winecfg asks me, that the esd driver is not needed and if it can be deleted.
Said no, however still no sound.
Selcted everything, tried every config, dunno anymore, crackling sound, still no two sound sources at the same time, game horribly slow with crackling sound, great.
Uninstall Wine package, rm -rf ~/.wine/
Reinstall wine, reinstall steam, everything is fine, no winecfg used.
suddenly 9 out of 10 times, wine says registry in use by another program, none running, wondering, google => workaround => add shortcuts.dat to steam folder.
Did it now 10 out of 10 times wine says registry in use, pissed.
Uninstall wine, rm -rf ~/.wine/
Reinstall wine, reinstall Steam, no sound at all. **** you Linux
Also:
Microsoft Intelli Optical mouse 5 buttons plus wheel, istalled imwheel, configured X11, did workaround, now sidebuttons work but my mousewheel does "go back one page" and "go forward one page" on mwheel up and mwheel down.

Is there any way to load a system backup that recreates the state of Linux before you helplessly misconfigured your system?
I'd apreciate that so i did not have to reinstall the whole OS to get my games running with my spare knowledge of linux.

Please dont tell me what i could have done, im just too pissed right now to do any kind of Work around.
It took me two hours of my free time just to get to know that i most obviously did something wrong. Two goddam hours i wanted to relax and play my game, so please no try this try that try tralala, except for a system backup recovery tool.
So that i dont have to bleed all the time i stumble across my own mistakes.

---

### Post by dpar on 2007-09-13
If for some odd reason I want to run windows programs, I use Windows. Thats why I duel boot.
But then thats just me:biggrin:

---

### Post by init1 on 2007-09-13
> **thegreatbeste said:**
> Hi there.
I am running Feisty on a Sony Vaio FS315h

Ubuntu install went very well, wine install, steam install also, works right out of the box.
ALC260 soundchip in my notebook.
Cant hear sounds from two programs i.e. Teamspeak and CounterStrike.
Workarounds for esd, alsa, oss, jack, whatsoever, no idea, ten workarounds, none working. Suddenly no sound in Steamgames at all.
Winecfg started the first time, automatically selects a driver, set to emulation, still no sound.
Suddenly winecfg asks me, that the esd driver is not needed and if it can be deleted.
Said no, however still no sound.
Selcted everything, tried every config, dunno anymore, crackling sound, still no two sound sources at the same time, game horribly slow with crackling sound, great.
Uninstall Wine package, rm -rf ~/.wine/
Reinstall wine, reinstall steam, everything is fine, no winecfg used.
suddenly 9 out of 10 times, wine says registry in use by another program, none running, wondering, google => workaround => add shortcuts.dat to steam folder.
Did it now 10 out of 10 times wine says registry in use, pissed.
Uninstall wine, rm -rf ~/.wine/
Reinstall wine, reinstall Steam, no sound at all. **** you Linux
Also:
Microsoft Intelli Optical mouse 5 buttons plus wheel, istalled imwheel, configured X11, did workaround, now sidebuttons work but my mousewheel does "go back one page" and "go forward one page" on mwheel up and mwheel down.

Is there any way to load a system backup that recreates the state of Linux before you helplessly misconfigured your system?
I'd apreciate that so i did not have to reinstall the whole OS to get my games running with my spare knowledge of linux.

Please dont tell me what i could have done, im just too pissed right now to do any kind of Work around.
It took me two hours of my free time just to get to know that i most obviously did something wrong. Two goddam hours i wanted to relax and play my game, so please no try this try that try tralala, except for a system backup recovery tool.
So that i dont have to bleed all the time i stumble across my own mistakes.

Don't expect to get games running in Linux. If they work, great, but it is not common. If you want to go back to another state, backup your important files, and then reinstall. For next time, make images of your partition with partimage.
```

apt-get install partimage

```
Linux takes time and patience. It won't always work the way you want it to.

---

### Post by dhobbs on 2007-09-13
I would say that you're out of luck.

It sounds like system recovery tools are in initial stages of development (are they even more than a thought yet?) and from what I have found online there isn't any way to restore a system unless you personally backed everything up before you tried to install everything (if you could, then I want to know about this black magic).

You've got to enter into a new mindset if you're going to successfully run Linux. That is, if you break it, you're lucky because now you get to fix it.  Besides, most everything is recoverable in Linux because there are very few (if any) programs that are trying to maliciously infect/remain on your system when they are removed.

If you want to fix things I would recommend uninstalling wine entirely and starting over from scratch and doing a little more homework before rampaging into the world of wine and windows compatibility.  I believe wine uses OSS a lot which only allows one program to use the sound card (ALSA allows multiple devices to access the card).  You should look into using [[COLOR="Blue"]aoss[/COLOR]]("http://linux.die.net/man/1/aoss") to wrap those OSS games in ALSA.

Be patient and let the community help you without the anger or attitude please.

---

### Post by jfinkels on 2007-09-13
Yes, use partimage.

Remember that there was/is no assurance that a Windows program such as Steam or Counterstrike will work on a Linux computer. wine is an application layer that essentially makes an attempt to translate Windows function calls to Linux function calls. Petition valve to make their games available on Linux!

---

### Post by thegreatbeste on 2007-09-14
The funny thing is that after the third time i reinstall wine from scratch it behaves different.
While after the first and second time everything was fine, why doesn't it work for the third time?
Sure i can fix it but in the evening getting home from work i simply want to use my computer and not repair it. So it would be very nice if there was a piece of software that simply remembers all the commands u did and that can make them undone. 
To set your computer back into a working state.

---

