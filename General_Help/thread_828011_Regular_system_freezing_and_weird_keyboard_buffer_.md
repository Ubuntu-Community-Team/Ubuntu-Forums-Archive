---
title: "Regular system freezing and weird keyboard buffer behaviour"
date: 2008-06-13
forum: General Help
---

### Post by voteforpedro on 2008-06-13
Every so often, say, every 20 minutes or so, an application will lock up for around 5 minutes.

My original thought was Firefox 3.5 was causing it but after downgrading to Firefox 2 I'm still having the same problems.

Normally it is caused by Firefox. Firefox will freeze for around 5 minutes. During that time I can do pretty much anything else. However...

If I am using Terminal the keyboard buffer goes a bit odd whilst in "freeze mode". For example, if I was typing "sudo" it might output "sud" but no "o". If I then type a space it will output "o "! The key inputs are making their way to the buffer safely but are not being outputted to the screen instantly. The keyboard is a Keysonic wireless keyboard with built-in touchpad.

Anyway, I am hoping this buffer issue is part and parcel of the random freezing and won't happen once I fix the underlying problem.

VLC Player also froze in the same manner yesterday.

The common denominator in this equation is the wireless network card or something associated with it. The card is a DWL-122 rev C using the out-of-the-box drivers. It appears to work fine aside with the annoyances of Keychain and having to enter my SSID and password everytime I logon. Grrr!

Has anybody experienced the same problems?

---

