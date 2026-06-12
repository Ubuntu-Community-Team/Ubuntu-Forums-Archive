---
title: "Broken font on CNN site"
date: 2015-01-11
forum: General Help
---

### Post by Dave_Rove on 2015-01-11
Browsing Google News with Firefox, I followed a link to CNN, [this]("http://edition.cnn.com/2015/01/10/europe/charlie-hebdo-paris-shooting/") , and found a broken font with some character edges faded and partly missing . Do other people see this or is it just me? It'd be surprising if a site like CNN had a font that was broken for all Linux users. I found a Firefox plugin for font analysis, and it told me that it was an embedded font actually called "CNN". I'm aware that the "Freedesktop" font rendering engine as used by most Linux distros behaves a little differently to its Windows and Mac counterparts, so it might be a case of this "CNN" font not being properly tested on all platforms.

[IMG]http://i.imgur.com/8F1CXzD.png[/IMG]

---

### Post by coffeecat on 2015-01-11
What operating system/distro are you using? The font rendering on the File/Edit/View/etc Firefox toolbar looks as though it is neither Ubuntu nor one of the Ubuntu flavours.  

For what it's worth, your url shows a different image, text and list on the left from your screenshot, but the font rendering in the main text is just fine in Ubuntu 14.10

---

### Post by Dave_Rove on 2015-01-11
Well, the fault has simply gone away, with fairly bold characters now appearing in place of the broken characters, so I've no idea what happened.

(I'm using 14.10 and I had got the same result with the Unity and KDE desktops. I'd set "Droid" fonts as default and my Firefox was hugely customised but that shouldn't have affected the appearance of embedded fonts on a web-page.)

(Edit: I'd scrolled halfway through the page to highlight the broken text before making the screenshot so that's why the image looked different.)

---

### Post by dfsmith on 2015-01-25
When CNN did their site redesign at the beginning of 2015, all my Firefox/KDE renderings of the site went hard-to-read, similar to the image in the top post.
I changed KDE->System Settings->Application Appearance->Fonts->Antialiasing->Hinting from "medium" to "slight" and the appearance became readable again.
This behavior is present in (at least) Ubuntu Trusty and Debian Wheezy.

---

