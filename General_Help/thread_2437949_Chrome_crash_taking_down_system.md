---
title: "Chrome crash taking down system"
date: 2020-03-03
forum: General Help
---

### Post by steve234 on 2020-03-03
Hi guys,

I recently let my OS (LUBUNTU 18.04.4 LTS - i3WM is my DM) update (I know, why ever would someone update a working system). I now have a problem where, when I use OnShape web (a CAD app) Chrome goes down if I do anything taxing, and often takes the system with it. 

**Edit, I've since reproduced the system going down in Chrome x2, and once in Firefox - Both were irritrievable hangs with only the mouse working**.

Luckily this time Chrome went down, without taking the systems with it. My dmesg log doesn't seem to be giving much away:

```
 583.634299] nouveau 0000:01:00.0: chromium-browse[2914]: nv50cal_space: -16[  584.027216] nouveau 0000:01:00.0: gr: DATA_ERROR 0000000d [BEGIN_END_ACTIVE]
[  584.027221] nouveau 0000:01:00.0: gr: 00100000 [] ch 6 [001f857000 chromium-browse[2914]] subc 3 class 8597 mthd 12e4 data 00000000
[  584.027239] nouveau 0000:01:00.0: gr: DATA_ERROR 0000000d [BEGIN_END_ACTIVE]
[  584.027241] nouveau 0000:01:00.0: gr: 00100000 [] ch 6 [001f857000 chromium-browse[2914]] subc 3 class 8597 mthd 1360 data 00000000
[  584.027250] nouveau 0000:01:00.0: gr: DATA_ERROR 0000000d [BEGIN_END_ACTIVE]
[  584.027252] nouveau 0000:01:00.0: gr: 00100000 [] ch 6 [001f857000 chromium-browse[2914]] subc 3 class 8597 mthd 19c4 data 00000000
[  584.027265] nouveau 0000:01:00.0: gr: DATA_ERROR 0000000d [BEGIN_END_ACTIVE]
[  584.027267] nouveau 0000:01:00.0: gr: 00100000 [] ch 6 [001f857000 chromium-browse[2914]] subc 3 class 8597 mthd 1a00 data 00001111
[  584.027279] nouveau 0000:01:00.0: gr: DATA_ERROR 0000000d [BEGIN_END_ACTIVE]
[  584.027281] nouveau 0000:01:00.0: gr: 00100000 [] ch 6 [001f857000 chromium-browse[2914]] subc 3 class 8597 mthd 12e8 data 00000000
[  584.027291] nouveau 0000:01:00.0: gr: DATA_ERROR 0000000d [BEGIN_END_ACTIVE]
[  584.027293] nouveau 0000:01:00.0: gr: 00100000 [] ch 6 [001f857000 chromium-browse[2914]] subc 3 class 8597 mthd 12cc data 00000000
[  584.027304] nouveau 0000:01:00.0: gr: DATA_ERROR 0000000d [BEGIN_END_ACTIVE]
[  584.027306] nouveau 0000:01:00.0: gr: 00100000 [] ch 6 [001f857000 chromium-browse[2914]] subc 3 class 8597 mthd 19bc data 00000000
[  584.027316] nouveau 0000:01:00.0: gr: DATA_ERROR 0000000d [BEGIN_END_ACTIVE]
[  584.027318] nouveau 0000:01:00.0: gr: 00100000 [] ch 6 [001f857000 chromium-browse[2914]] subc 3 class 8597 mthd 1380 data 00000000
[  584.027328] nouveau 0000:01:00.0: gr: DATA_ERROR 0000000d [BEGIN_END_ACTIVE]
[  584.027330] nouveau 0000:01:00.0: gr: 00100000 [] ch 6 [001f857000 chromium-browse[2914]] subc 3 class 8597 mthd 1594 data 00000000
[  584.027339] nouveau 0000:01:00.0: gr: DATA_ERROR 0000000d [BEGIN_END_ACTIVE]
[  584.027342] nouveau 0000:01:00.0: gr: 00100000 [] ch 6 [001f857000 chromium-browse[2914]] subc 3 class 8597 mthd 12ec data 00000000
[  584.027351] nouveau 0000:01:00.0: gr: DATA_ERROR 0000000d [BEGIN_END_ACTIVE]
[  584.027353] nouveau 0000:01:00.0: gr: 00100000 [] ch 6 [001f857000 chromium-browse[2914]] subc 3 class 8597 mthd 12d4 data 00001d01
[  584.027362] nouveau 0000:01:00.0: gr: DATA_ERROR 0000000d [BEGIN_END_ACTIVE]
[  584.027364] nouveau 0000:01:00.0: gr: 00100000 [] ch 6 [001f857000 chromium-browse[2914]] subc 3 class 8597 mthd 1688 data 00000000
[  584.027373] nouveau 0000:01:00.0: gr: DATA_ERROR 0000000d [BEGIN_END_ACTIVE]
[  584.027375] nouveau 0000:01:00.0: gr: 00100000 [] ch 6 [001f857000 chromium-browse[2914]] subc 3 class 8597 mthd 1534 data 00000000
[  584.027384] nouveau 0000:01:00.0: gr: DATA_ERROR 0000000d [BEGIN_END_ACTIVE]
[  584.027386] nouveau 0000:01:00.0: gr: 00100000 [] ch 6 [001f857000 chromium-browse[2914]] subc 3 class 8597 mthd 13b0 data 00000000
[  584.027395] nouveau 0000:01:00.0: gr: DATA_ERROR 0000000d [BEGIN_END_ACTIVE]
[  584.027397] nouveau 0000:01:00.0: gr: 00100000 [] ch 6 [001f857000 chromium-browse[2914]] subc 3 class 8597 mthd 1570 data 00000000
[  584.027406] nouveau 0000:01:00.0: gr: DATA_ERROR 0000000d [BEGIN_END_ACTIVE]
[  584.027408] nouveau 0000:01:00.0: gr: 00100000 [] ch 6 [001f857000 chromium-browse[2914]] subc 3 class 8597 mthd 166c data 00000000
[  584.027417] nouveau 0000:01:00.0: gr: DATA_ERROR 0000000d [BEGIN_END_ACTIVE]
[  584.027419] nouveau 0000:01:00.0: gr: 00100000 [] ch 6 [001f857000 chromium-browse[2914]] subc 3 class 8597 mthd 1518 data 00000000
[  584.027428] nouveau 0000:01:00.0: gr: DATA_ERROR 0000000d [BEGIN_END_ACTIVE]
[  584.027430] nouveau 0000:01:00.0: gr: 00100000 [] ch 6 [001f857000 chromium-browse[2914]] subc 3 class 8597 mthd 1520 data 00000000
[  584.027439] nouveau 0000:01:00.0: gr: DATA_ERROR 0000000d [BEGIN_END_ACTIVE]
[  584.027441] nouveau 0000:01:00.0: gr: 00100000 [] ch 6 [001f857000 chromium-browse[2914]] subc 3 class 8597 mthd 1658 data 00000000
[  584.027450] nouveau 0000:01:00.0: gr: DATA_ERROR 0000000d [BEGIN_END_ACTIVE]
[  584.027452] nouveau 0000:01:00.0: gr: 00100000 [] ch 6 [001f857000 chromium-browse[2914]] subc 3 class 8597 mthd 0dac data 00001b02
[  584.027461] nouveau 0000:01:00.0: gr: DATA_ERROR 0000000d [BEGIN_END_ACTIVE]
[  584.027463] nouveau 0000:01:00.0: gr: 00100000 [] ch 6 [001f857000 chromium-browse[2914]] subc 3 class 8597 mthd 0db0 data 00001b02
[  584.027472] nouveau 0000:01:00.0: gr: DATA_ERROR 0000000d [BEGIN_END_ACTIVE]
[  584.027474] nouveau 0000:01:00.0: gr: 00100000 [] ch 6 [001f857000 chromium-browse[2914]] subc 3 class 8597 mthd 0db4 data 00000000
[  584.027483] nouveau 0000:01:00.0: gr: DATA_ERROR 0000000d [BEGIN_END_ACTIVE]
[  584.027485] nouveau 0000:01:00.0: gr: 00100000 [] ch 6 [001f857000 chromium-browse[2914]] subc 3 class 8597 mthd 1918 data 00000000
[  584.027494] nouveau 0000:01:00.0: gr: DATA_ERROR 0000000d [BEGIN_END_ACTIVE]
[  584.027497] nouveau 0000:01:00.0: gr: 00100000 [] ch 6 [001f857000 chromium-browse[2914]] subc 3 class 8597 mthd 191c data 00000900
[  584.027505] nouveau 0000:01:00.0: gr: DATA_ERROR 0000000d [BEGIN_END_ACTIVE]
[  584.027508] nouveau 0000:01:00.0: gr: 00100000 [] ch 6 [001f857000 chromium-browse[2914]] subc 3 class 8597 mthd 1920 data 00000405
[  584.027517] nouveau 0000:01:00.0: gr: DATA_ERROR 0000000d [BEGIN_END_ACTIVE]
[  584.027519] nouveau 0000:01:00.0: gr: 00100000 [] ch 6 [001f857000 chromium-browse[2914]] subc 3 class 8597 mthd 168c data 00000000
[  584.027528] nouveau 0000:01:00.0: gr: DATA_ERROR 0000000d [BEGIN_END_ACTIVE]
[  584.027530] nouveau 0000:01:00.0: gr: 00100000 [] ch 6 [001f857000 chromium-browse[2914]] subc 3 class 8597 mthd 0dc0 data 00000000
[  584.027539] nouveau 0000:01:00.0: gr: DATA_ERROR 0000000d [BEGIN_END_ACTIVE]
[  584.027541] nouveau 0000:01:00.0: gr: 00100000 [] ch 6 [001f857000 chromium-browse[2914]] subc 3 class 8597 mthd 0dc4 data 00000000
[  584.027550] nouveau 0000:01:00.0: gr: DATA_ERROR 0000000d [BEGIN_END_ACTIVE]
[  584.027552] nouveau 0000:01:00.0: gr: 00100000 [] ch 6 [001f857000 chromium-browse[2914]] subc 3 class 8597 mthd 0dc8 data 00000000
[  584.027561] nouveau 0000:01:00.0: gr: DATA_ERROR 0000000d [BEGIN_END_ACTIVE]
[  584.027563] nouveau 0000:01:00.0: gr: 00100000 [] ch 6 [001f857000 chromium-browse[2914]] subc 3 class 8597 mthd 131c data 00000000
[  584.027572] nouveau 0000:01:00.0: gr: DATA_ERROR 0000000d [BEGIN_END_ACTIVE]
[  584.027574] nouveau 0000:01:00.0: gr: 00100000 [] ch 6 [001f857000 chromium-browse[2914]] subc 3 class 8597 mthd 1320 data 00000000
[  584.027583] nouveau 0000:01:00.0: gr: DATA_ERROR 0000000d [BEGIN_END_ACTIVE]
[  584.027585] nouveau 0000:01:00.0: gr: 00100000 [] ch 6 [001f857000 chromium-browse[2914]] subc 3 class 8597 mthd 1324 data 00000000
[  584.027594] nouveau 0000:01:00.0: gr: DATA_ERROR 0000000d [BEGIN_END_ACTIVE]
[  584.027596] nouveau 0000:01:00.0: gr: 00100000 [] ch 6 [001f857000 chromium-browse[2914]] subc 3 class 8597 mthd 1328 data 00000000
[  584.027605] nouveau 0000:01:00.0: gr: DATA_ERROR 0000000d [BEGIN_END_ACTIVE]
[  584.027607] nouveau 0000:01:00.0: gr: 00100000 [] ch 6 [001f857000 chromium-browse[2914]] subc 3 class 8597 mthd 1394 data 00000000
[  584.027616] nouveau 0000:01:00.0: gr: DATA_ERROR 0000000d [BEGIN_END_ACTIVE]
[  584.027618] nouveau 0000:01:00.0: gr: 00100000 [] ch 6 [001f857000 chromium-browse[2914]] subc 3 class 8597 mthd 0f54 data 00000000
[  584.027627] nouveau 0000:01:00.0: gr: DATA_ERROR 0000000d [BEGIN_END_ACTIVE]
[  584.027629] nouveau 0000:01:00.0: gr: 00100000 [] ch 6 [001f857000 chromium-browse[2914]] subc 3 class 8597 mthd 1700 data ffffffff
[  584.027638] nouveau 0000:01:00.0: gr: DATA_ERROR 0000000d [BEGIN_END_ACTIVE]
[  584.027641] nouveau 0000:01:00.0: gr: 00100000 [] ch 6 [001f857000 chromium-browse[2914]] subc 3 class 8597 mthd 1704 data ffffffff
[  584.027649] nouveau 0000:01:00.0: gr: DATA_ERROR 0000000d [BEGIN_END_ACTIVE]
[  584.027652] nouveau 0000:01:00.0: gr: 00100000 [] ch 6 [001f857000 chromium-browse[2914]] subc 3 class 8597 mthd 1708 data ffffffff
[  584.027661] nouveau 0000:01:00.0: gr: DATA_ERROR 0000000d [BEGIN_END_ACTIVE]
[  584.027663] nouveau 0000:01:00.0: gr: 00100000 [] ch 6 [001f857000 chromium-browse[2914]] subc 3 class 8597 mthd 170c data ffffffff
[  584.027672] nouveau 0000:01:00.0: gr: DATA_ERROR 0000000d [BEGIN_END_ACTIVE]
[  584.027674] nouveau 0000:01:00.0: gr: 00100000 [] ch 6 [001f857000 chromium-browse[2914]] subc 3 class 8597 mthd 1710 data ffffffff
[  584.027683] nouveau 0000:01:00.0: gr: DATA_ERROR 0000000d [BEGIN_END_ACTIVE]
[  584.027685] nouveau 0000:01:00.0: gr: 00100000 [] ch 6 [001f857000 chromium-browse[2914]] subc 3 class 8597 mthd 1714 data ffffffff
[  584.027694] nouveau 0000:01:00.0: gr: DATA_ERROR 0000000d [BEGIN_END_ACTIVE]
[  584.027696] nouveau 0000:01:00.0: gr: 00100000 [] ch 6 [001f857000 chromium-browse[2914]] subc 3 class 8597 mthd 1718 data ffffffff
[  584.027705] nouveau 0000:01:00.0: gr: DATA_ERROR 0000000d [BEGIN_END_ACTIVE]
[  584.027707] nouveau 0000:01:00.0: gr: 00100000 [] ch 6 [001f857000 chromium-browse[2914]] subc 3 class 8597 mthd 171c data ffffffff
[  584.027716] nouveau 0000:01:00.0: gr: DATA_ERROR 0000000d [BEGIN_END_ACTIVE]
[  584.027718] nouveau 0000:01:00.0: gr: 00100000 [] ch 6 [001f857000 chromium-browse[2914]] subc 3 class 8597 mthd 1720 data ffffffff
[  584.027727] nouveau 0000:01:00.0: gr: DATA_ERROR 0000000d [BEGIN_END_ACTIVE]
[  584.027729] nouveau 0000:01:00.0: gr: 00100000 [] ch 6 [001f857000 chromium-browse[2914]] subc 3 class 8597 mthd 1724 data ffffffff
[  584.027738] nouveau 0000:01:00.0: gr: DATA_ERROR 0000000d [BEGIN_END_ACTIVE]
[  584.027740] nouveau 0000:01:00.0: gr: 00100000 [] ch 6 [001f857000 chromium-browse[2914]] subc 3 class 8597 mthd 1728 data ffffffff
[  584.027797] nouveau 0000:01:00.0: gr: DATA_ERROR 0000000d [BEGIN_END_ACTIVE]
[  584.027799] nouveau 0000:01:00.0: gr: 00100000 [] ch 6 [001f857000 chromium-browse[2914]] subc 3 class 8597 mthd 172c data ffffffff
[  584.027814] nouveau 0000:01:00.0: gr: DATA_ERROR 0000000d [BEGIN_END_ACTIVE]
[  584.027816] nouveau 0000:01:00.0: gr: 00100000 [] ch 6 [001f857000 chromium-browse[2914]] subc 3 class 8597 mthd 1730 data ffffffff
[  584.027825] nouveau 0000:01:00.0: gr: DATA_ERROR 0000000d [BEGIN_END_ACTIVE]
[  584.027827] nouveau 0000:01:00.0: gr: 00100000 [] ch 6 [001f857000 chromium-browse[2914]] subc 3 class 8597 mthd 1734 data ffffffff
[  584.027836] nouveau 0000:01:00.0: gr: DATA_ERROR 0000000d [BEGIN_END_ACTIVE]
[  584.027839] nouveau 0000:01:00.0: gr: 00100000 [] ch 6 [001f857000 chromium-browse[2914]] subc 3 class 8597 mthd 1738 data ffffffff
[  584.027848] nouveau 0000:01:00.0: gr: DATA_ERROR 0000000d [BEGIN_END_ACTIVE]
[  584.027850] nouveau 0000:01:00.0: gr: 00100000 [] ch 6 [001f857000 chromium-browse[2914]] subc 3 class 8597 mthd 173c data ffffffff
[  584.027862] nouveau 0000:01:00.0: gr: DATA_ERROR 0000000d [BEGIN_END_ACTIVE]
[  584.027864] nouveau 0000:01:00.0: gr: 00100000 [] ch 6 [001f857000 chromium-browse[2914]] subc 3 class 8597 mthd 1740 data ffffffff
[  584.027873] nouveau 0000:01:00.0: gr: DATA_ERROR 0000000d [BEGIN_END_ACTIVE]
[  584.027875] nouveau 0000:01:00.0: gr: 00100000 [] ch 6 [001f857000 chromium-browse[2914]] subc 3 class 8597 mthd 1744 data ffffffff
[  584.027884] nouveau 0000:01:00.0: gr: DATA_ERROR 0000000d [BEGIN_END_ACTIVE]
[  584.027887] nouveau 0000:01:00.0: gr: 00100000 [] ch 6 [001f857000 chromium-browse[2914]] subc 3 class 8597 mthd 1748 data ffffffff
[  584.027895] nouveau 0000:01:00.0: gr: DATA_ERROR 0000000d [BEGIN_END_ACTIVE]
[  584.027898] nouveau 0000:01:00.0: gr: 00100000 [] ch 6 [001f857000 chromium-browse[2914]] subc 3 class 8597 mthd 174c data ffffffff
[  584.027907] nouveau 0000:01:00.0: gr: DATA_ERROR 0000000d [BEGIN_END_ACTIVE]
[  584.027909] nouveau 0000:01:00.0: gr: 00100000 [] ch 6 [001f857000 chromium-browse[2914]] subc 3 class 8597 mthd 1750 data ffffffff
[  584.027918] nouveau 0000:01:00.0: gr: DATA_ERROR 0000000d [BEGIN_END_ACTIVE]
[  584.027920] nouveau 0000:01:00.0: gr: 00100000 [] ch 6 [001f857000 chromium-browse[2914]] subc 3 class 8597 mthd 1754 data ffffffff
[  584.027929] nouveau 0000:01:00.0: gr: DATA_ERROR 0000000d [BEGIN_END_ACTIVE]
[  584.027931] nouveau 0000:01:00.0: gr: 00100000 [] ch 6 [001f857000 chromium-browse[2914]] subc 3 class 8597 mthd 1758 data ffffffff
[  584.027940] nouveau 0000:01:00.0: gr: DATA_ERROR 0000000d [BEGIN_END_ACTIVE]
[  584.027942] nouveau 0000:01:00.0: gr: 00100000 [] ch 6 [001f857000 chromium-browse[2914]] subc 3 class 8597 mthd 175c data ffffffff
[  584.027951] nouveau 0000:01:00.0: gr: DATA_ERROR 0000000d [BEGIN_END_ACTIVE]
[  584.027953] nouveau 0000:01:00.0: gr: 00100000 [] ch 6 [001f857000 chromium-browse[2914]] subc 3 class 8597 mthd 1760 data ffffffff
[  584.027962] nouveau 0000:01:00.0: gr: DATA_ERROR 0000000d [BEGIN_END_ACTIVE]
[  584.027964] nouveau 0000:01:00.0: gr: 00100000 [] ch 6 [001f857000 chromium-browse[2914]] subc 3 class 8597 mthd 1764 data ffffffff
[  584.027973] nouveau 0000:01:00.0: gr: DATA_ERROR 0000000d [BEGIN_END_ACTIVE]
[  584.027975] nouveau 0000:01:00.0: gr: 00100000 [] ch 6 [001f857000 chromium-browse[2914]] subc 3 class 8597 mthd 1768 data ffffffff
[  584.027984] nouveau 0000:01:00.0: gr: DATA_ERROR 0000000d [BEGIN_END_ACTIVE]
[  584.027986] nouveau 0000:01:00.0: gr: 00100000 [] ch 6 [001f857000 chromium-browse[2914]] subc 3 class 8597 mthd 176c data ffffffff
[  584.027995] nouveau 0000:01:00.0: gr: DATA_ERROR 0000000d [BEGIN_END_ACTIVE]
[  584.027997] nouveau 0000:01:00.0: gr: 00100000 [] ch 6 [001f857000 chromium-browse[2914]] subc 3 class 8597 mthd 1770 data ffffffff
[  584.028006] nouveau 0000:01:00.0: gr: DATA_ERROR 0000000d [BEGIN_END_ACTIVE]
[  584.028008] nouveau 0000:01:00.0: gr: 00100000 [] ch 6 [001f857000 chromium-browse[2914]] subc 3 class 8597 mthd 1774 data ffffffff
[  584.028017] nouveau 0000:01:00.0: gr: DATA_ERROR 0000000d [BEGIN_END_ACTIVE]
[  584.028019] nouveau 0000:01:00.0: gr: 00100000 [] ch 6 [001f857000 chromium-browse[2914]] subc 3 class 8597 mthd 1778 data ffffffff
[  584.028028] nouveau 0000:01:00.0: gr: DATA_ERROR 0000000d [BEGIN_END_ACTIVE]
[  584.028031] nouveau 0000:01:00.0: gr: 00100000 [] ch 6 [001f857000 chromium-browse[2914]] subc 3 class 8597 mthd 177c data ffffffff
[  584.028039] nouveau 0000:01:00.0: gr: DATA_ERROR 0000000d [BEGIN_END_ACTIVE]
[  584.028042] nouveau 0000:01:00.0: gr: 00100000 [] ch 6 [001f857000 chromium-browse[2914]] subc 3 class 8597 mthd 1798 data 00000000
[  584.028051] nouveau 0000:01:00.0: gr: DATA_ERROR 0000000d [BEGIN_END_ACTIVE]
[  584.028053] nouveau 0000:01:00.0: gr: 00100000 [] ch 6 [001f857000 chromium-browse[2914]] subc 3 class 8597 mthd 1510 data 00000000
[  584.028062] nouveau 0000:01:00.0: gr: DATA_ERROR 0000000d [BEGIN_END_ACTIVE]
[  584.028064] nouveau 0000:01:00.0: gr: 00100000 [] ch 6 [001f857000 chromium-browse[2914]] subc 3 class 8597 mthd 1664 data 00000000
[  620.283417] FAT-fs (sdc1): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.



```

