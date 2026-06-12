---
title: "Firefox hiccups"
date: 2007-07-30
forum: General Help
---

### Post by rvbhute on 2007-07-30
Firefox browser on my setup has developed a few problems.

1. If I click on a link in Thunderbird, it doesn't start Firefox. If Firefox is **already** started, then the link opens in a new tab.

2. I connect to the net using ADSL - DLink GLB-502T modem. Unless the modem is ON **and** the PPPOE link is active, Firefox won't browse properly. Here's the scenario:
[LIST]
[*]Modem is off or pppoe link is down
[*]I open local sites (localhost) in Firefox.
[*]After the 3rd or 4th click, Firefox simply says "Waiting for localhost..."
[*]I checked Apache's access log, Firefox **did not** request a page.
[*]Epiphany surfs on localhost just fine in similar conditions.
[/LIST]

It is as if Firefox forgets to "get" pages if modem's pppoe link s down or if modem is off. **file://** works perfectly.

---

### Post by murraymca on 2007-07-30
Is firefox set as your default browser (in preferred applications)?

I'm not sure about thunderbird links, I thought there was an option...I just did a quick search and found this link:  [http://www.zulustips.com/2007/03/28/forcing-thunderbird-to-open-links-in-firefox.html](http://www.zulustips.com/2007/03/28/forcing-thunderbird-to-open-links-in-firefox.html) You may want to check this out also:  [http://www.novell.com/coolsolutions/feature/15898.html](http://www.novell.com/coolsolutions/feature/15898.html)

Might be helpful.

Cheers

---

### Post by rvbhute on 2007-07-30
Yes it did! Link problem solved! Created a key in Thunderbird's about:config. Thank you very much!

---

### Post by murraymca on 2007-07-30
No worries, I'm glad it worked.  Not sure if it is the correct solution...but I guess if it works for you :)

---

