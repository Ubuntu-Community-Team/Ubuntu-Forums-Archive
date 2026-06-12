---
title: "Lightning plug-in for Thunderbird not working?"
date: 2013-10-26
forum: General Help
---

### Post by bug67 on 2013-10-26
Running Thunderbird 24.0 with the Lightning 2.6.1 add-on in Ubuntu 13.10.  When I go to add a new calendar, calendar is grayed out and I cannot select it.  Also cannot switch between day, week or month views in the calendar tab.  And finally, the calendar side pane will not stay visible after Thunderbird has been quit and relaunched.  Any ideas?

:popcorn:

---

### Post by vanadium on 2013-10-26
I suddenly had your issue yesterday, and I still do not now how it happened in the first place. Resolution: remove Lightning 2.6.1. and install Lightning 2.6.0. See [https://blog.mozilla.org/calendar/](https://blog.mozilla.org/calendar/)

---

### Post by bug67 on 2013-10-26
Thanks, vanadium!  Installing Lightning 2.6 fixed it.  :)

---

### Post by vanadium on 2013-10-26
As I noticed five minutes ago, that is not the complete fix. In Edit - Preferences, Advanced: Update tab, uncheck "Installed Add-ons", or it will be broken again within a couple of days. This explains my "I suddenly had your issue yesterday, and I still do not now how it happened in the first place."

---

### Post by box02-0 on 2013-10-26
Same problem. I will try installing Lightning 2.6.0. How will we know when 2.6.1 will be operational??

Thanks,

M...

---

### Post by &amp;hiu)(@% on 2013-10-27
It could be that Mozilla is working on this issue right now. From this page:
[https://addons.mozilla.org/en-US/thunderbird/addon/lightning/versions/](https://addons.mozilla.org/en-US/thunderbird/addon/lightning/versions/)
I can see that there is a newer beta version available, although it's not considered reliable and stable so far.
I haven't tried the beta-version myself, but maybe it provides a solution to this error?

---

### Post by vanadium on 2013-10-27
Don't bother, and stick with 2.6. Once Thunderbird 24.0.1 is pushed towards the Ubuntu systems, upgrade to the latest stable version (which currently is the 2.6.1). What we see now is an exceptional unexpected situation. Normally, it should be fine always to use the latest stable plugin. Not this time, though.

---

### Post by mustang on 2013-10-28
> **vanadium said:**
> I suddenly had your issue yesterday, and I still do not now how it happened in the first place. Resolution: remove Lightning 2.6.1. and install Lightning 2.6.0. See [https://blog.mozilla.org/calendar/](https://blog.mozilla.org/calendar/)

Thank you!

---

### Post by trindflo on 2013-11-01
Thunderbird 24.1.0 just installed for me.  I had reverted Lightning to 2.6 and it stopped working again.  This time I deleted the 2.6 version and got the announcement that as of 2.6.2 Lightning is built in.  So I guess you need to delete any installed versions in order to activate the built in version.

---

### Post by vanadium on 2013-11-01
I now uninstalled the addons, and then reinstalled them through the software centre: xul-ext-lightning, xul-ext-gdata-provider if you use google calendar ... This way, versions automatically will match, as the updates are pushed though the regular software channel, and and on our systems after some checking from the Ubuntu developpers. Although what happened now probably was quite exceptional, working through the official repo should still be more fool proof.

---

### Post by Panawe on 2013-11-01
Newbie here. 
Same problem, just upgraded to Thunderbird 24.1 and calendar stopped working and I can't reinstall Lighning 2.6.
What's the latest work-around?

---

### Post by plucky on 2013-11-01
> **Panawe said:**
> Newbie here. 
Same problem, just upgraded to Thunderbird 24.1 and calendar stopped working and I can't reinstall Lighning 2.6.
What's the latest work-around?

Just open the addons window and update the Lightening addon which should use the 2.6.2 version.

Good Luck

---

### Post by Panawe on 2013-11-01
Many thanks.

---

### Post by scotw2 on 2013-11-01
Still not working for me with 2.6.2.  Calendar settings are all grayed out.

---

### Post by vanadium on 2013-11-01
Remove the calender plugin you installed using Thunderbird Tools - addons, then install, using the ubuntu software center, xul-ext-lightning. Then you will never again have versions that don't match.

---

### Post by scotw2 on 2013-11-01
Working now.  Thanks!

---

### Post by georgjung on 2013-11-17
Thanks vanadium, this one was helpful. I had the same problem (recurring due to auto updates) and just recalled that I had hit this site again. I just threw away the local plug-in installation and found that xul-ext-[...] was already installed. Lighning back and working!

---

