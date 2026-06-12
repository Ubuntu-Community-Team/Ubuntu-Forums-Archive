---
title: "MS Fonts a bit messy"
date: 2007-02-01
forum: General Help
---

### Post by navneeth on 2007-02-01
I installed the mscorettfonts package sometime ago. For the most part, everything (at least within the browser) looked good, but there were a few places, including vBulletin forums, where some of the text were a bit garbled. I have included a screetshot which shows what I'm talking about. Look at the difference between the words underlined in blue(good) and those in red(bad). I would appreciate it if anyone can tell how to get rid of this mess.

---

### Post by f00buntu on 2007-02-01
Setup your fonts in firefox like i did in the screenshot:
Hope it helps!

---

### Post by navneeth on 2007-02-02
My settings are almost the same. I had selected Sans-Serif instead of Arial. But I don't see any difference after changing it to Arial and restarting Firefox. Anyway, I had checked the option to let the webpages choose their own font rather than use what I had chosen.

---

### Post by f00buntu on 2007-02-02
I created a custom .fonts.conf in my home:

```

<match target="font">
 <test name="family" compare="eq" qual="any">
  <string>Anadale Mono</string>
  <string>Arial</string>
  <string>Courier New</string>
  <string>Georgia</string>
  <string>Impact</string>
  <string>Tahoma</string>
  <string>Times New Roman</string>
  <string>Verdana</string>
 </test>
 <edit mode="assign" name="antialias"><bool>false</bool></edit>
</match>
```

i'm currently using the following settings in gnome-font-properties:

---

### Post by logos34 on 2007-02-02
> **navneeth said:**
> I installed the mscorettfonts package sometime ago. For the most part, everything (at least within the browser) looked good, but there were a few places, including vBulletin forums, where some of the text were a bit garbled. I have included a screetshot which shows what I'm talking about. Look at the difference between the words underlined in blue(good) and those in red(bad). I would appreciate it if anyone can tell how to get rid of this mess.

Have you tried this fix
[http://www.ubuntuforums.org/showthread.php?t=208396&highlight=fontconfig](http://www.ubuntuforums.org/showthread.php?t=208396&highlight=fontconfig)
?
(see screenshot of browser on that page)

---

### Post by kerry_s on 2007-02-02
I found there's 2 things missing in the fonts. Down load the attached, untar and put them in /usr/share/fonts/truetype/msttcorefonts.

---

