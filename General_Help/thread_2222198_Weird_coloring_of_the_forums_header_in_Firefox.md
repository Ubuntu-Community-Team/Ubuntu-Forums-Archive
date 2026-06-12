---
title: "Weird coloring of the forums header in Firefox"
date: 2014-05-05
forum: General Help
---

### Post by Erik1984 on 2014-05-05
I have a weird Firefox issue with colors on some pages. On these forums the orange looks darker and the header has 2 colors now. It seems to be an issue with my current install of Firefox but I haven't located the source of the problem yet. I'm quite sure it's a local issue as I have tried a few things:

- Firefox on a new user account -> normal colors
- Other browsers (Chromium and Konqueror) -> normal colors

This I have tried to fix the problem on my personal Firefox:

- Restart with add-ons disabled -> colors still weird.
- Clear browser cache -> colors still weird.

My system:
Kubuntu 14.04 (Upgrade from 13.10, problem existed before upgrade)
Firefox 29 (problem also on Firefox 28)

Maybe this thread is in the wrong place as the issues I probably not with the code of the forums, but still I'd appreciate some pointers on how to tackle this issue :P

Some screenshots to illustrate the problem:

Add-ons disabled
[http://imgur.com/C4Cs8Hm](http://imgur.com/C4Cs8Hm)

Comparison of Firefox and Chromium
[http://imgur.com/UiYq1dS](http://imgur.com/UiYq1dS)

Firefox on fresh user profile on same system.
[http://imgur.com/wV1jiV2](http://imgur.com/wV1jiV2)

---

### Post by jbaerboc on 2014-05-06
Have you tried re-installing FireFox in it's entirety? Might be a specific strange setting that has it confused but if you do a full re-install I'd assume a fresh FireFox install wouldn't have the problem? Just some thoughts :-) good luck!

---

### Post by QIII on 2014-05-06
*Moved to **General Help.***

This is an issue with your browser, not with the Forums site itself.

---

### Post by mcduck on 2014-05-07
Firefox correcltly handles color profiles and gamma values stored in .png images, which is great for photographs but can cause that kind of issues if your computer's color management isn't quite correctly configured (or more often if the web designer doesn't know what color correction and profiles are, and the actual images on the page have strange profiles).

Anyway, the settings in Firefox can be tweaked through* about:config* page, but I'd actually recommend getting this nice extension instead: [https://addons.mozilla.org/en-US/firefox/addon/color-management/]("https://addons.mozilla.org/en-US/firefox/addon/color-management/"). If you've set up a color calibration in Ubuntu's color options, set firefox to use the same color profile (it *should* do it by default ut that doesn't seem to quite work...). Or, if you prefer, just set it to not use color profiles at all, in whch case you of course won't get accurate colors on photographs and such, but web site graphics will look ok (even though the colors won't be correct, they will at least be icorrect in the same way as with any other browser ;))

edit: Here's a better and more detailed explanation about the problem you're seeing: [http://www.metalvortex.com/blog/2012/03/16/831.html]("http://www.metalvortex.com/blog/2012/03/16/831.html")

---

### Post by Erik1984 on 2015-01-23
**Update**
@mcduck Thanks for your explanation. I haven't done anything with the color profiles manually ever, but could it be that having 2 monitors automatically changes the color profile? It can't be a coincidence that when I unplug my second monitor (different in resolution from my primary monitor) the colors on the forums are back to normal again.

---

