---
title: "openoffice crashes in gutsy"
date: 2007-10-19
forum: General Help
---

### Post by vertexoflife on 2007-10-19
I found this: 
[http://ubuntuforums.org/showthread.php?p=3551457](http://ubuntuforums.org/showthread.php?p=3551457)

The solutions offered on that page do not help. Removing Ooo-gtk or reinstalling does not fix problems.
I had this same problems in both the Beta and RC's of Gutsy, I thought it would be fixed by now, I didn't manage to get it fixed then.

OOo locks up when I try to format a page, (adjust margins, etc) 

I am running Gutsy Gibbon 7.10 on a Toshiba Tecra laptop. Any ideas?

---

### Post by jasonlee88 on 2007-10-19
I'm accustomed to using the f11 key in firefox to go to full screen mode. So I inadvertently pressed f11 in open office (the correct shortcut is ctrl+shift+j) to go into full screen mode, and it just crashed. I tried it again and again, and each time, openoffice crashes whenever I press f11. It's not a terribly important issue, since I don't need to press f11 while in openoffice, but I thought I should report the issue anyways. Do any of you guys have this problem?

---

### Post by vertexoflife on 2007-10-20
Please, I really need to figure out what could be causing this problem. Along with this whenever I try to run applets in forefox it locks up and crashes.

---

### Post by dptxp on 2007-10-20
I have been facing one problem in open office DRAW, was in Feisty too.
I can not draw rectangles, I get only squares.:confused:

---

### Post by vertexoflife on 2007-10-20
How is it that two of the most important programs in a final release don't work?

---

### Post by talon314 on 2007-10-20
I just updated to Gutsy and, to make a long story short, installed openoffice.org from the repos. When I launch Openoffice impress, the splash screen appears and hangs. Here's the output from $openoffice -impress:

*** glibc detected *** /usr/lib/openoffice/program/soffice.bin: free(): invalid pointer: 0x0858be60 ***

Anyone else having this problem?

btw, Dell B130, 1.5 Celeron M, 1280 MB RAM.

---

### Post by Colro on 2007-10-20
My oo.org keeps crashing -- I can't open a simple powerpoint without getting stuck on a black screen once it's done importing ( [http://blackhawkit.com/c0ld/ooproblem.png](http://blackhawkit.com/c0ld/ooproblem.png) ) and whenever I try to change the general settings on writer it crashes as well. Do I need to reinstall it or something? :x

---

### Post by Colro on 2007-10-20
Update: via googleing I've discovered that it's a problem with my GTK theme, and resetting to the default "human" ubuntu theme **does** solve the problem. I've heard that there's a way to make OO.org ignore your theme via some GTK package or whatnot, but I have no clue what this is nor how to install it.

---

### Post by Colro on 2007-10-20
bump

---

### Post by DazzaL on 2007-10-20
i have the same issue.

you have only 2 options that I know of..
1. stick to a compatible theme.

2. uninstall openoffice-gtk package...this will make ooo look quite different though

---

### Post by kolinab on 2007-10-20
Pushing F11 does not crash my openoffice, what it does do is bring up the Styles and Formatting dialog. 

There are a few threads floating around regarding these recent openoffice crashes. My OO was crashing until I removed the openoffice.org-gtk package.

See my post below for links to related threads.

Good luck, let us know how things work out.

K

---

### Post by mad4dweb on 2007-10-20
I REMOVED Ooo-gtk and everything started working properly !!!
 Printing Customazing etc.

The only concecuences is that i lost my theme on office applicactions

---

### Post by kolinab on 2007-10-20
These threads keep popping up . . . 

Here are some more:

[edited, threads have been merged - thanks bapoumba]

[http://ubuntuforums.org/showthread.php?t=584088](http://ubuntuforums.org/showthread.php?t=584088)
[http://ubuntuforums.org/showthread.php?t=450008](http://ubuntuforums.org/showthread.php?t=450008)
[http://ubuntuforums.org/showthread.php?t=582152](http://ubuntuforums.org/showthread.php?t=582152) (this thread)
[http://ubuntuforums.org/showthread.php?t=583813](http://ubuntuforums.org/showthread.php?t=583813)
[http://ubuntuforums.org/showthread.php?t=563781](http://ubuntuforums.org/showthread.php?t=563781) in closed Gutsy Forum

Removing the openoffice.org-gtk package worked for me.

Good luck!

Kolin

---

### Post by FredB on 2007-10-21
No crash here, both using F11 / ctrl + shift + j

Gutsy AMD64 - cleanly installed.

---

### Post by FredB on 2007-10-21
No crash here. AMD64 Gutsy, clean install.

---

### Post by bapoumba on 2007-10-21
Merged several threads here. Thanks kolinab :)

---

### Post by texadactyl on 2007-10-21
By chance, I saw a crash log that seems to point to an incompatibility between the Gnome 2.20 (2007-09-17) glib.   

I tried the Gutsy openoffice (2.3.0-1ubuntu5) on an older Gnome and no worries.
Then, I tried openoffice with KDE 3.5 on Gutsy and no worries.

My conclusion is that openoffice either has a new bug w.r.t. to Gnome 2.20, vice versa, or its one of those unexpected ambiguities that occurs sometimes in software development.

Suggestion for 7.10 users who rely on openoffice a great deal:  Run under KDE for awhile.  Experience a new desktop manager.  When openoffice or Gnome or both are fixed, switch back to Gnome unless, of course, you have been converted.

For myself, I am going to follow my own advice for the family production machine (_not_ falling back to 7.04).  My family doesn't care between KDE and Gnome as long as things function as expected and the desktop is setup equivalently for their applications.  Makes sense to me.

-Richard

---

### Post by texadactyl on 2007-10-21
I guess that for some people removing the ooo GTK binding works and for some it doesn't.  I am assuming that everyone starts with a totally up-to-date Gnome and Ubuntu 7.10.  Still, we all tailor our 'nixes.

Anyways, I am the one who said try switching to KDE for a bit because I also had the same set of issues (crashes, freezes, etc.).  I found that all of these worked for me:

[INDENT]Downgrading Gnome to a release before 2.20 (E.g. 2.19)[/INDENT]
[INDENT]Switching to KDE 3.5[/INDENT]
[INDENT]Getting rid of the openoffice GTK binding[/INDENT]

Good luck,

Richard

---

### Post by macabro22 on 2007-10-21
Doodes!

Removing the Openoffice.org-gtk resolved my crash when printing issue as well.

Sweet.

Here's the crash  backtrace:
```
htorres@HAL9000:~$ openoffice
htorres@HAL9000:~$ *** glibc detected *** /usr/lib/openoffice/program/soffice.bin: free(): invalid pointer: 0x08e8cd70 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb6adad65]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb6ade800]
/usr/lib/libglib-2.0.so.0(g_free+0x31)[0xb63c0961]
/usr/lib/openoffice/program/libvclplug_gtk680li.so[0xb57e3d29]
/usr/lib/openoffice/program/libvcl680li.so(_ZN11SalGraphics22GetNativeControlRegionEmmRK6RegionmRK16ImplControlValueR16SalControlHandleRKN3rtl8OUStringERS0_SC_PK12OutputDevice+0x17b)[0xb7db7a8b]
/usr/lib/openoffice/program/libvcl680li.so(_ZN6Window22GetNativeControlRegionEmmRK6RegionmRK16ImplControlValueN3rtl8OUStringERS0_S8_+0x103)[0xb7e78633]
/usr/lib/openoffice/program/libvcl680li.so(_ZN7ListBox6ResizeEv+0x18c)[0xb7ec1d9c]
/usr/lib/openoffice/program/libvcl680li.so[0xb7e5ed14]
/usr/lib/openoffice/program/libvcl680li.so(_ZN6Window4ShowEht+0xca)[0xb7e614ea]
/usr/lib/openoffice/program/libvcl680li.so(_ZN7ListBoxC1EP6WindowRK5ResId+0xd6)[0xb7ec0576]
/usr/lib/openoffice/program/libsvt680li.so(_ZN18PrinterSetupDialogC1EP6Window+0x1b8)[0xb789ee38]
/usr/lib/openoffice/program/libsfx680li.so[0xb30e843f]
/usr/lib/openoffice/program/libsfx680li.so[0xb30cf878]
/usr/lib/openoffice/program/libsfx680li.so[0xb311ab4a]
/usr/lib/openoffice/program/libsfx680li.so[0xb311b2e8]
/usr/lib/openoffice/program/libsfx680li.so[0xb311b358]
/usr/lib/openoffice/program/libsfx680li.so[0xb314ace5]
/usr/lib/openoffice/program/libsfx680li.so[0xb314ac89]
/usr/lib/openoffice/program/libvcl680li.so[0xb7e72e66]
/usr/lib/openoffice/program/libvclplug_gen680li.so(_ZN10SalDisplay21DispatchInternalEventEv+0xbc)[0xb53c416c]
/usr/lib/openoffice/program/libvclplug_gtk680li.so[0xb57c3041]
/usr/lib/openoffice/program/libvclplug_gtk680li.so[0xb57c3081]
/usr/lib/libglib-2.0.so.0[0xb63b7551]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x17c)[0xb63b911c]
/usr/lib/libglib-2.0.so.0[0xb63bc55f]
/usr/lib/libglib-2.0.so.0(g_main_context_iteration+0x65)[0xb63bcac5]
/usr/lib/openoffice/program/libvclplug_gtk680li.so[0xb57c5171]
/usr/lib/openoffice/program/libvclplug_gen680li.so(_ZN14X11SalInstance5YieldEbb+0x37)[0xb53cb927]
/usr/lib/openoffice/program/libvcl680li.so(_ZN11Application5YieldEb+0x59)[0xb7c72559]
/usr/lib/openoffice/program/libvcl680li.so(_ZN11Application7ExecuteEv+0x3c)[0xb7c7267c]
/usr/lib/openoffice/program/soffice.bin(_ZN7desktop7Desktop4MainEv+0x145d)[0x806f07d]
/usr/lib/openoffice/program/libvcl680li.so[0xb7c7834c]
/usr/lib/openoffice/program/libvcl680li.so(_Z6SVMainv+0x35)[0xb7c78455]
/usr/lib/openoffice/program/soffice.bin(main+0xcf)[0x806150f]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb6a87050]
/usr/lib/openoffice/program/soffice.bin(_ZN6Window15SetPosSizePixelEllllt+0x365)[0x80613d1]
======= Memory map: ========
08048000-0809d000 r-xp 00000000 08:05 1031586    /usr/lib/openoffice/program/soffice.bin
0809d000-0809e000 rw-p 00054000 08:05 1031586    /usr/lib/openoffice/program/soffice.bin
0809e000-08eb0000 rw-p 0809e000 00:00 0          [heap]
aca00000-aca21000 rw-p aca00000 00:00 0 
aca21000-acb00000 ---p aca21000 00:00 0 
acbb7000-accaa000 r--p 00000000 08:05 1032578    /usr/lib/openoffice/help/en/scalc.ht
accaa000-acda9000 r--p 00000000 08:05 1032577    /usr/lib/openoffice/help/en/scalc.db
acda9000-acddc000 r-xp 00000000 08:05 326264     /usr/lib/libxslt.so.1.1.21
acddc000-acddd000 rw-p 00032000 08:05 326264     /usr/lib/libxslt.so.1.1.21
acddd000-acef7000 r-xp 00000000 08:05 976209     /usr/lib/libdb-4.5.so
acef7000-acefa000 rw-p 0011a000 08:05 976209     /usr/lib/libdb-4.5.so
acefb000-acf15000 r-xp 00000000 08:05 1038257    /usr/lib/openoffice/program/svtmisc.uno.so
acf15000-acf17000 rw-p 00019000 08:05 1038257    /usr/lib/openoffice/program/svtmisc.uno.so
acf17000-acf76000 r-xp 00000000 08:05 1038267    /usr/lib/openoffice/program/libucpchelp1.so
acf76000-acf78000 rw-p 0005f000 08:05 1038267    /usr/lib/openoffice/program/libucpchelp1.so
acf78000-ad1b9000 rw-p acf78000 00:00 0 
ad1b9000-ad1ef000 r-xp 00000000 08:05 976389     /usr/lib/libhunspell-1.1.so.0.0.0
ad1ef000-ad1f3000 rw-p 00036000 08:05 976389     /usr/lib/libhunspell-1.1.so.0.0.0
ad207000-ad20f000 r-xp 00000000 08:05 1038233    /usr/lib/openoffice/program/libmcnttype.so
ad20f000-ad210000 rw-p 00008000 08:05 1038233    /usr/lib/openoffice/program/libmcnttype.so
ad210000-ad21e000 r-xp 00000000 08:05 1037179    /usr/lib/openoffice/program/libspell680li.so
ad21e000-ad21f000 rw-p 0000e000 08:05 1037179    /usr/lib/openoffice/program/libspell680li.so
ad21f000-ad23c000 r-xp 00000000 08:05 1038253    /usr/lib/openoffice/program/libsrtrs1.so
ad23c000-ad23d000 rw-p 0001d000 08:05 1038253    /usr/lib/openoffice/program/libsrtrs1.so
ad23d000-ad253000 r-xp 00000000 08:05 1037315    /usr/lib/openoffice/program/basprov680li.uno.so
ad253000-ad255000 rw-p 00015000 08:05 1037315    /usr/lib/openoffice/program/basprov680li.uno.so
ad255000-ad25c000 r-xp 00000000 08:05 1038240    /usr/lib/openoffice/program/proxyfac.uno.so
ad25c000-ad25d000 rw-p 00006000 08:05 1038240    /usr/lib/openoffice/program/proxyfac.uno.so
ad25d000-ad2a3000 r-xp 00000000 08:05 1038273    /usr/lib/openoffice/program/ucptdoc1.uno.so
ad2a3000-ad2a6000 rw-p 00045000 08:05 1038273    /usr/lib/openoffice/program/ucptdoc1.uno.so
ad2a6000-ad2e0000 r-xp 00000000 08:05 1038249    /usr/lib/openoffice/program/libscriptframe.so
ad2e0000-ad2e2000 rw-p 00039000 08:05 1038249    /usr/lib/openoffice/program/libscriptframe.so
ad2e2000-ad302000 r-xp 00000000 08:05 1037762    /usr/lib/openoffice/program/fsstorage.uno.so
ad302000-ad304000 rw-p 0001f000 08:05 1037762    /usr/lib/openoffice/program/fsstorage.uno.so
ad304000-ad322000 r-xp 00000000 08:05 1037326    /usr/lib/openoffice/program/reflection.uno.so

```

---

### Post by vertexoflife on 2007-10-21
Uninstalling openoffice-gtk makes it so that Openoffice does not have borders and will cover both taskbars.

EDIT: Nevermind, this workaround works if Legacy Fullscreen Support is disabled in the 'Workarounds' Section of CCSM (CompizConfig-settings-manager)

---

### Post by carstanje on 2007-11-21
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/131526](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/131526) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
Can you try using a different GTK theme like the basic Human theme? Some themes are incomplete and this will cause openoffice to crash. This is a [known bug]("https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/131526") for openoffice but there is no workaround yet.

---

### Post by woodsby on 2007-11-24
> **carstanje said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/131526](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/131526) [br].[/br] ---------------------------- [br].[/br].

I used the temporary updates listed on that bug report.  Just add:

deb [http://ppa.launchpad.net/blueyed/ubuntu](http://ppa.launchpad.net/blueyed/ubuntu) gutsy main

to your list of sources and check for updates.  I haven't fully tested this yet, but it appears to work fine through all the things that were making it crash before.  I prefer to keep my darker themes...

---

### Post by Jiawen on 2007-12-16
Doing that just gives a bunch on UNAUTHORIZED updates to packages having nothing to do with Openoffice. How do you actually get the OOo updates?

---

### Post by macabro22 on 2007-12-16
I would suggest using emerald-theme manager.

That solved all my problems. There are really nice themes for emerald, with transparency and all.

Cheers

---

### Post by Jiawen on 2007-12-16
You mean, emerald + compiz? There's apparently some *other* bug that causes compiz + emerald under Xfce to not give window borders or show taskbars when a full-screen app is showing. In other words, I have to close Firefox entirely to get at any other program. Bug after bug.

If there's a way of using emerald without compiz, please tell me! Or if there's a way to actually get compiz + emerald working under Xfce, I'd love to know that, too.

---

### Post by macabro22 on 2007-12-16
> **Jiawen said:**
> You mean, emerald + compiz? There's apparently some *other* bug that causes compiz + emerald under Xfce to not give window borders or show taskbars when a full-screen app is showing. In other words, I have to close Firefox entirely to get at any other program. Bug after bug.

If there's a way of using emerald without compiz, please tell me! Or if there's a way to actually get compiz + emerald working under Xfce, I'd love to know that, too.

Hmm, I don't have those issues in gnome. Maybe there's a workaround I don't know of.

Try asking the experts on the #compiz-fusion channel at irc.freenode.net.

They are always very helpfull, particulally  crdlb, amphi and Scottdoker

---

### Post by Jiawen on 2007-12-17
The bugs in compiz-fusion go quite a bit deeper than I had previously thought. Just getting compiz installed and running is a very complicated task -- there are several different people's formulations of it, all mutually exclusive, and apparently there are also issues with Nvidia graphics cards (which I have), and other things that cause compiz to crash as it starts. I really don't have the energy to bang my head against a big tree just to avoid banging my head against a small tree.

I guess I'll just have to hope that someone comes up with a bugfix for Openoffice that I can actually apply somehow. :(

---

### Post by macabro22 on 2007-12-17
Actually Ooffice calc just crashes when I try to sum a rom with a sum function.

I will try uninstalling the gtk package and see if the problem is solved.

---

### Post by Jiawen on 2007-12-23
Has anyone had any success? It's getting really frustrating having to kill OO.o every few minutes and restart. :(

The bug tracking page carstanje linked to describes some bugfixes, but I see no way to install or enable them. (Yes, I have the Proposed repository enabled, but when I look in Synaptic, the only OO.o available is the one I already have.)

Someone please help! This is getting to be a huge headache.

---

### Post by macabro22 on 2007-12-24
Nope.
Didn't work.

---

