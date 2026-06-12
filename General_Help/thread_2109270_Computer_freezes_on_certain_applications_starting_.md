---
title: "Computer freezes on certain applications starting up..."
date: 2013-01-27
forum: General Help
---

### Post by msw1 on 2013-01-27
Hello. I have a severe problem. Whenever I launch certain applications, (Steam in particular ALWAYS does this, but I've had one or two other things do it, and I'm sure there is more I haven't tried). my computer freezes. I can move my mouse around, but nothing on my computer works. Flashing | freezes in terminal, etc. This did not happen before. I am using Ubuntu 12.10 64-bit. This does not happen in a 2D Desktop. I am using a AMD Radeon HD 6670 graphics card. Doing terminal tests, my card fully supports all effects. I have ***strong*** reason to believe this is due to mistakes I may have made in CCSM, borderline positive. (Disabling 3D Cube did not do it, btw.) If anyone has experienced said problem before and can answer this, or can just tell from my newbie mistake right off the bat, please do so. Here are pics of my CCSM.

[http://img560.imageshack.us/img560/3246/screenshotfrom201301270.png](http://img560.imageshack.us/img560/3246/screenshotfrom201301270.png)
[http://img543.imageshack.us/img543/3246/screenshotfrom201301270.png](http://img543.imageshack.us/img543/3246/screenshotfrom201301270.png)

If you know how to fix this, tell me! Thanks!

I will provide more information if needed.

I am using Unity 3D.

---

### Post by msw1 on 2013-01-27
Fixed post and title; I can't believe I was so vague, and also completely forgot to post my problem. :mad:

---

### Post by Spyderkid on 2013-01-27
On compiz-config-manager (CCSM) go to prefrences, then click "reset to defaults"

---

### Post by msw1 on 2013-01-27
Thank you! I was able to narrow it down from there and found out the culprit was "D-bus." Now everything works great. ):P

---

### Post by karnev on 2013-01-29
> **Spyderkid said:**
> On compiz-config-manager (CCSM) go to prefrences, then click "reset to defaults"
one addition maybe, in my case unities top and side panels did not came up anymore after compiz "reset to defaults"

I first tried to rename  .compiz-1 and .config/compiz-1 in .compiz-1-BACKUP and .config/compiz-1-BACKUP but that did not seem to sort any affect. (using unity-2d)

Then  tried to activate a terminal (in unity )
ctrl alt T
ccsm
and then reactivate the unity plugin.

Now I have to wait whether or not the freezes still occur. In my case it happens most often when using flash video and audio only streams but also when playing a DVD. still trying to get some grip on error messages:
Gdk-WARNING **: update-notifier: Fatal IO error 11 (Hulpbron is tijdelijk onbeschikbaar) on X server :0.
but update notifier can be replaced by several other programs they all get the same IO error.

---

### Post by karnev on 2013-01-29
unity/compiz still not acting as normal. windows decorations were missing and desktop switching did not work

did a 
unity --reset 
it generated quite some errors but seems to act normal now

---