Any ideas? Other than remembering never to update... anything that is working....  ever.... I can't seem to find a "way in" to start anal;ysing the issue? My suspicions are it's a WebGL, or NVIDEA dirver problem, as OnShape usues that heavily.

---

### Post by sdsurfer on 2020-03-04
> never to update... anything that is working....  ever....

Nah, failure is just an opportunity to learn. :-D 18.04 is really solid.

This post is so timely, I just resolved this Monday. I recently received a company System76 Gazelle lappie, I own one personally and have never had a problem with it but this new one froze and froze, I began to suspect it was hardware but as it turns out, it was indeed the wrong driver. My first go-to on freezing issues is always graphic drivers but didn't this time because it was new out of the box and presumed it was configured (has a 6 GB Nvidia GPU.) It wasn't.

Look at your log:
```
[  584.028031] **nouveau** 0000:01:00.0: gr: 00100000 [] ch 6 [001f857000 chromium-browse[2914]] subc 3 class 8597 mthd 177c data fffffff]
```

I was getting very similar logs, the very last syslog entry before total lockup (and I mean TOTAL) were lines and tracebacks with one common element, noveau.

**Nouveau** is the X.org display driver. You say Nvidia, first confirm your hardware is using the Nvidia driver. The most simple is open a terminal window and execute:

