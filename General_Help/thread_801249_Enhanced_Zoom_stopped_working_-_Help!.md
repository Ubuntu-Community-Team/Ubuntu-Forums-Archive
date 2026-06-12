---
title: "Enhanced Zoom stopped working - Help!"
date: 2008-05-20
forum: General Help
---

### Post by vapotrini on 2008-05-20
Hey guys, a few weeks back my enhanced zoom totally stopped working. Since I was installing all sorts of stuff I assumed that something, somewhere down the line messed up the plug in. I thought no big deal as I knew I was going to reformat my entire drive to start over fresh. 

Well today I reformatted and reinstalled hardy. Before I installed ANYTHING else I started checking to make sure everything was working fine, everything was EXCEPT guess what, the enhanced zoom, wtf!? A fresh install and same result???

I've done numerous searches for a cure to this but haven't had any luck. I know about the multiple accounts bug but I only have one account, so it's not that. I'm totally stumped and would really like to get this feature working as it was one of my favorites. 

Does anyone know what I can do to get this working again?

---

### Post by bobjenkins on 2008-05-20
Are you talking about the zoom where you hold (super/windows key) and play around with the mouse wheel?

If so strange that it wouldn't work after a brand new install

I read somewhere that it might be a graphics driver issue, try that:) Goodluck ill post back ifI find anything else
--- EDIT
pulled this off a post

two things...

check system> admin>users and groups

make sure tha account has nearly the same accesses that the main account has (leave out admin functions if you want)

check system> preferenced> advanced desktop settings

make sure enhanced zoom/ magnify is on

if you dont have that menu you will need to install it

sudo apt-get install ccsm


----------
compiz-fusion has an enhanced zoom, I do not know if you have that installed already:)

---

### Post by vapotrini on 2008-05-20
Thanks for the response, I tried everything you suggested already... still no luck. 

Anyone else have an other ideas?

---

### Post by bobjenkins on 2008-05-20
If you look in compiz there is an enhanced zoom and at the very end (under all) there is just a desktop zoom, I have tried both and both seem to do the same thing (zoom with super+mousewheel) you could try the other one, just a thought goodluck

---

### Post by vapotrini on 2008-05-20
Thanks for the response bob, I tried your idea and eventually I got it working. At first it locked up my computer... but after I rebooted it all started working again. THANK YOU very much!!!

---

### Post by wild_oscar on 2008-05-29
I have the same problem. Posted a bug in launchpad: [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/235768]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/235768")

Desktop zoom also doesn't work and seems to freeze the computer sometimes.

Enhanced Desktop zoom workedlike a charm before upgrading to Hardy from Gutsy!

---

### Post by vapotrini on 2008-05-31
I finally figured out what was wrong with mine. Twinview. Seems this plug in won't work with multiple displays... at least not for me. It was driving me insane that I couldn't get it working.

---

### Post by wild_oscar on 2008-05-31
> **vapotrini said:**
> I finally figured out what was wrong with mine. Twinview. Seems this plug in won't work with multiple displays... at least not for me. It was driving me insane that I couldn't get it working.

Oh, lord! Thank you very much, vapotrini. That's precisely it!

I had the issue posted [here]("http://forum.compiz-fusion.org/showthread.php?p=59248#post59248") and [here]("http://ubuntuforums.org/showthread.php?t=811973")

---

### Post by kshane on 2008-05-31
After reading the original post, I played around with this plugin for the first time.  I love it!  But, I also found that it will not workwhen the "Shelf" plugin is enabled...  At least on my machine.

Kevin

---

### Post by vapotrini on 2008-05-31
> **wild_oscar said:**
> Oh, lord! Thank you very much, vapotrini. That's precisely it!

I had the issue posted [here]("http://forum.compiz-fusion.org/showthread.php?p=59248#post59248") and [here]("http://ubuntuforums.org/showthread.php?t=811973")

Glad to hear I at least helped someone. I know how frustrating it can be, believe me.

---

