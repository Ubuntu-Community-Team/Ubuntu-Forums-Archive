---
title: "iBus, fcitx, Anthy, Mozc for Japanese input after 15.10"
date: 2016-01-25
forum: General Help
---

### Post by anotherChris on 2016-01-25
I'm pretty much computer illiterate, but I got fcitx with Mozc up and running on Lubuntu 15.10.  All of the support/advice about installing Japanese writing support refers to iBus, so it's confusing for people like me.  Also, they all refer to Anthy.  I finally figured out:

iBus and fcitx are both platforms for taking the normal keyboard input and converting it into non-Latin characters.

If you have old versions of an Ubuntu release, you might have just iBus.  
If you've been upgrading, you might have both iBus and fcitx.  
If, like me, you just did a fresh install of 15.10 or later, you will have only fcitx.  You can forget about iBus.

The part that was really confusing was that Github (I have no idea what Github is, btw) lists both Mocz and Anthy, so I thought I should have both, but don't.

If iBus and fcitx are programs for switching from standard keyboard inputs to non-standard outputs, Anthy and Mocz seem to ride on top of those programs and define exactly how the outputs are created.

iBus has been replaced by fcitx in Lubuntu development, and [according to the fcitx website]("https://fcitx-im.org/wiki/Mozc"), Anthy is now being rolled into Mocz:

> [COLOR=#252525][FONT=sans-serif]Mozc is the open source version of Google Japanese Input. The relationship between Mozc and Google Japanese Input is just like Chromium and Google Chrome. Mozc is not open developed, though it's open source.[/FONT][/COLOR]
[COLOR=#252525][FONT=sans-serif]Anthy development has moved to Mozc.[/FONT][/COLOR]



So you just need fcitx and Mocz...

My question is does anyone have a good place for instructions on how to use Mozc?  For example, I would assume that to type &#20140;&#37117;, you would input "k-i" and then "small", then "y-o" but you just type "k-y-o".  Trial and error is fine and good, but tutorials or manuals anywhere?  Thanks.

---

