---
title: "SCIM Question- Possible to use &quot;SmartPinyin&quot; with Traditional Characters?"
date: 2005-05-28
forum: General Help
---

### Post by magomago on 2005-05-28
question is pretty much self explanatory.  I tried all the input methods for traditional, and I couldn't find one that was the same as "smart pinyin" that is the phonetic system i learned, but I was taught with traditional characters.  Is there a way to use traditional characters instead of simplifed?  Thanks!

---

### Post by magomago on 2005-05-29
bump

---

### Post by magomago on 2005-06-13
bump once more :D

---

### Post by DancingSun on 2005-07-02
Yes, I have the same question as well!

Even though I'm a Traditional Chinese user, I find memerizing the Roman Pinyin much easier, as you don't need to remember another keyboard layout.

---

### Post by adrian440 on 2005-07-08
I am no expert on this, I am learning chinese and use simplified characters. 

When using smart-pinyin mode, I can type ctrl-/ and specify that only traditional or simplified characters are written. Also in scim's settings, you can change pronunciation ambiguities z/zh, c/ch, s/sh. Would that solve the problem?

I have heard that the zhuyin (bo-po-mo-fo)method requires the package scim-chewing, maybe this is what you need. Its only in the Breezy release at the moment.

---

### Post by DancingSun on 2005-07-08
[QUOTE=adrian440]I am no expert on this, I am learning chinese and use simplified characters. 

When using smart-pinyin mode, I can type ctrl-/ and specify that only traditional or simplified characters are written. Also in scim's settings, you can change pronunciation ambiguities z/zh, c/ch, s/sh. Would that solve the problem?

I have heard that the zhuyin (bo-po-mo-fo)method requires the package scim-chewing, maybe this is what you need. Its only in the Breezy release at the moment.[/QUOTE]
 &#32321;&#39636;&#26234;&#33021;&#25340;&#38899;&#12290;
Wow it worked!
Thanks a lot adrian440! I never bothered to try out ctrl-/.  But what's odd is that there's "&#20013;“ and “&#31616;” charcater mode which both seems to be simplified Chinese characters...did you notice any difference?

---

### Post by adrian440 on 2005-07-15
I think the &#20013; symbol means that both simplified and traditional characters are offered as choices. I wonder how useful this is for native speakers - I'm surprised that its the default, but then hey, what do I know. I'd have thought it should bring up simplified if your locale is zh_CN, or traditional if your locale is zh_TW or zh_HK.

---

