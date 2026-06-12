---
title: "Sometimes things in system tray open minimized"
date: 2015-03-14
forum: General Help
---

### Post by Roasted on 2015-03-14
Hello friends. On 14.04.2 here and I noticed some things open minimized. I haven't seen a real pattern for it and it happens with multiple things. Sometimes it's fine, other times, minimized from the get-go. I uploaded a video to youtube as that'll show what I mean far better.

Has anybody seen this? Or have any idea how to make things not auto-minimize?

[http://youtu.be/LuLRvG3TR_o](http://youtu.be/LuLRvG3TR_o)

---

### Post by kerry_s on 2015-03-14
they don't look minimized, just in the background, behind the forward facing app. it's a feature :)

---

### Post by Roasted on 2015-03-14
LOL. Quite an irritating "feature". I looked around online but couldn't find anything specific to this. No talk or anything even slightly related unless I just struck out with my searches. I fired up 15.04 in a virtual machine, same thing happened with almost zero effort. 

Maybe it's time for a bug report... surely I was hoping there'd be a quick tweak for this. :(

---

### Post by mc4man on 2015-03-14
I wouldn't call it a feature. Some apps thru their indicator or systray icon have option to always open 'minimized', but obviously that's not your case here. 
Whether or not it'll be helpful in this case it wouldn't hurt to change the focus prevention level in compiz from the default of low to off. (what the default should be.

Found in ccsm > General Options > Focus and Raise Behavior

---

### Post by Roasted on 2015-03-14
> **mc4man said:**
> I wouldn't call it a feature. Some apps thru their indicator or systray icon have option to always open 'minimized', but obviously that's not your case here. 
Whether or not it'll be helpful in this case it wouldn't hurt to change the focus prevention level in compiz from the default of low to off. (what the default should be.

Found in ccsm > General Options > Focus and Raise Behavior

I wonder if there's a unity-tweak-tool equivalent. I found some similar settings in the tweak tool but what I've tinkered with so far hasn't changed the behavior I'm seeing (though while similar, these changes I made were not identically worded). I'd prefer to use the unity-tweak-tool over ccsm if possible, or even dconf, as I've had enough issues with ccsm before that I like to avoid it if possible. :P

---

### Post by kostkon on 2015-03-14
It's [a known issue]("https://bugs.launchpad.net/ayatana-design/+bug/627195").

---

### Post by mc4man on 2015-03-14
Don't think that tweak tool does this, nor could dconf-editor as most compiz settings don't have schemas so they only show in the editor if changed from default values.

So to test you can use dconf write 
```
dconf write  /org/compiz/profiles/unity/plugins/core/focus-prevention-level 0
```
log out/in & see.
If inclined to set back to the crappy default of low then - 
dconf write  /org/compiz/profiles/unity/plugins/core/focus-prevention-level 1

---

### Post by Roasted on 2015-03-14
> **mc4man said:**
> Don't think that tweak tool does this, nor could dconf-editor as most compiz settings don't have schemas so they only show in the editor if changed from default values.

So to test you can use dconf write 
```
dconf write  /org/compiz/profiles/unity/plugins/core/focus-prevention-level 0
```
log out/in & see.
If inclined to set back to the crappy default of low then - 
dconf write  /org/compiz/profiles/unity/plugins/core/focus-prevention-level 1

That... seems to have worked? By worked I mean I've flipped between 0 and 1 (of those two commands) and each time, 0 had no issues, but 1 I could replicate the issue with relative ease. I haven't exactly used it for hours/days/etc but so far, so good.

I guess essentially creating that rule within dconf adjusts the parameter in compiz accordingly, yes? If so, that baffles me. If you read the bug report, there are different "sub-bugs" (I suppose?) of the applications that were affected, such as Rhythmbox, Empathy, etc. It confuses me over how I was having issues with, well, pretty much anything; my-weather-indicator, ownCloud client, network manager, etc., and suddenly this one thing fixed it - meanwhile on that bug report, things were split off to accommodate each item. Is this, do I dare say, a hackish workaround? I mean, if it's not a hackery workaround and it (seemingly) addresses every application I ever had issues with, why on earth would Unity not auto-push this dconf parameter and just... live on happily ever after?

In short, I have to assume the 'fix' is deeper than this one dconf entry, however from what I can tell, it seems to work just fine. 

Eh?

---

### Post by mc4man on 2015-03-14
ubuntu/unity has had an ongoing issue with window focus for some time. There was a 2 line change to gtk that resolved almost all of them but they decided to fix on an individual basis, some of which you see reflected in that bug report. 

I've found that any remaining issues could also be fixed by the settings change in compiz so have used that rather than rebuild gtk.  A common one here used to be in Firefox's download window > r. click on a dl > open containing folder, it  would often open the nautilus window without focus.  
So between the individual fixes over time & the compiz option change I no longer see any focus problems.
Whether the compiz setting was behind many of the previous issues don't know, may of been.

In any event the option has no real use being enabled, at least for most users. (there are actually 4 levels from Off to Very High.
Have had a bug on for a while, don't really expect any action though it really should be changed
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1403140](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1403140)

---

### Post by Roasted on 2015-03-14
> **mc4man said:**
> In any event the option has no real use being enabled, at least for most users. (there are actually 4 levels from Off to Very High.
Have had a bug on for a while, don't really expect any action though it really should be changed
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1403140](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1403140)

Hi there. Thanks for your response, although I am mildly confused by your response. I'm hoping you could clarify/elaborate since, well, I'm a curious person. :)

You mention above that the option has no real use for most users being enabled, although you refer to it as a 'bug' and mention it really should be changed (which then suggests it does have benefit being enabled by default for users). I'm a little lost... which is it? :P

Thanks again!

---

### Post by mc4man on 2015-03-14
Well the option is enabled by default, at a setting of "Low" (1)
The bug is that the default setting should be "Off" (0) as it causes focus issues being enabled & has no apparent positive effect/use for most users. So what should be changed is that the default setting should be set to  Off.

(- many of the settings in compiz were simply inherited, not by actual testing of their viability or desirability  over time & other changes like unity, GLES,  ect.

---

### Post by Roasted on 2015-03-14
Thanks for your assistance and clarification. I have been using the laptop most of the evening without any issue. :)

---

### Post by mc4man on 2015-03-14
Hopefully things stay good. 
Sometimes simple solutions  to bugs  proves elusive.

---

