---
title: "Ubuntu rasterizes fonts and UI elements fuzzier with time after closing laptop lid"
date: 2017-05-21
forum: General Help
---

### Post by duke-wellington on 2017-05-21
Hello.

I'm running Ubuntu 16.04 LTS. I've been noticing fuzzy fonts and UI and I didn't know what the reason was until I was on Chrome and I tried closing the laptop lid when displaying to my external monitor. The problem gets worse over time, but rasterizes perfect again if you hover the mouse over some UI elements or hyperlinks. This problem never happens when I don't have Chrome running, so this is why it took a while for me to find out how to reproduce it. Also, the fuzzy rasterization problem affects the entire Operating System, even if I close Chrome. I only fix it by rebooting (or possibly by restarting the X session, however I don't do this). I'm wondering if this is a problem with Mir. I know that Canonical is switching to Wayland and Gnome soon, but so far 16.04 LTS is still using Unity.

I know this could exclusively be a problem with Chrome, but I doubt it because it affects my entire system even if Chrome closes. So I'm giving a heads up to you peeps.

Here's a link to a pic:
[http://i.imgur.com/32EBlIH.png](http://i.imgur.com/32EBlIH.png)

Bonus:
Also, when I close the laptop lid with the login screen present, the system tries to hibernate or sleep even if I have the system settings set to not perform any action on laptop lid closing or opening. I figure this has something to do with the root session, but I'm not sure how to change the laptop lid behavior for root (and I'm pretty sure I've tried setting a password for root, logging into a root GUI session, and changing the system settings to no avail). I could auto-login but I'd rather keep my OS password protected, and I could try a different flavor of Ubuntu with a different login daemon but I want to stick to the defaults.

---

