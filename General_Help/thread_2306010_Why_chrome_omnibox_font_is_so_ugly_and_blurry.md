---
title: "Why chrome omnibox font is so ugly and blurry?"
date: 2015-12-11
forum: General Help
---

### Post by pktypa on 2015-12-11
Hi everyone!
I run ubuntu in vmware and sometimes virtualbox and there is one thing that really annoys me: chrome omnibox font is awful. Font is way too large, not sharp, just ugly.
Please check my screenshot in attachment to see what I mean. Is there something I could do to make it look better? I have already installed infinality patches and set style for "linux", but nothing has changed.

---

### Post by The Cog on 2015-12-11
It's difficult to be sure because I think your screenshot has been reduced somewhere along the way, but none of the fonts in the screenshot look too bad to me. Which bit of text is in Chrome Omnibox font?

---

### Post by pktypa on 2015-12-11
By omnibox I meant the url bar. Do not you think the font there is too thick and not sharp enough? I attach for comparison firefox under ubuntu: please look at the url bar and compare it with chrome url bar - I see huge difference. I know I do not have to use chrome, but being front end dev I use different browsers all the time.

---

### Post by The Cog on 2015-12-20
Sorry for the delay in responding. It's been a busy week for me.
Yes, I see the difference now you point it out (I had not noticed before).
I think the difference is just the font size in the address bar, not the actual choice of font - the character shapes look the same to me. 
Anyway, I can't find a way to change the font used in the address bar, either in firefox or in chromium.

---

### Post by vasa1 on 2015-12-20
> **The Cog said:**
> ... change the font used in the address bar, ... in firefox ...
```
#urlbar * { background: #222222 !important;  font-weight: bold !important; color: #796645 !important; font-family: "Liberation Serif" !important; }
```in a Stylish sheet (or probably userChrome.css) should work in Fx 43.

I'm not sure Chrome allows such customization without going the themes route.

---

### Post by buzzingrobot on 2015-12-22
The omnibox and the tab button fonts here is too large.  This improved things a bit:

Enter "chrome://flags" in the omnibox. This opens a large page of flags with a warning about their experimental nature.  Scroll down until you find "[B]Material design in the browser's top chrome"

[/B]Here, that flag was set to "non-Material".  I toggled it to "Material".  After restarting Chrome, the omnibox and tab button fonts were smaller.

---

