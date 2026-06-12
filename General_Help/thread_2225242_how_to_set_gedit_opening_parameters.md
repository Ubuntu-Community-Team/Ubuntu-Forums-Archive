---
title: "how to set gedit opening parameters"
date: 2014-05-20
forum: General Help
---

### Post by sam_baker2 on 2014-05-20
Is there anyway to set the opening parameters of gedit so that it
will always open at a certain position and at a certain W/L size?

Mine always open full screen, I would like to change that.
Seems there should be a default setting somewhere that one can set.

Thanks

---

### Post by coldcritter64 on 2014-05-20
I'm not on a Unity desktop or on Ubuntu, but I'm remembering a window maximise setting in Compiz that I'd turn to 100 % to stop windows over a certain size automatically going to full screen. 

IIRC the default state of the setting is about 70% and any window that size or larger will automatically go to full screen, highly annoying. See if in compizconfig settings manager there is a setting like that and try to change it to 100% to disable it, IF it turns out to be the cause of the problem.

Otherwise window sizes and placement per application can be set with the gdevilspie application (in the repositories), a very powerful tool when you work out how to use it, it took me a while to work it out but now don't know how I ever got by without it (even when I'm on Ubuntu I install and use it very extensively, it's a very good tool).

> Is there anyway to set the opening parameters of gedit so that it
will always open at a certain position and at a certain W/L size?
Actually gdevilspie is excellent for that scenario just with the geometry settings alone. See the attached screenshot for a better idea of gdevilspie. That shot shows the settings for my browsers "about" dialog box, including for opacity as well as geometry. Cheers.

---

### Post by sam_baker2 on 2014-05-20
Thanks coldcritter64 !
I will give that a try. It looks cool.
Amazing how many goodies Linux has that one might not be aware of.

---

### Post by sam_baker2 on 2014-05-20
opps.
I thought it was working, but gedit stil opens in full screen.
I set application name, window name & window workspae all to "gedit", no luck.

Raw listing is:
```
 
( begin 
( is ( application_name ) "gedit" )
( is ( window_name ) "gedit" )
( is ( window_workspace ) "gedit" )
) 
( begin 
( geometry "500x500+30+30" )
( println "match" )
)
)

```

---

### Post by coldcritter64 on 2014-05-20
> **sam_baker2 said:**
> opps.
I thought it was working, but gedit stil opens in full screen.
I set application name, window name & window workspae all to "gedit", no luck....Have you ticked the box for automatic start of the devilspie daemon on boot up; there is a tickbox near the stop/start button. Also when the daemon is active the button will show as a red lettered "stop" button, if it is showing as green "start" button the daemon is not running and nothing will happen. **Edit:** after setting any rule stop then restart the daemon with that button for any change to happen, OR shut down any open window the rule applies to and reopen for the daemon to pick it up and do its business.

If, after checking the details above in this post, the window still keeps going fullscreen, you will need to install compizconfig-settings-manager and hunt down the compiz setting I mentioned in my first post; it is most likely the culprit IF the gDp daemon IS active. Take care with "ccsm" in what you alter.
[B]
Edit 2[/B]: you only need the application name set if you want all gedit windows the same. Only set an entry in the window name if you want to do an action on a specific instance of gedit (with a unique window name). Unset that window workspace, that could be stopping you here (not sure). I tend to set the minimal amount of options till I get the desired effect; in your case I'd only set the application name (it appears you want ALL gedit windows the same).

---

### Post by mcduck on 2014-05-21
Compiz (the windowmanager used in Unity) also has built-in tools for defining window sizes, workspaces to launch on and various other things so Devilspie shouldn't be needed at all (and might actually just end conflicting with what Compiz is trying to do).

Anyway, just install CompizConfig Settings Manager (if you don't have it already), and under "Window Management"-section you'll find the "Window Rules" and "Place Windows"-plugins.

---

### Post by sam_baker2 on 2014-05-21
Are there any instructions anywhere about how to set Compiz to do this? I have absolutely no idea about how to set it so that gedit will always
open at a certain position and at a certain W/L size.

I got devilspie to work, but for some reason, when I put gedit in fullscreen, then close it out, the next time it is opened, it 
always opens at full screen. I can repostion it to any other position/size and close it out and when it opens back up, it
will open to the parameters I have set in devilspie.

(also, I use Xubuntu 12.04 )

---

### Post by coldcritter64 on 2014-05-21
Install ccsm (the package in the repos is called compizconfig-settings-manager) and look for that automaximize value and change it to 100% (as much to rule it out as a contributing factor). Also very nearly any window when shut down from fullscreen will remember it's size and on reopening will still be at fullscreen. 

There is an **unmaximize** action in gDp you would need to set as well to force the changes, the fullscreen setting and compiz settings seem to override gDp from my experiences with it. So it is a handy addition but takes a lot of experimenting at times to get everything "working together". Check all the compiz settings and use the unmaximize action of gDp.

I have never used the compiz plugin myself for windows and have only ever noted the automaximize function of compiz to "clash" with gDp (quite possible there could be more that do, I haven't seen any in 4 to 5 years  of use) You can use the "get" button in gDp to get the current settings of a window for checking existing settings of a window, of the values reported only the ones you tick will be set by gDp. 
If you use the "get" button always check the "Application name" setting, sometimes it is wrong and won't work, example ... gnome-terminal gets put in as Terminal and won't work till the name is changed, the get button is a bit buggy in that regard. 

Don't set rules in gDp for any window you set in Compiz and use the gDp "get" button on windows to check settings first, only ticked values will be set by gDp, then there won't be clashing of the 2. 

Personally I don't like using the compiz plugins for windows controls, I believe compiz has improved but I remember a hell of a lot of problems with beginners and ccsm, so much so that it was nearly ripped out of the repos and now carrys a warning for new/inexperienced users at startup. I caution inexperienced/new users to use it with care, though a lot of changes/improvements have been made I saw on my last install using it.

> (also, I use Xubuntu 12.04 )Debian Wheezy, xfce 4.8 DE here and no problems with it, but I don't have to contend with compiz like you do (I have done so in the past though without problems).

---

### Post by sam_baker2 on 2014-05-22
Thanks coldcritter64.
Setting gDs window to unmaximize did the trick.
Also thanks mcduck about informing me about compiz.
I am going to be looking into this for a lot of other things it seems to
be useful.

---

### Post by grumblebum2 on 2014-05-22
> **sam_baker2 said:**
> Thanks coldcritter64.
Setting gDs window to unmaximize did the trick.
Also thanks mcduck about informing me about compiz.
I am going to be looking into this for a lot of other things it seems to
be useful.
Compiz isn't the window manager in Xubuntu, so unless you have installed compiz and enabled it as your window 
manager, ccsm will have no affect.

---

### Post by coldcritter64 on 2014-05-22
> **grumblebum2 said:**
> Compiz isn't the window manager in Xubuntu, so unless you have installed compiz and enabled it as your window 
manager, ccsm will have no affect.

Yes, I missed that even when commenting on my Debian install OP, I definitely should have picked that up as I have specifically added compiz to xubuntu in the past to get an xubuntu cube running. Thanks grumblebum2 for pointing that out. 

@OP, ignore any of my past comments about compiz, they are effectively off the original problem's topic. Sorry for any added confusion. Cheers coldcritter64.

---

