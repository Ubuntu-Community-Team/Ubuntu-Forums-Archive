---
title: "Strange problem in Lubuntu 20.04"
date: 2021-01-27
forum: General Help
---

### Post by jet-bundle on 2021-01-27
I'd like to raise a strange intermittent problem which has arisen on two Lubuntu 20.04 installations, in the hope that this has been experienced by others and that there is a route to a solution. I'm posting in General Help, as it isn't clear that any other forum would be more appropriate, but of course the Moderators will be able to advise.

I'll describe the problem on one of the installations.

I'm a mathematician, and regularly use TeX. I compose documents using TeXworks, and often need to rearrange text or formulas by cutting and pasting. The problem is that, when doing this, additional copies of the cut text sometimes appear in unwanted places in the document.

I'm certain that this isn't caused by finger trouble. Yesterday, for example, I cut and pasted four lines of text, easily recognisable because two of the lines contained red text. I discovered that three copies of this text had been inserted into the document, in the middle of sentences or formulas, at positions about a window-height apart, below the current cursor position. It would have been impossible for me to have done this by accident.

I believe that this is a problem with Lubuntu rather than TeXworks, because a similar problem occurs on the second installation, which is used by my wife. She is not a mathematician, but experiences a similar problem when composing long emails in Thunderbird.

I do not recall the problem occurring when we used 18.04; it seems to hae started after the upgrade to 20.04.

There is one respect in which both the installations are non-standard, in that I have set the environment variable SAL_USE_VCLPLUGIN to gtk3 rather than qt5; the reason for this is to work round the known bug in LibreOffice 6.4 where exporting to pdf fails to include images.

I'd be grateful for any advice.

---

