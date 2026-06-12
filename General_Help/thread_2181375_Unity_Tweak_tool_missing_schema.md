---
title: "Unity Tweak tool missing schema"
date: 2013-10-17
forum: General Help
---

### Post by Edward_Bray on 2013-10-17
Hi, I've been using Ubuntu for a few years now, wouldn't consider myself to be very knowledgable in how it actually works, just how to use it for everyday use.

I noticed recently that, after an update, I could no longer open Unity Tweak Tool; every time I try I get an error message saying "the folliwing schema is missing com.canonical.indicator.bluetooth" and when I close the message it doesn't start up.

What exactly *is* a schema, why would it be missing and, most importantly, how can I reinstall it so I can get back to tweaking to my heart's content.

Thanks

---

### Post by pharma on 2013-10-18
Hi, I did an online update to 13.10 and had the same problem.  After searching online and checking Synaptic, I finally decided to try "Missing recommended packages" in Synaptic Custom Filters and installed them all.  "Hey Presto!" Unity Tweak Tool works. If you don't use Synaptic the steps are: 1. "sudo apt-get install synaptic" in terminal 2. Open Synaptic from the dash 3. Click on Custom Filters then Missing Recommended Packages 4. Highlight all and right click mark for installation 5. Click apply on the toolbar.  Not very scientific but it worked for me.

I usually keep Synaptic on the Unity Launcher.  Good Luck

---

### Post by Edward_Bray on 2013-10-18
That worked great, thanks :)

---

### Post by lakshmijiju on 2013-12-10
Great ! worked for me. thanks !

---

