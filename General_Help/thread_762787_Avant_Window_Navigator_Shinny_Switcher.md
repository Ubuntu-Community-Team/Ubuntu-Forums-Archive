---
title: "Avant Window Navigator Shinny Switcher"
date: 2008-04-22
forum: General Help
---

### Post by jimbo99 on 2008-04-22
I have a new situation, which started about a week ago.  Prior to that I had Avant Window Navigator running just fine.  

The problem is that once I load the "shiny switcher" applet it shows 5 desktops and when I click on any  of them the desktop goes blank leaving just the wallpaper.  I can do nothing at this point except alt+ctl+backspace to reload the desktop.

If I don't use the shiny switcher it works fine.  I tried one of the other desktop switchers and it worked for a while though it looked crummy.  Now it doesn't work either.

Any ideas?  I like to have the switcher to switch desktops.  I demo linux a lot to customers and want them to see the best of the world of linux.  So, it is important that I be able to keep going.

Any help would be greatful.  Bug reports on their product generally results in some very braindead responses from the developers, so I'm posting here.

---

### Post by moonbeam on 2008-04-22
> **jimbo99 said:**
> I have a new situation, which started about a week ago.  Prior to that I had Avant Window Navigator running just fine.  

The problem is that once I load the "shiny switcher" applet it shows 5 desktops and when I click on any  of them the desktop goes blank leaving just the wallpaper.  I can do nothing at this point except alt+ctl+backspace to reload the desktop.

If I don't use the shiny switcher it works fine.  I tried one of the other desktop switchers and it worked for a while though it looked crummy.  Now it doesn't work either.

Any ideas?  I like to have the switcher to switch desktops.  I demo linux a lot to customers and want them to see the best of the world of linux.  So, it is important that I be able to keep going.

Any help would be greatful.  Bug reports on their product generally results in some very braindead responses from the developers, so I'm posting here.

As the shinyswitcher developer I'm interested in getting this debugged :-)  And on this particular case I'm not convinced you will get a less  "braindead" response here than in one of our bugs...

Anyway, if you do feel like filing a bug I would suggest including the following info.  

Distribution and version.
Awn and awn-extras repo with version (or what source version used).
The other switcher used.
Window manager in use.
Desktop environment in use if it's not obvious from the window manager
Run awn from a terminal put the terminal into the bug report.
Any other relevant info.

It sounds like an interesting issue and I can think of a few possibilities... but I would really need more information.

[https://bugs.launchpad.net/awn-extras/](https://bugs.launchpad.net/awn-extras/)

thanks,

---

### Post by jimbo99 on 2008-04-24
I can say with all honesty that what I have received in response to report about Avant Window Navigator have pretty much been braindead pass the buck back to the user responses.  As a general rule I feel all developers should "take responsibility for your code and for your problems and accept them as your problems that are interfering with your customers (the user), even if the user isn't paying you directly--translation:  don't pass the buck".

I have it installed on many computers, not just one.  I have linux installed on many computers and am satisfied with it, and actually very pleased.

I have removed every file related to Avant Window Navigator by hand; everyone I could find, that is.

Reinstalled it.  Same problem.

This morning found that the Avant Window Navigator (even without the shiny switcher activated) would cause the icons in AWN to disappear.

--and keep in mind that over the past several days there have been a lot of updates to the applets portion of AWN.

I noticed earlier that the shiny switcher now had 5 desktops instead of 4.  I had made no changes to the number of desktops and the compiz settings manager confirmed I had only 4.  When I checked out the more dull versions of the switchers they too had 5.

I'm somewhat holding off on addressing any of these issues as Hardy was just released.  If feedback for desktop boxes is positive I'll most likely back up my home folder and wipe/reinstall with 8.04.  If it isn't very good then I'll hold off and maybe examine this in more detail.

---

### Post by moonbeam on 2008-04-24
> **jimbo99 said:**
> I can say with all honesty that what I have received in response to report about Avant Window Navigator have pretty much been braindead pass the buck back to the user responses.  As a general rule I feel all developers should "take responsibility for your code and for your problems and accept them as your problems that are interfering with your customers (the user), even if the user isn't paying you directly--translation:  don't pass the buck".

I have it installed on many computers, not just one.  I have linux installed on many computers and am satisfied with it, and actually very pleased.

I have removed every file related to Avant Window Navigator by hand; everyone I could find, that is.

Reinstalled it.  Same problem.

This morning found that the Avant Window Navigator (even without the shiny switcher activated) would cause the icons in AWN to disappear.

--and keep in mind that over the past several days there have been a lot of updates to the applets portion of AWN.

I noticed earlier that the shiny switcher now had 5 desktops instead of 4.  I had made no changes to the number of desktops and the compiz settings manager confirmed I had only 4.  When I checked out the more dull versions of the switchers they too had 5.

I'm somewhat holding off on addressing any of these issues as Hardy was just released.  If feedback for desktop boxes is positive I'll most likely back up my home folder and wipe/reinstall with 8.04.  If it isn't very good then I'll hold off and maybe examine this in more detail.

I won't argue with you perceptions of how we handle our bugs... it is probably a zero sum exercise :-)

That being said, I do encourage you to file a bug report if your initial approach doesn't bring a resolution.  

I will say that it is very interesting that other switchers are showing the same issue...  shinyswitcher definitely has no resemblance internally to any of the other awn switchers.

Thanks,

---