```
lspci | grep VGA
```

(You shouldn't have to sudo)

If a controller is listed with Nvidia, it is available to your system.

[I][B]NOTE: The following advice is for MY computer, MY scenario - only execute if you feel confident you can revert if it doesn't work.
[/B][/I]
If Nvidia is listed, go to Search your Computer->System Settings->Software & Updates->Additional Drivers Tab, let it load. If it's the same condition, you will likely see a section for NVIDIA Corporation with radio buttons, one for X.Org and hopefully one for Nvidia. If my guess is correct, you will have Noveau selected.

Select the NVIDIA driver and apply changes, it will download and install. Reboot. Hopefully your problem is now history. If not, set it back to the X.Org driver, it's something else.

**Edit:** An alternative method that I used to chase down the problem:
```
sudo tail -f /var/log/syslog
```

 before evoking the commands that caused it to freeze. The -f is interactive, outputs to screen in real-time. This way I could see the exact point at which it hung. You can then, on reboot, less the log, find the entry, and look for any line with "Oops" in it. Following that will be some Call Trace stuff showing the call stack that led to the "Oops."

---

### Post by Autodave on 2020-03-04
Some specs on your equipment would probably be helpful.

ALWAYS do updates: they often times are security updates and need to be done!

---

### Post by steve234 on 2020-03-04
@Autodave specs are: older i7 processor, 16GB ram, NVIDEA G210 graphics - so not my netbook!

Thanks sdsurfer, Apologies, I've cross-posted some of the information you're after[ in another thread ]("https://ubuntuforums.org/showthread.php?t=2437992")- figured hardware was a better fit.

>  first confirm your hardware is using the Nvidia driver.

```
[COLOR=#000000][FONT=&amp]NVIDIA Corporation GT218 [GeForce G210][/FONT][/COLOR]
Kernel driver in use: nouveau [COLOR=#000000][FONT=&amp]Kernel modules: nvidiafb, nouveau[/FONT][/COLOR]
```

>  go to Search your Computer->System Settings->Software & Updates->Additional Drivers Tab, let it load. If it's the same condition, you will likely see a section for NVIDIA Corporation with radio buttons, one for X.Org and hopefully one for Nvidia. If my guess is correct, you will have Noveau selected.

I did this today actually when I saw nouveau in the lspci output and that reminded me about the proprietary driver. Unfortunately the radio button did nothing (it reverted back to nouveau when applied).

I've since installed the nvidia-340 driver manually using the ubuntu-drivers devices method. Now the radio button stays selected. Fingers crossed

---

### Post by steve234 on 2020-03-04
So far so good - now I can get back to designing super-awesome:

- Nerf magazines with Hex Pattern through them; and
- drums which take many darts.

[ATTACH=CONFIG]285150[/ATTACH][ATTACH=CONFIG]285151[/ATTACH]

(if interested see attached scrots):

---

### Post by sdsurfer on 2020-03-04
Cool, at the upper right of the thread under Thread Tools you should see "Mark thread as solved" when you're sure.

---

### Post by steve234 on 2020-03-10
This fix seems to be working well - marked solved, thanks for all your help.

---

### Post by steve234 on 2020-03-13
> **sdsurfer said:**
> Cool, at the upper right of the thread under Thread Tools you should see "Mark thread as solved" when you're sure.

Sorry @sdsurfer but unfortunately this fix is [causing me another issue ]("https://ubuntuforums.org/showthread.php?t=2438451"), one more problematic as this box is a shared family PC. 

I've now plugged my monitor into the VGA port rather than HDMI, for two reasons:

(1) I only run one screen now I'm on a smaller desk; and
(2) the HDMI adapter is my work's property, and I need it for my work laptop.

The resolution has gone down to 1024 from 1920. I've managed a fix, but only if I use the noveau driver and suffer system hangs when I use OnShape

I have no idea why my system is only recognising the resolutions of the old smaller monitor on the VGA connection, but it looks as if the NVIDEA driver is broken for custom resolution setting via CVT and xrandr

I'd been running this PC as a family PC for ages, but with "linux not working" i.e. the resolution is all weird I may get pressure to head back to Windows after all this time.

I may have to suck up the linux-yness and buy my own HDMI adaptor - which is sub-optimal

---

