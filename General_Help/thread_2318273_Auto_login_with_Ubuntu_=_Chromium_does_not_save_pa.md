---
title: "Auto login with Ubuntu = Chromium does not save passwords. Can I change that?"
date: 2016-03-24
forum: General Help
---

### Post by Roasted on 2016-03-24
Hi friends. I have a slightly unique situation here. While the title screams "bad idea, dude!", here's the situation.

Ubuntu 14.04 running as our HTPC (Unity's display scaling works great here)
User = htpc, which auto logs in (there's an administrator user that's separate and not involved here)

I have two indoor wireless cameras acting as baby cameras. When I navigate to the web interface (which is ZoneMinder, as the cameras are connected to ZM), I log in, hit save password, and I would think I'm good to go. Problem is, once I reboot/power off and then back on/etc and repeat the same process, the user + password is *not* saved.

In contrast, in every other scenario I tried, including with the administrator user on the same computer that requires logging in at the main LightDM login screen, the browser credentials are saved so I just hit enter and boom - I can see if the girls are napping or goofing off, etc.

I uninstalled and reinstalled Chromium. Blasted any trace of its profile in my home directory. Cleared out everything from "the beginning of time". All the same behavior. Based on what I'm seeing, it seems as if the lack of browser-save-password functionality is seemingly disabled with the fact Ubuntu is automatically logging in.

I'm really trying to stick to using Chromium in this case for a few reasons. Side story so this may make more sense: Chromium in this case is being leveraged because they have the fancy --kiosk flag, which is reason #1. As a result, I created a custom desktop launcher, tied it to an icon, placed it in the launch bar, and once clicked, full screen camera feeds are presented to me (CTRL + W to exit). Gaining this functionality with Firefox is more difficult due to the lack of the --kiosk flag. Reason #2 is Ubuntu lumps together similar processes under one icon within the launch bar. So if I open the ZoneMinder montage with Firefox, but then launch Firefox to read local news in a totally separate window, they still get lumped together via grouping instead of staying separate. This means I could have two windows under the Firefox icon, or two instances under the "ZM Dashboard" icon that I created. All depends what opened first (from what I can tell). Using a different browser in this case negates this altogether.

The other alternative I suppose would be to create a bogus password for the htpc account and just manually log in, like say 123 or something. Or just change the "view only" user I created in ZoneMinder to be just that (user:123) since that user is very locked down with what they can do (stream live feeds only).

Are there any other options that I didn't think of?

---

