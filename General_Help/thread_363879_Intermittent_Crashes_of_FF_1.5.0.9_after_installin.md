---
title: "Intermittent Crashes of FF 1.5.0.9 after installing Flash 9"
date: 2007-02-17
forum: General Help
---

### Post by azteech on 2007-02-17
I know there are other Firefox issues that have been discussed, but don't seem to find a solution to the below problem, and I am not sure if this is the correct forum to post this particular issue. If not, please move to the correct forum, where I may be able to find a solution. Thanks in advance.
+++++++++++++++++++++++++++++++++++++++++++++
Issue: Intermittent**_ Crashes of FF 1.5.0.9 after installing Flash 9_**

After long break from Linux, reinstalled it as dual boot. I installed Ubuntu Linux 5.10 (Breezy) on my HP Pavilion xl844. Dual booting with WinBlows XP. Ubuntu installed on secondary drive. 

Initial install of Linux, encountered no problems. A week of accessing the Internet with Firefox (version 1.5.0.9) had no problems, except for the occasional reminders that PlugIns were needed for this or that. 
After ensuring everything worked properly decided it was time to tackle the Plugin prompts. 1st Plugin I tackled was Flash. Downloaded and installed the Flash 9 (final) Plugin Everything installed properly - no error messages received, and I was able to view several Flash movies, on various sites. After installation of Flash 9, other pressing matters needing attention, and I shut down the computer. 
The next day, fired up the computer, logged in, and began accessing the Internet. Accessing my home page, I experienced repeated (and frequent/intermittent) crashes with Firefox. After several (approx 10) restarts of Firefox it seemed to stabilize and remain open with no additional crashes. It seems FF crashes become more prevalent if I attempt to open multiple tabs before my home page (my.yahoo.com) completely loads. Several crashes seem to occur if I use the "back" button to go to a previous page view, while others cause FF to crash when clicking on links within a page (have FF set to open new links in new tabs). This problem also seems to happen whether I am viewing web pages with or without flash on them. 
This has been an on going problem now for about a week, crashes causing several restarts of Firefox, and then it stabilizes. Each time FF crashes there is no error message. Looking in the log files, I am not able to see any messages concerning FF. When I look at the "about:PlugIns" screen all I see is: 

Shockwave Flash 

File name: libflashplayer.so 
Shockwave Flash 9.0 r31 

MIME Type Description Suffixes Enabled 
application/x-shockwave-flash Shockwave Flash swf Yes 
application/futuresplash FutureSplash Player spl Yes 


Suspect the problem to be Flash 9. Does anyone know how to find error messages concerning FF crashes, troubleshooting tips, correction tips, and/or how to remove Flash 9 to see if this corrects the problem. 

Further note: I have not upgraded Ubuntu Linux yet - so I know upgrades are not the issue. It remains stock, initial load from official Ubuntu 5.10 Desktop Install CD (waiting for my Ubuntu 6.06 LTS CDs to arrive). No additional PlugIns, or extensions for FF have been installed as yet. Have looked through the Forum, and not able to locate any similar issues, for my current setup. Any help would be appreciated.

---

### Post by roland on 2007-02-17
This is a known bug. See [this](http://ubuntuforums.org/showthread.php?t=283364) thread for a list of bugs, and [this](http://ubuntuforums.org/showpost.php?p=1673725&postcount=23) post for a solution. I hope it works.

---

### Post by azteech on 2007-02-17
Thanks roland. Have tried the 1st option listed in the fix. Will see if this corrects the problem. Will let everyone know if this works.

---

### Post by azteech on 2007-02-17
Okay, have tried all recommended solutions to this problem and it still exists :(. Color Depth was already set to "24", and there is no composit section in /etc/X11/xorg.conf file. So only solution I could do was to add the extra line in the /etc/firefox/firefoxrc file. This didn't help either; firefox still crashes. Any other suggestions or troubleshooting ideas?

---

### Post by azteech on 2007-02-18
A question for the developers - 

Looking at the system requirements for Flash 9, I noted that Flash 9 is only supported on the following Linux flavors:

> Linux
_Platform_                                                                                                                                                                                                                                                                                                                                           _Browser_
Red Hat Enterprise Linux (RHEL) 3 update 8, RHEL 4 update 4 (AS/ES/WS)                            Firefox 1.5.0.7 and higher; Mozilla 1.7.x and higher; SeaMonkey 1.0.5     and higher
Novell SUSE 9.x or 10.1                                                                                          Firefox 1.5.0.7 and higher; Mozilla 1.7.x and higher;    SeaMonkey 1.0.5     and higherThis info can be found at [http://www.adobe.com/products/flashplayer/productinfo/systemreqs/](http://www.adobe.com/products/flashplayer/productinfo/systemreqs/)

If it is only supported on Red Hat and Novell SUSE Linux flavors, could this be the cause of the FF crash issues Ubuntu users are experiencing?

---

### Post by Velotix on 2007-02-18
I've been using Flash 9 BETA, and whilst I have the occasional minor glitch such as Firefox hanging on loading a tab it hasn't previously rendered (i.e. I open a new tab but don't look at the tab until it's supposedly finished loading, click it and FF hangs for about 30 seconds before working normally all of a sudden, though on rare occasions FF hangs completely).

Though that's an obviously annoying issue, I don't think it's caused by Flash 9 at all. I'm using Ubuntu Edgy, which uses the newest stable Linux kernel, and Firefox 2.0.0.1. I don't think Breezy is officially supported any longer simply because it's too old, so it's probably a "need-to-upgrade-and-quick" issue.

---

### Post by azteech on 2007-02-18
Velotix,

Thanks for your reply. Happy that you are not experiencing this issue. However, this is a known bug with FF and Flash 9 (roland posted a link to bug report above).

As for Breezy support, it is being supported at least until April this year, if memory serves me correctly. But you are correct in that I definetly need to get upgraded as soon as possible. Just waiting for my new cds to arrive (it stinks to have only dial access).

---

### Post by azteech on 2007-02-23
We can close this thread. Not able to correct issue within 5.10. However, have upgraded to 6.10 and no longer have the problem I faced before with flash 9. Thanks to all for input.

---

