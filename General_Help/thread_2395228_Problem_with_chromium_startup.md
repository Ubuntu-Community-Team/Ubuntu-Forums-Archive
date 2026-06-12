---
title: "Problem with chromium startup"
date: 2018-06-28
forum: General Help
---

### Post by Tom_Carr on 2018-06-28
I am running ubuntu 18.04

I want Chromium to startup when ubuntu starts up.  In startup application preferences I have:
Name:  Chromium
Command:  chromium-browser
Comment:  Chromium


It doesn't start up.  What am I doing wrong?

---

### Post by deadflowr on 2018-06-28
Is it the apt version or snap version?
If installed from Ubuntu Software it might not be clear which was installed unless you look closely.
To see which with ease just run the snap list command to see what if any snaps are installed
```
snap list
```
if nothing then it's more likely the apt version.
In which case we'll have o take a closer look at what's going on.

---

### Post by Tom_Carr on 2018-06-29
It looks like it is the snap version.  

tom@tom-OptiPlex-990:~$ snap list
Name                  Version       Rev   Tracking  Developer  Notes
chromium              67.0.3396.62  353   stable    canonical  -
core                  16-2.33       4830  stable    canonical  core
gnome-3-26-1604       3.26.0        64    stable/&#8230;  canonical  -
gnome-calculator      3.28.1        178   stable/&#8230;  canonical  -
gnome-characters      3.28.2        101   stable/&#8230;  canonical  -
gnome-logs            3.28.2        37    stable/&#8230;  canonical  -
gnome-system-monitor  3.26.0        45    stable/&#8230;  canonical  -
tom@tom-OptiPlex-990:~$

---

### Post by Tom_Carr on 2018-06-29
I never installed chromium.  It was automatically installed when I installed ubuntu 18.04.  This was a fresh install.

---

### Post by deadflowr on 2018-06-29
Try
```
snap run chromium
```
as the Exec line.

You can see 
```
snap help
```
for basic snap commands.

Or if snap is too much to deal with just install the apt version.
```
sudo apt install chromium-browser
```
then if you want you can keep the snap version or remove it.

Both versions can be installed at the same time.
(snaps are self-contained within their own little world)

---

### Post by Tom_Carr on 2018-06-29
I put "[COLOR=#000000][FONT=&quot]snap run chromium" in the command line of startup  and now chromium starts when the computer starts.  Problem solved.  Thanks.

One other related question.  If I have tabs open in chromium, and I power off without  closing chromium first, when I power back on I get a message box saying "Restore Pages?".  If I close chromium before powering off, it opens next time with no tabs open.

Is there a way to set things up so it  just automatically reopens with the tabs open from before the last shut down?[/FONT][/COLOR]

---

### Post by deadflowr on 2018-06-29
You should be able to set it to open with the last pages open by setting it in settings
Scroll down in settings and find the section where ti says **On Startup** and set it to *Continue where you left off*.
(setting is the 3 dots at the end of the bar that the address bar is on or you can open it with
```
chrome://settings
```
that should set it to always open with whatever tabs you had when you closed it.

The restore tabs that shows is when the browser did not properly shutdown.
So it can save where you were in case of some disaster struck, like if the power got shut off accidentally or if something caused the browser to crash.
And then you can restart exactly where you left off.
if that make sense.

---

### Post by Tom_Carr on 2018-06-29
That solves all my problems.  Thanks for your help Deadflowr.

---