### Post by Fyda on 2008-05-31
> **vapotrini said:**
> Well today I reformatted and reinstalled hardy. Before I installed ANYTHING else I started checking to make sure everything was working fine, everything was EXCEPT guess what, the enhanced zoom, wtf!? A fresh install and same result???It's not clear here whether you mean a fresh install with a new */home* directory, or a fresh install with a preserved */home* directory. If the latter, it'd suggest that you still have some stale settings which (for whatever reason) don't work with the new version. It's also not clear if everyone else with this problem has exactly the same situation (of having a brand new installation).
> **bobjenkins said:**
> I read somewhere that it might be a graphics driver issue, try that:)Where did you read that?
> **bobjenkins said:**
> make sure tha account has nearly the same accesses that the main account has (leave out admin functions if you want)What is this meant to accomplish, exactly?
> **bobjenkins said:**
> make sure enhanced zoom/ magnify is on
**Enhanced Zoom Desktop** (Ezoom) is the relevant plugin here. **Magnifier** has nothing to do with Ezoom and it doesn't matter whether you have it enabled or disabled.
> **bobjenkins said:**
> compiz-fusion has an enhanced zoom, I do not know if you have that installed alreadySince Ubuntu Hardy ships with Compiz and Compiz Fusion (at least, plugins-main and plugins-extra), it is highly unlikely that anyone with a fresh install would *not* have Ezoom (it's in plugins-main).
> **bobjenkins said:**
> If you look in compiz there is an enhanced zoom and at the very end (under all) there is just a desktop zoom, I have tried both and both seem to do the same thing (zoom with super+mousewheel)Almost. Ezoom allows working mouse input (by either zooming and transforming the screen, or drawing a fake cursor). The older **Desktop Zoom** does not have this feature, but it allows selecting a region with the mouse to zoom into (which the version of Ezoom in Hardy does not do). There is a large enough difference in functionality for users to prefer one over the other.
> **vapotrini said:**
> I finally figured out what was wrong with mine. Twinview. Seems this plug in won't work with multiple displays... at least not for me.According to the author of Ezoom, it's highly unlikely that TwinView would be responsible, since he developed and uses the plugin with TwinView on. It also works for him on his Ubuntu Hardy installation with the stock version of Compiz (with TwinView, of course). See the bug tracker entry **[here](http://bugs.opencompositing.org/show_bug.cgi?id=956)**.

It's marginally possible if there's some misconfiguration in TwinView (or Ubuntu has applied its own patch that affects Compiz or TwinView), but the point is that so far nobody has come up with any solid proof that this problem is actually TwinView's fault, let alone that Ezoom completely won't work on TwinView.

If you can provide more detailed information about your video card, drivers and configuration, then that would be helpful for tracking down the cause, since a non-working plugin isn't much to look at in terms of troubleshooting.

It may also be helpful for affected users to export their Compiz profile (in the *Preferences* section in CCSM; the exported file can be posted to a site like [www.pastebin.com](www.pastebin.com)), so that others can import those exact settings and test them to see if this is a settings issue. (The basic premise: if the profile can produce the same problem on another machine that doesn't have TwinView, then the issue is not TwinView. On the other hand, if the profile doesn't cause the problem on another machine with TwinView, then the issue is with either the specific version of TwinView, or the specific TwinView configuration on the machine with the problem.)

---

### Post by vapotrini on 2008-06-01
> **Fyda said:**
> It's not clear here whether you mean a fresh install with a new */home* directory, or a fresh install with a preserved */home* directory. If the latter, it'd suggest that you still have some stale settings which (for whatever reason) don't work with the new version. It's also not clear if everyone else with this problem has exactly the same situation (of having a brand new installation).
Where did you read that?
What is this meant to accomplish, exactly?

**Enhanced Zoom Desktop** (Ezoom) is the relevant plugin here. **Magnifier** has nothing to do with Ezoom and it doesn't matter whether you have it enabled or disabled.
Since Ubuntu Hardy ships with Compiz and Compiz Fusion (at least, plugins-main and plugins-extra), it is highly unlikely that anyone with a fresh install would *not* have Ezoom (it's in plugins-main).
Almost. Ezoom allows working mouse input (by either zooming and transforming the screen, or drawing a fake cursor). The older **Desktop Zoom** does not have this feature, but it allows selecting a region with the mouse to zoom into (which the version of Ezoom in Hardy does not do). There is a large enough difference in functionality for users to prefer one over the other.
According to the author of Ezoom, it's highly unlikely that TwinView would be responsible, since he developed and uses the plugin with TwinView on. It also works for him on his Ubuntu Hardy installation with the stock version of Compiz (with TwinView, of course). See the bug tracker entry **[here](http://bugs.opencompositing.org/show_bug.cgi?id=956)**.

It's marginally possible if there's some misconfiguration in TwinView (or Ubuntu has applied its own patch that affects Compiz or TwinView), but the point is that so far nobody has come up with any solid proof that this problem is actually TwinView's fault, let alone that Ezoom completely won't work on TwinView.

If you can provide more detailed information about your video card, drivers and configuration, then that would be helpful for tracking down the cause, since a non-working plugin isn't much to look at in terms of troubleshooting.

It may also be helpful for affected users to export their Compiz profile (in the *Preferences* section in CCSM; the exported file can be posted to a site like [www.pastebin.com](www.pastebin.com)), so that others can import those exact settings and test them to see if this is a settings issue. (The basic premise: if the profile can produce the same problem on another machine that doesn't have TwinView, then the issue is not TwinView. On the other hand, if the profile doesn't cause the problem on another machine with TwinView, then the issue is with either the specific version of TwinView, or the specific TwinView configuration on the machine with the problem.)


"According to the author it is highly unlikely that twinview would be responsible" haha... Are you SERIOUS?!?!

So wait... let's believe EVERYTHING authors say why don't we. I've written programs before, I actually know 3 languages. And I'm not talking about hacking plugins, I mean REAL languages. I HIGHLY doubt any self respecting programmer would make such claims, claims of a 'full proof' plugin. Nothing is perfect and whether you believe it or not, Ezoom isn't either. The resolution of my monitor made it impossible for me to install hardy wihtout having my plasma plugged in hence why I didn't know why it wasn't working. On top of which someone else confirmed my finding and yet here you are defending something which you obviously know very little about. Here what... :guitar: GOOD LUCK to you!

---

### Post by Fyda on 2008-06-01
> **vapotrini said:**
> I HIGHLY doubt any self respecting programmer would make such claims, claims of a 'full proof' plugin. Nothing is perfect and whether you believe it or not, Ezoom isn't either.I never claimed Ezoom was perfect. And neither did the author. If you can point to an actual part of my post that claimed this, go ahead.

I was merely pointing out that this thread was severely lacking in *detailed information*. If you can produce that information, then you can *contribute* towards a fix. Of course, the alternative is for you to continue insisting that TwinView is the problem without producing actual debug logs, configuration files or, well, anything that substantiates your claim besides "it doesn't work with TwinView enabled". I do not care how much programming prowess you can boast of; that is irrelevant to the fact that you have failed to provide meaningful data.

> **vapotrini said:**
> On top of which someone else confirmed my finding and yet here you are defending something which you obviously know very little about.And what exactly do I "know very little about"?

It would also be much more constructive if you could address the rest of my post instead of jumping into a grossly misdirected personal attack. Did I ever attack you? No, I asked you to provide more information. If you feel this is an insult to your credibility or competence, well, I'm sorry I made you feel that way. It was never my intention.

Clearly, you do not appreciate it when people attempt to apply more thorough criteria to debugging something. Why you had to react with such hostility and rudeness is beyond me.

---

### Post by wild_oscar on 2008-06-01
> **vapotrini said:**
> "According to the author it is highly unlikely that twinview would be responsible" haha... Are you SERIOUS?!?!

So wait... let's believe EVERYTHING authors say why don't we. I've written programs before, I actually know 3 languages. And I'm not talking about hacking plugins, I mean REAL languages. I HIGHLY doubt any self respecting programmer would make such claims, claims of a 'full proof' plugin. Nothing is perfect and whether you believe it or not, Ezoom isn't either. The resolution of my monitor made it impossible for me to install hardy wihtout having my plasma plugged in hence why I didn't know why it wasn't working. On top of which someone else confirmed my finding and yet here you are defending something which you obviously know very little about. Here what... :guitar: GOOD LUCK to you!

As another user with the same issue, I'd suggest that you post your bug in the bugtracker at [http://bugs.opencompositing.org/show_bug.cgi?id=956]("http://bugs.opencompositing.org/show_bug.cgi?id=956") so we can all discover the root of the problem.

---

### Post by wild_oscar on 2008-06-04
Bug submitted:

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/235768]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/235768")

---

### Post by Plasma_NZ on 2008-06-06
ok i had this problem, and this is how i fixed it...

went into ccsm - then went to "Desktop Cube" - in the general tab i selected "multi output mode" - and wahla ! working again...

Hope this helps.

---

### Post by wild_oscar on 2008-06-06
> **Plasma_NZ said:**
> ok i had this problem, and this is how i fixed it...

went into ccsm - then went to "Desktop Cube" - in the general tab i selected "multi output mode" - and wahla ! working again...

Hope this helps.

What option did you choose in "multiple output mode"? Did that enable enhanced zoom after/without X restart?
Setting the option to "multiple cubes" did not work for me. Still don't have ezoom working.

---

### Post by Plasma_NZ on 2008-06-06
> **wild_oscar said:**
> What option did you choose in "multiple output mode"? Did that enable enhanced zoom after/without X restart?
Setting the option to "multiple cubes" did not work for me. Still don't have ezoom working.

I selected "Multipule Cubes" and then tested zoom and nearlly shat myself cause it worked :D Good Luck..

---

### Post by Plasma_NZ on 2008-06-08
> **wild_oscar said:**
> What option did you choose in "multiple output mode"? Did that enable enhanced zoom after/without X restart?
Setting the option to "multiple cubes" did not work for me. Still don't have ezoom working.

So - did it solve your problem..? sure others would also like to know aswell..

---

### Post by wild_oscar on 2008-06-09
> **Plasma_NZ said:**
> I selected "Multipule Cubes" and then tested zoom and nearlly shat myself cause it worked :D Good Luck..

Selecting "Multiple cubes" did not work for me. Enhanced Zoom still doesn't work with that option.

---

### Post by wild_oscar on 2008-06-12
Any news on this issue?

[https://bugs.launchpad.net/ubuntu/+s...iz/+bug/235768]("https://bugs.launchpad.net/ubuntu/+s...iz/+bug/235768")

---

### Post by terdon on 2009-12-01
Well, I found a kind of workaround. I get this problem with an external screen connected to my laptop (twinview). Starting X with the external screen unplugged and then connecting it when X is up and running lets me zoom.

It breaks if I reload compiz though...

---

### Post by Cuco3 on 2010-04-03
> **Plasma_NZ said:**
> ok i had this problem, and this is how i fixed it...

went into ccsm - then went to "Desktop Cube" - in the general tab i selected "multi output mode" - and wahla ! working again...

Hope this helps.Thanks for the fix :D

---

### Post by TheNerdAL on 2010-04-03
Mark [SOLVED] if solved. :)

---

