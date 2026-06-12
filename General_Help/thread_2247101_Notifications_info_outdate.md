---
title: "Notifications info outdate"
date: 2014-10-05
forum: General Help
---

### Post by tuxbonewits.com on 2014-10-05
noobie here, but; not totally. Been computing since 1984, mostly windows.
I've got 5-6 years using Puppy Linux from v1.0x to  Precise 5.7.1.

Yesterday I updated everything I could get the updater to update and now getting this;

[IMG]http:/bonewits.com/Notifications 20141005.jpg[/IMG]

[I][COLOR=#0000ff]The Update information is outdated. This
may be caused by network problems or by a 
repository that is no longer available. Please 
update manually by selecting "Show 
Updates" from the indicator menu and 
watching for any failing repositories.[/COLOR]
[/I]
When I do as asked, I get the following:

[COLOR=#0000ff]*The software on this computer is up to date.*[/COLOR]

I have tried all of the options in the Indicator menu.
Yesterday, after several hours, the notification disappeared.
Today after waking up my laptop, it is back.

So now the question is; How do I get rid of this seemingly bogus notification? ;)

Thanks in advance. Your help is appreciated.

[COLOR=#000000][FONT=Times New Roman]HP Pavillion g7 - 2269wm[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]AMD Quad-Core A8-4500M Accelerated Processor[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]17.3" diagonal HD+ BrightView LED Display[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]Advanced Micro Devices, Inc. [AMD/ATI] Trinity [Radeon HD 7640G][/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]Advanced Micro Devices, Inc. [AMD/ATI] Trinity HDMI Audio Controller[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]Qualcomm Atheros AR9485 Wireless Network Adapter (rev 01)[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]500 GB HDD[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]DVD A DS8A9SH[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]6144MB DDR3 SDRAM[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]DVD Optical Drive[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]20141004 - Ubuntu 14.04.1 LTS Trusty Tahr OS[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]---------------------------------------------------------------------------------------------

[/FONT][/COLOR]To have no errors,
Would be life without meaning,
No struggle, No Joy

---

### Post by Vladlenin5000 on 2014-10-05
Please do it manually and copy/paste the results here if there are errors:
```
sudo apt-get update
sudo apt-get upgrade
```

PS - Puppy isn't supported in the main forums. Your thread should be moved to the proper section shortly.

---

### Post by tuxbonewits.com on 2014-10-06
Thanks Vladlenin5000 


ran the code, no prob


rebooted, seems to be gone, but;
I'll wait until tomorrow and see if it comes back
just like it did today.


I will mark this thread solved in a few days IF 
I do not get the same notification


BTW: I did not say I was running Puppy
I said "I've got 5-6 years using Puppy Linux from v1.0x to Precise 5.7.1."
This was ment to note that I have some expirence with one linux distro.
I have been using Ubuntu since 2014-05-01


HP Pavillion g7 - 2269wm
AMD Quad-Core A8-4500M Accelerated Processor
17.3" diagonal HD+ BrightView LED Display
Advanced Micro Devices, Inc. [AMD/ATI] Trinity [Radeon HD 7640G]
Advanced Micro Devices, Inc. [AMD/ATI] Trinity HDMI Audio Controller
Qualcomm Atheros AR9485 Wireless Network Adapter (rev 01)
500 GB HDD
DVD A DS8A9SH
6144MB DDR3 SDRAM
DVD Optical Drive
20141004 - Ubuntu 14.04.1 LTS Trusty Tahr OS
---------------------------------------------------------------------------------------------


To have no errors,
Would be life without meaning,
No struggle, No Joy

---

### Post by Elfy on 2014-10-06
*Thread moved to **General Help**.*

---

### Post by tuxbonewits.com on 2014-10-06
That pesky notification of 'update info outdated' is back.

I suppose I could turn Notifications off, but; that would defeat the purpose of the tool.

Can I live without it?
Is there another way to get Notifications?
Open to suggestions :)

HP Pavillion g7 - 2269wm
AMD Quad-Core A8-4500M Accelerated Processor
17.3" diagonal HD+ BrightView LED Display
Advanced Micro Devices, Inc. [AMD/ATI] Trinity [Radeon HD 7640G]
Advanced Micro Devices, Inc. [AMD/ATI] Trinity HDMI Audio Controller
Qualcomm Atheros AR9485 Wireless Network Adapter (rev 01)
500 GB HDD
DVD A DS8A9SH
6144MB DDR3 SDRAM
DVD Optical Drive
20141004 -  Ubuntu 14.04.1 LTS Trusty Tahr OS
------------------------------------------------------------------------

Ohhhhhhhhhh                        Nooooooooooo !
          Not another learning experience !

---

### Post by Vladlenin5000 on 2014-10-07
You may need to check your sources. Perhaps you added a PPA which is unstable, sometimes offline -or- you may need to change the server for the Ubuntu repositories.

---

