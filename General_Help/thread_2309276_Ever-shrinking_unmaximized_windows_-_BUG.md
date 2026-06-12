---
title: "Ever-shrinking unmaximized windows - BUG?"
date: 2016-01-09
forum: General Help
---

### Post by 2CV67 on 2016-01-09
I often work with a shallow unmaximised window in LibO Calc (to enter data from browser widows in the background) and I am really tired of having to re-size the Calc window to stop it shrinking too far!

I never needed to resize windows like this in Excel, nor in OpenOffice Calc, nor in LibO Calc before about November 2014 (not certain exactly when).

I couldn’t tell what was happening, so made some tests & these are the findings:

1. Behaviour is the same in Calc, Writer & Draw, and similar or worse in other applications (FF, TB, Gedit...) but easier to see & define in Calc.
2. An unmaximised window can be maximised & unmaximised indefinitely without the unmaximized window losing it’s chosen size & position on the screen.
3. An unmaximised window can be closed & reopened indefinitely with no problem.
4. If an unmaximized window is maximized, then closed, then reopened, then unmaximized, it loses height, the top of the window being lower on the screen. (BUG?)
5. Starting, for instance with a 10-row Calc window, after successive unmax>max>close>open>unmax cycles, I end up with 10 – 8 – 6 – 4 – 2 rows…

Is this the “normal” behaviour?

Is there a solution?

Should I report a bug?

This is with LibO 4.4.2.2 in Ubuntu 15.04

I initially only noticed the problem in LibO & posted on the LibO forum, but now see similar behaviour with other applications after cycling unmax>max>close>open>unmax:
- Thunderbird - windows shift to screen top & shrink each cycle.
- Firefox - windows shift to screen base & shrink each cycle.
- Gedit - windows lose height & move to screen base (first cycle) then swell to nearly full screen (subsequent cycles!).

On the same PC under Windows 8.1, LibO Calc windows keep their size & position OK...

---

### Post by 2CV67 on 2016-01-09
Further information:

1. I am using the default Ambiance theme, with Menus in the window's title bar.

2. In normal use, I don't actually go deliberately through the unmax>max>close>open>unmax cycle with any one Calc file, but if I close my usual file unmaximized, then the next Calc file gets opened unmaximized, so I maximize it to use it, then close it, so next time I open the usual file, it starts off maximized...

---

### Post by vasa1 on 2016-01-09
Have you tried with another window manager?

---

### Post by 2CV67 on 2016-01-09
> **vasa1 said:**
> Have you tried with another window manager?
You mean move away from Unity & towards Gnome or something?

On my old (very old) PC I used Lubuntu & XFCE but that was a continuing adventure & I wanted to get "mainstream" when I got a newer PC capable of running Unity.

Seems like a very major change to fix a small irritation...

Or does "window manager" mean something else?

---

### Post by vasa1 on 2016-01-09
> **2CV67 said:**
> You mean move away from Unity & towards Gnome or something?

On my old (very old) PC I used Lubuntu & XFCE but that was a continuing adventure & I wanted to get "mainstream" when I got a newer PC capable of running Unity.

Seems like a very major change to fix a small irritation...

Or does "window manager" mean something else?

The window manager affects precisely the aspect you've reported. One can have more than one window manager installed and switch between them from the terminal. I don't use Unity but have the impression that things are tightly integrated. But with other DEs such as Lubuntu, MATE, Xubuntu, switching between window managers *in the same session* isn't traumatic. [MATE even provides a GUI]("https://ubuntu-mate.community/t/mate-tweak-will-support-more-window-managers/1349") to let users switch between WMs.

My point was that if you couldn't reproduce the irritation with another window manager, that *may* point to a bug in Compiz (which I think is Unity's WM+compositor).

---

### Post by 2CV67 on 2016-01-10
Sorry, vasa1, I didn't mean to belittle your original suggestion to try another window manager!
But even after a lot of G**gling "Ubuntu window manager" I was still not sure whether it was the same thing as "Desktop Environment" or (as I now think) just a part of that.
And my problem with Calc is not significant enough to push me from Unity to, say Lubuntu for everyday work.

But I am certainly prepered to add another Desktop Environment to my backup 14.04LTS partition (which is only for emergencies & playing around) as a diagnostic step.
I will report back on that...

I would be interested to know what behaviour anybody else sees with unmaximized window cycling, and with which DE's or WM's.

Should I be able to influence unmaximized window behaviour in the Unity (Compiz?) WM parameters?

Thanks again for your help!

---

### Post by 2CV67 on 2016-01-10
Well, that was easier than I expected - I already had XFCE available in my 14.04LTS partition!
No doubt from some previous test which I have forgotten...

EDIT - THESE RESULTS ARE WITH XFCE
Results with a Calc file:
1. An unmaximised window can be maximised & unmaximised indefinitely without the unmaximized window losing it&#8217;s chosen size & position on the screen.
2. An unmaximised window can be closed & reopened indefinitely with no problem.
3. If an unmaximized window is maximized, then closed, then reopened, then unmaximized, then it stays at the maximized size!!! In fact it fills the screen width so well you can't "find" the edge to pull it back & have to shift the window before you can reduce the width again.

