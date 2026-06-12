---
title: "Laptop with 17.10 suspends with lid closed, even with an external display attached"
date: 2017-12-18
forum: General Help
---

### Post by jlacroix on 2017-12-18
My understanding is that by default, GNOME is configured to not suspend when you close the lid and an external display is attached. This has been the case for quite a while. However, with Ubuntu 17.10, laptops seem to suspend no matter what when you close the lid, regardless of whether or not you have a display attached. My use-case is I use my laptop as a desktop when I'm home in the evenings, and then as a laptop when I take it with me during the day. With previous versions of Ubuntu, this worked fine. With 17.10, this is literally impossible.

If I power off my laptop, boot it with the lid closed, this will work properly. My external display will work and function as normal. Then, if I use the laptop screen with the lid open and then re-attach the display and close the lid, it will start suspending again. The problem is that there is no way around this. I've even tried waking the laptop and quickly closing the screen before it has a chance to wake up all the way. It will still suspend.

My desired result is that if a display is attached, the laptop should NEVER suspend when the lid is closed.

I've tried adjusting the power settings in the GNOME settings app, as well as the Tweak Tool. Those settings are all ignored. In fact, I've even configured Systemd by editing the /etc/systemd/logind.conf file and those settings seem to be ignored. In fact, I've even opened up the dconf editor and configured the following settings (all of which are ignored):

/org/gnome/settings-daemon/plugins/power/lid-close-ac-action
/org/gnome/settings-daemon/plugins/power/lid-close-battery-action
/org/gnome/settings-daemon/plugins/power/lid-close-suspend-with-external-monitor

I can't imagine why suspending a laptop with an external display attached would be desired behavior but it seems to me that something on the system literally overrides all of these settings. Has anyone found a way around this? As it stands right now, I need to reboot my laptop every time I connect to an external display. I've even tried a different laptop, and I'm able to reproduce this behavior with a live USB as well, so it's definitely not my configuration.

---

### Post by bcriger on 2018-03-14
I'm also having this problem, I have to reboot with the lid closed if I want to just use an external display.

---

