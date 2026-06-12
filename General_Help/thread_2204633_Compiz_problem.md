---
title: "Compiz problem"
date: 2014-02-09
forum: General Help
---

### Post by typos1 on 2014-02-09
About a year ago I modified 1 thing in CCSM (compiz settings manager - I am aware that modifying compiz can cause problems, this is why I only checked or unchecked 1 box and then put it back the way it was before I changed it), I cant remember what box it was that I checked or unbchecked, but it did not work or I wasnt happy with it, so I undid the change. 

Ever since, I have had a bug with compiz - if I have a window open on a desktop other than the one I am on and I click on the icon in unity, it will not take me to that window, this feature will only work if the window is open on the desktop I am on, then it will take me there.

I have uninstalled and re-installed compiz, but it made no difference - the problem was still there (which reminded me of a problem I have with VLC - suddenly it stopped working - nothing would happen if you clicked on "open with VLC", so I uninstalled it, then re-installed it and still get the same problem !). I uninstalled and re-installed compiz settings manager, but still could not sort the problem.

I ve put up with this problem for about a year, I recently upgraded to 13.10 so I thought I d try and fix it, so I think I need some help ! Anyone got any ideas ?

Thanks

---

### Post by typos1 on 2014-02-10
Tried removing CCSM using Synaptic, hoping that maybe there were other things installed also and if I removed them aswell it would sort the problem. 

That didnt work as there doe not seem to be any other parts.

---

### Post by typos1 on 2014-02-12
Should I try and uninstall then re-install Compiz ?

---

### Post by deadflowr on 2014-02-12
If you still have ccsm installed open it and in the left side panel,thingy, click open preferences.
There is a button called something lie reset to deafults.

This will make the desktop seemingly bork for a minute or two.
Let it bork away.

**Do not close the ccsm window**.(emphasis needed)
When the borking seems to stop, go back to the main ccsm screen and select the option for unity plugin(or whatever it is called.(It is in the section "Desktop")

When the unity plugin window is open, check the enable plugin in the left side panel.
It'll probably ask to set something, I usually take whatever defaults there are(usually the default selections are highlighted).
After that, look to see that other settings are set, like window decorations, desktop wall, expo, and I think most crucial, opengl.( Though I believe the opengl plugin gets enabled when you enable the unity plugin)

Usually though, all you'll need to do is simple enable unity plugin.


See if this helps.

---

### Post by ralph-beeby on 2014-02-13
deadflowr, do you think it's worth installing ccsm if I haven't already? I'm having some problems with my desktop environment (Unity, 12.04) and I think Compiz might be the source of the problem. If I enter
```
$ unity --reset
```
into a terminal, it appears to bork for a minute or two and eventually tells me
```
Compiz (opengl) - fatal: Root visual is not a GL visual
```

Just wondering whether trying the "reset to defaults" option in ccsm might fix the problems I'm having!

---

### Post by monkeybrain20122 on 2014-02-13
> **ralph-beeby said:**
> deadflowr, do you think it's worth installing ccsm if I haven't already? I'm having some problems with my desktop environment (Unity, 12.04) and I think Compiz might be the source of the problem. If I enter
```
$ unity --reset
```
into a terminal, it appears to bork for a minute or two and eventually tells me
```
Compiz (opengl) - fatal: Root visual is not a GL visual
```

Just wondering whether trying the "reset to defaults" option in ccsm might fix the problems I'm having!
Won't help. It appears to be a graphic driver problem. [http://ubuntuforums.org/showthread.php?t=1959496](http://ubuntuforums.org/showthread.php?t=1959496)

---

### Post by ralph-beeby on 2014-02-13
> **monkeybrain20122 said:**
> Won't help. It appears to be a graphic driver problem. [http://ubuntuforums.org/showthread.php?t=1959496](http://ubuntuforums.org/showthread.php?t=1959496)

I did stumble across that thread - thought it might be a driver problem, but I've got an ATI Radeon in this computer, and, as far as I can tell, no proprietary drivers! (Ironically, my other machine has a nVIDIA card and driver and is working fine...)

---

### Post by monkeybrain20122 on 2014-02-13
CCSM is not a big program to install so it is worth having a tweak tool. But since you didn't have it, you could not have changed the default settings (how without the ccsm?), so it is already default.

 I think the problem will be fixed if you install the proprietary driver. The thread is about a different card, but I think the general diagnosis that it is graphic driver related is still valid.

---

### Post by ralph-beeby on 2014-02-13
Both very good points! I shall have a look for a Radeon driver and see how that fares. Thanks very much!

Update: solved, at least in my case. Have ended up removing fglrx - which I think is the proprietary driver and fallen back to the open-source version. (My mistake: I forgot I'd installed fglrx and fglrx-amdcccle ages ago; for some reason they weren't showing up in my "Additional Drivers" list!) 

Essentially ended up following the commands at [https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection#Problem:_Need_to_purge_-fglrx](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection#Problem:_Need_to_purge_-fglrx) and now my desktop is the way I remember it. Thanks again for your help!

---

### Post by typos1 on 2014-02-13
Well, it seems to have sorted my problems. It didnt bork for very long, I lost unity, all window controls and went to one desktop, effectively leaving me with a broken system, unable to use anything. 

With some clever workarounds (like using F11 to minimise Firefox, cant remember how I managed to get the window bacjk up again afterwards), I managed to get firefox back (to finish reading your instructions!) and eventually re-enable unity etc. 

I had 3 warnings of things conflicting with Gnome after restting defaults. I chose the option dis-able whatever CCSM thought would conflict.

But now the problem is sorted . . . I just have a new problem of not being able to re-size windows !

edit: was as simple as re-enabling "resize windows" lol

So sorted, thanks !!

---

### Post by monkeybrain20122 on 2014-02-13
> **typos1 said:**
>  I just have a new problem of not being able to re-size windows !

Open ccsm, scroll down to Window Management and check the box "Resize Window".

---

### Post by deadflowr on 2014-02-13
> **monkeybrain20122 said:**
> Won't help. It appears to be a graphic driver problem. [http://ubuntuforums.org/showthread.php?t=1959496](http://ubuntuforums.org/showthread.php?t=1959496)

Off topic, but I remember the 295.40 nvidia driver was unbelievably borken.(This is actually a typo, but it fits well)

typos1, Yeah the reset defaults can leave things un-enabled, which why the first things to check are the unity plugin and make sure window decorations are enabled as well.
With windows decorations, you'll at least be able to close or minimize.
In general, though, most settings come back set as they should.
But you never know.
The thing about resetting the system with ccsm, is that it works for all supported versions of Ubuntu.
Where as the unity --reset command, and the newer dconf reset commands work per certain releases.
So whether you have 12.04 or 13.10 ccsm reset will work, for the most part.
(Unless something else is factoring into it, like a borked driver)

---

### Post by typos1 on 2014-02-13
Lol, yeah I already worked it out and edited my previous post before I saw your post above !

---