So - even worse than Unity/Compiz & surely unacceptable?
These symptoms brought on a sense of déjà-vu & sure enough I had been there a couple of years ago when I was using XFCE on my previous feeble PC, then with 12.04 & 13.10.
I posted about it on the OOo forum here:
[https://forum.openoffice.org/en/forum/viewtopic.php?p=307160#p307160](https://forum.openoffice.org/en/forum/viewtopic.php?p=307160#p307160)

Is nobody else bothered by this behaviour, or does nobody else have it?

---

### Post by vasa1 on 2016-01-10
> **2CV67 said:**
> ...

Results with a Calc file:
...
3. If an unmaximized window is maximized, then closed, then reopened, then unmaximized, then it stays at the maximized size!!! In fact it fills the screen width so well you can't "find" the edge to pull it back & have to shift the window before you can reduce the width again.
...
I use the default window manager supplied with Lubuntu 14.04 LTS and that is Openbox 3.5.2. My LibreOffice is version 4.4.5.2 (direct from libreoffice.org and not from Ubuntu's repos).

Openbox doesn't have an "unmaximise" option but it has a "restore" option which, I'm assuming is the same thing.

I can't reproduce point 3.

---

### Post by mc4man on 2016-01-10
This would be a bug, easily reproduced. What's happening is when restored it's loosing vertical height amounting to the window deco, ie. 28px.
(- you could check that with xwininfo (xwininfo -all), check the window height from one to the next, ect., likely is shrinking by 28 px.

As far as filing a bug doing so on 15.04 is worthless as it's almost EOL, on 15.10 almost worthless. You should do so from a 16.04 install & do so during the dev, not after release.
(- note that this has occurred from time to time in the past on an app specific basis so what's happening isn't unique or unknown in that regard.

---

### Post by 2CV67 on 2016-01-10
Exactly right, mc4man! (Talking now about Calc in Unity, not in XFCE).

The window drops 28 pixels & loses 28 pixels of height.

Before cycle:
```
xwininfo: Window id: 0x3e00064 "tes.ods - LibreOffice Calc"

  Root window id: 0x2c3 (the root window) (has no name)
  Parent window id: 0xe011a6 (has no name)
     1 child:
     0x3e00065 (has no name): ()  1x1+-1+-1  +58+621

  Absolute upper-left X:  59
  Absolute upper-left Y:  [COLOR="#FF0000"]622[/COLOR]
  Relative upper-left X:  0
  Relative upper-left Y:  0
  Width: 1189
  Height: [COLOR="#FF0000"]285[/COLOR]
  Depth: 24
  Visual: 0x21
```

After cycle:
```
xwininfo: Window id: 0x4400064 "tes.ods - LibreOffice Calc"

  Root window id: 0x2c3 (the root window) (has no name)
  Parent window id: 0xe024a4 (has no name)
     1 child:
     0x4400065 (has no name): ()  1x1+-1+-1  +58+649

  Absolute upper-left X:  59
  Absolute upper-left Y:  [COLOR="#FF0000"]650[/COLOR]
  Relative upper-left X:  0
  Relative upper-left Y:  0
  Width: 1189
  Height: [COLOR="#FF0000"]257[/COLOR]
  Depth: 24
  Visual: 0x21
```

If it is a known problem, then is there aleady a bug report I can join?

What you say about filing a bug report is worrying.
As a deliberate late-adopter, I am never going to report any problem in the development or early-life phase (that's why I am a late adopter!).
But problems which continue through version after version deserve attention too, don't they?

Thanks again (both) for your input!

---

### Post by mc4man on 2016-01-10
By known I mean this has happened in the past to specific apps, not in general.
I've got 16.04 so maybe will file a bug & link here.

The reason for filing in 16.04 during dev is that after release updates that aren't security related become much harder to get thru, usually they require extra steps & still may not be accepted. See - 
[https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)

In this case it's 50-50 there'll be a fix as it only affects calc in an ubuntu session. Some apps that save position & or size get 'thrown' by the fact that when max'ed the window deco merges into the unity panel. This affects them when trying to restore to the previous size.

---

### Post by 2CV67 on 2016-01-10
Thanks for the explanations & I certainly understand the risk involved in making changes!

I am not pretending this problem is vital or urgent, & I wouldn't expect a running fix in a current release.

I did mention at the end of my first post:
> I initially only noticed the problem in LibO ... but now see similar behaviour with other applications after cycling unmax>max>close>open>unmax:
- Thunderbird - windows shift to screen top & shrink each cycle.
- Firefox - windows shift to screen base & shrink each cycle.
- Gedit - windows lose height & move to screen base (first cycle) then swell to nearly full screen (subsequent cycles!).

It's just that I use lots of Calc files, some maximized & some unmaximized, so hit the problem very frequently with Calc.

Thanks again - especially if you do get round to filing a bug report & getting a fix one day!

---

### Post by mc4man on 2016-01-10
This also happens in LO writer, maybe all LO apps?
writer > open a docu in a window, max., close, reopen docu, restore. window loses 28 px

---

### Post by vasa1 on 2016-01-10
> **mc4man said:**
> ... Some apps that save position & or size get 'thrown' by the fact that when max'ed the window deco merges into the **unity panel**. This affects them when trying to restore to the previous size.
Okay, so that seems Unity-specific though OP posted elsewhere about something similar with Xfce.

---

### Post by 2CV67 on 2016-01-11
Yes, I just edited my #7 post to clarify that that post concerned results with XFCE which are different (worse) than with Unity.
Maybe we should keep this thread to Unity?

---

### Post by 2CV67 on 2016-03-03
> **mc4man said:**
> By known I mean this has happened in the past to specific apps, not in general.
I've got 16.04 so maybe will file a bug & link here.

Did you manage to file a bug for 16.04?

I confirm I have the same problem in 15.10

---

