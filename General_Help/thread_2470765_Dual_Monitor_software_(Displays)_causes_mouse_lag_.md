---
title: "Dual Monitor software (Displays) causes mouse lag and eractic mouse"
date: 2022-01-10
forum: General Help
---

### Post by rosentritt on 2022-01-10
I am running two HP computers, A and B, with two monitors each.
Machine A  was running Ubuntu 16, since 2017, two HP monitors via  DisplayLink plugable usb 2.0 display adapter.  This ran well for years  and 16 was preferrable to the changes in 18 and after.
Machine B was running Xubuntu 16, two identical HP monitors via a  DisplayLink plugable usb 2.0 display adapter.  This ran even better and  we did not have a reason to change anything.
In mid-December 2021, on Machine B, after both 'software updates' and an  electrical outage, the mouse started behaving erractic when the second  monitor was on.  There were not any problems just using one monitor.
 
[LIST=1]
[*]when moving and it paused, it would leave a ghost pointer showing
[*]it would sometimes leave pointer  'trails', much like some old mouse setting in windows3
[*]it would carry small (a few mm) squares of pixels and leave traces
[*]mouse lags, starts and stops and 'jumps around'
[/LIST]
 After trying a few fixes to no avail, I 'updated' to Xubuntu 20.  The  problem persisted with slight variations.  No problem with single  monitor.
I then did a complete new install from a MATE 20 live usb.  Same  problem, with a very slight improvement.  No problem with single  monitor.
I then 'updated' to MATE 21.  Same problem.  No problem with single monitor.
 With nothing else to try and liking the look of MATE 20,  I installed  it on Machine A, in a new partition.  (Machine A did NOT suffer from the  electrical outage.)
With second monitor on, A has a different problem.  If the second  monitor is used, the mouse lags and moves eratic.  (Has the look of a  system that is low on resources and is struggling.)  No problem with  single monitor.

 I have tried all the settings in various combinations, mouse and  displays, installing Arandr, with no improvements.  I've attempted  various things from the web, 'zoom' settings and nvida monitors......  nothing works as of yet.
It all seems to be related to the 'new' DISPLAYS software?
I'm surprised that my two computers seems to be the only two with this problem.
Any help would be greatly appreaciated.

---

### Post by guiverc on 2022-01-10
Ubuntu has both products that use the *year* format (eg. Ubuntu Core 20), and products using the *year.month* format, eg. Ubuntu 20.04 LTS Desktop.

No products using the *year* product have desktops, and no *flavors* are created for them, as they are *snap* only products and cannot use *deb* packages; being intended for *headless* server use only.

Please try and be precise with details. 

FYI: If you have/had a Ubuntu Core 16 system, one benefit of that system was when you upgraded to a later release (eg. Ubuntu Core 18 or Ubuntu Core 20), no end user-apps actually changed as only the base OS updates, ie.  very different when compared to a 16.04 to 18.04 upgrade where all packages upgrade and many more changes  occur. The different product format (*year/18 vs year.month/18.04*) highlights the differing products.

---

### Post by rosentritt on 2022-01-11
Sorry about any confusion, I've used Ubuntu since 2005 and didn't really know about Core.  All the products I have tried have been year.04 LTS.

---

