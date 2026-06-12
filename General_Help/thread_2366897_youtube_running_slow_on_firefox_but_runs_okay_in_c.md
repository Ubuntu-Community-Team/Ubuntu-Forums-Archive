---
title: "youtube running slow on firefox but runs okay in chromium"
date: 2017-07-23
forum: General Help
---

### Post by ardouronerous on 2017-07-23
I'm experiencing some lagging in playing Youtube videos in Firefox, but the videos runs okay on Chromium.

The videos are set to 480p.

Please note, I'm not using Flash player, so Youtube videos are running on HTML5, and other sites, such as Dailymotion videos runs okay on Firefox.

---

### Post by monkeybrain20122 on 2017-07-23
Try this on a new proile. Close Firefox. Open file manager, press ctrl+h or choose "show hidden files" from menu. Find the hidden folder .mozilla, change it to something else like .mozilla-bk

Now start Firefox, go to about:config and search for layers. Change layers.acceleration.force-enabled to true. Restart Firefox. If it doesn't crash go to Youtube and see if it makes a difference. 

To go back to the old profile, close Firefox, open file manager. show hidden again and delete .mozilla then rename .mozilla-bk to .mozilla.  If editing about:config like above works, do it again here in the old profile. The reason to test on a new profile is that for some hardware FF would crash if you force enable layers acceleration.

---

### Post by ardouronerous on 2017-07-23
It made Firefox faster.

But I Google about enabling layers.acceleration.force-enabled to true, we enabled hardware acceleration on Firefox and made it faster, but hardware acceleration on Firefox was disabled by default on Linux due to a security risk.
[URL="https://www.reddit.com/r/linux/comments/662dxm/psa_hardware_acceleration_on_firefox_may_be/"]
https://www.reddit.com/r/linux/comments/662dxm/psa_hardware_acceleration_on_firefox_may_be/[/URL]

I've recently received an update to the Linux kernel, updating from 4.8 to 4.10, is this security risk still a risk though?

---

### Post by monkeybrain20122 on 2017-07-23
> **ardouronerous said:**
> It made Firefox faster.

But I Google about enabling layers.acceleration.force-enabled to true, we enabled hardware acceleration on Firefox and made it faster, but hardware acceleration on Firefox was disabled by default on Linux due to a security risk.
[URL="https://www.reddit.com/r/linux/comments/662dxm/psa_hardware_acceleration_on_firefox_may_be/"]
https://www.reddit.com/r/linux/comments/662dxm/psa_hardware_acceleration_on_firefox_may_be/[/URL]

I've recently received an update to the Linux kernel, updating from 4.8 to 4.10, is this security risk still a risk though?

I think it is disabled because of some graphic driver issues that may crash FF if acceleration is enabled. If it works I won't worry about it.

---

### Post by ardouronerous on 2017-07-23
Okay thanks :)

---

### Post by ardouronerous on 2017-07-23
I've just noticed that Youtube and Startpage.com changed their colors to blue and brown, what's the occasion?

---

### Post by ardouronerous on 2017-07-23
enabling hardware acceleration on Firefox caused this, can someone please merge this with: [https://ubuntuforums.org/showthread.php?t=2366897](https://ubuntuforums.org/showthread.php?t=2366897)

---

### Post by ardouronerous on 2017-07-23
I've tried this on my Dell Inspiron E1505 laptop, and it caused pages some pages to be rendered as blue and brown, like for example, the red in Youtube's logo becomes blue.  what caused this?

---

### Post by monkeybrain20122 on 2017-07-23
> **ardouronerous said:**
> I've tried this on my Dell Inspiron E1505 laptop, and it caused pages some pages to be rendered as blue and brown, like for example, the red in Youtube's logo becomes blue.  what caused this?
Your graphic driver.

---

### Post by ardouronerous on 2017-07-23
so, what does that mean then?

---

### Post by lisati on 2017-07-23
> **ardouronerous said:**
> enabling hardware acceleration on Firefox caused this, can someone please merge this with: [https://ubuntuforums.org/showthread.php?t=2366897](https://ubuntuforums.org/showthread.php?t=2366897)

Threads merged

---

### Post by ardouronerous on 2017-07-23
why did enabling hardware acceleration affect my graphics card?
does this mean my graphics card is failing?

btw, enabling hardware acceleration on my Xubuntu 16.04 Desktop didn't cause problems like this.

The laptop is running Lubuntu 16.04.

---

