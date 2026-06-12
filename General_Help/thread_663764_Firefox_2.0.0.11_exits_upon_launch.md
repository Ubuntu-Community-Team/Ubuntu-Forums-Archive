---
title: "Firefox 2.0.0.11 exits upon launch"
date: 2008-01-10
forum: General Help
---

### Post by stchman on 2008-01-10
Hello all.

I have noticed recently that when I launch Firefox that it sometimes immediately exits.  This has started happening recently.  Has anyone else had this happen?

If I hurry up and put my mouse on the title bar and drag the Firefox window around it does not exit.

Any help would be appreciated.

Thanks.

---

### Post by MartynA on 2008-01-10
I only have some basic ideas, but have you tried deleting your profile (saving bookmarks) and re-running it? Also any new installed add-ons might be a culprit.

---

### Post by ed_x on 2008-01-10
Try running *firefox* from a terminal. You would probably see an logged error message in the terminal when Firefox crashes. For me, a corrupt .ttf font made it crash (websites using that font caused Firefox to crash) and I found that out by looking at the error messages in the terminal.

---

### Post by daimaru on 2008-01-11
> **stchman said:**
> Hello all.

I have noticed recently that when I launch Firefox that it sometimes immediately exits.  This has started happening recently.  Has anyone else had this happen?

If I hurry up and put my mouse on the title bar and drag the Firefox window around it does not exit.

Any help would be appreciated.

Thanks.

If you have the firefox extension "external ip" disable it or apply the fix posted on mozilla forums. the extension seems to try and contact the [www.crazzy.se](www.crazzy.se) development area and crashes firefox while doing that. 

so either wait for a fix from external ip developer or apply manual hack.

if you are not using external ip extension. sorry no idea what the problem is . 
hope this helps

---

### Post by stchman on 2008-01-11
> **daimaru said:**
> If you have the firefox extension "external ip" disable it or apply the fix posted on mozilla forums. the extension seems to try and contact the [www.crazzy.se](www.crazzy.se) development area and crashes firefox while doing that. 

so either wait for a fix from external ip developer or apply manual hack.

if you are not using external ip extension. sorry no idea what the problem is . 
hope this helps

Yes, I use this extension:

[https://addons.mozilla.org/en-US/firefox/addon/3372](https://addons.mozilla.org/en-US/firefox/addon/3372)

I have never had a problem with it before until recently.  Thank you for the info.

---

