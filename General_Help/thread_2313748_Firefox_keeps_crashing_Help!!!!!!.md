---
title: "Firefox keeps crashing Help!!!!!!"
date: 2016-02-15
forum: General Help
---

### Post by david489 on 2016-02-15
My Firefox browser keeps randomly crashing at least two to three times a day. I am very new to Ubuntu and don't have much experience. Here are the crash reports. Please let me know what caused this problem and how I can solve it.

Crash reports:

[https://crash-stats.mozilla.com/report/index/c33f1b14-a39d-40fc-be77-3b40c2160215](https://crash-stats.mozilla.com/report/index/c33f1b14-a39d-40fc-be77-3b40c2160215)


[https://crash-stats.mozilla.com/report/index/bda98cc8-772c-44f2-b56c-80b3c2160215](https://crash-stats.mozilla.com/report/index/bda98cc8-772c-44f2-b56c-80b3c2160215)


[https://crash-stats.mozilla.com/report/index/b7cd87ec-ed0f-4589-8ee4-329592160215](https://crash-stats.mozilla.com/report/index/b7cd87ec-ed0f-4589-8ee4-329592160215)

---

### Post by matt_symes on 2016-02-15
Hi

You installed Ubuntu a couple of days ago and firefox has been crashing since you installed it ? Does any other application crash ? 

Is Firefox your most used or only application ?

What hardware do you have ? Please detail it all here and its age.

Check your system memory. The three crash reports you posted are due to segmentation faults. Run memtest on it for a least 12 hours.

Kind regards

---

### Post by christian92 on 2016-02-15
Firefox sometimes is a little tricky

if you play Browsergame´s he take´s more and more Memory, till it collaps, i have this at Windows too

also there i had Problems that nobody can fix, then i reset the Browser, and now it work fine

here is the Link to reset: [https://support.mozilla.org/en-US/kb/refresh-firefox-reset-add-ons-and-settings](https://support.mozilla.org/en-US/kb/refresh-firefox-reset-add-ons-and-settings)

---

### Post by yoshii on 2016-02-15
If you can safe boot Firefox (there's some key that you hold down during bootup... more info on the firefox website), then you can turn off automatic addon upgrading.  
Also you might need to stop using a certain buggy addon.  

I used to get constant FireFox crashes.  Three things helped stop the crashes:

1) I disabled Apport because Apport itself was crashing along with FireFox
2) I got rid of some buggy addons
3) I upgraded FireFox to a higher version

Also, in the past I had less crashing after I DOWNgraded to a lower version of Flash.  

good luck

---

