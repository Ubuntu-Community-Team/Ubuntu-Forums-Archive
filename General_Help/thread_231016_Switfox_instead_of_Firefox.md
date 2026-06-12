---
title: "Switfox instead of Firefox"
date: 2006-08-06
forum: General Help
---

### Post by mishranurag on 2006-08-06
Hi!
Today in the evening, my firefox crashed and after that whenever I tried to open firefox, swiftfox started. I typed firefox command in terminal and swiftfox started. I can use swiftfox, but the problem is that it doesn't show Hindi fonts properly :(
Can anybody please let me know how to start using firefox again or get Hindi fonts work correctly in Swiftfox?
Anurag

---

### Post by aysiu on 2006-08-06
Why don't you explain the exact steps you took to install Swiftfox?

---

### Post by mishranurag on 2006-08-06
I had installed swiftfox long back using Automatix, but have not been using for long as it was not displaying Hindi fonts correctly.

---

### Post by Stirling on 2006-08-07
If swiftfox-bin is still in your running processes anytime you try to launch Firefox, Swiftfox will open.  Try doing [FONT="Courier New"]killall swiftfox-bin[/FONT] and then launch Firefox.  If that still doesn't work then it seems likely /usr/bin/firefox is pointing to Swiftfox.  I would do [FONT="Courier New"]ls -l /usr/bin/firefox[/FONT] and see if that is the case.  Off-topic, Swiftfox probably isn't displaying Hindi fonts correctly because Pango is disabled.

---

### Post by mishranurag on 2006-08-07
How can I enable Pango?

---

### Post by Stirling on 2006-08-07
You can't enable it in Swiftfox as it is compiled with Pango support disabled.  That was done because Pango causes a fairly large slowdown in rendering speed for some people.

---

### Post by sethmahoney on 2006-08-07
It might also be the fonts you have set up in swiftfox that are causing it to not render correctly.  Try switching to bitstream vera and/or bitstream vera sans - those work for me with cyrillic, and I think I remember another user saying they are successful with arabic.

---

### Post by mishranurag on 2006-08-08
> **sethmahoney said:**
> It might also be the fonts you have set up in swiftfox that are causing it to not render correctly.  Try switching to bitstream vera and/or bitstream vera sans - those work for me with cyrillic, and I think I remember another user saying they are successful with arabic.
Hmm! I will try that! Also this time after I restarted my computer firefox is working instead of swiftfox. I think its pretty weird, but I am out of my worry right now!

Anurag

---

