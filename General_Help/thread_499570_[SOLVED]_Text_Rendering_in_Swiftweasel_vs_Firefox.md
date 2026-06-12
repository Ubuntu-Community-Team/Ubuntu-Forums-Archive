---
title: "[SOLVED] Text Rendering in Swiftweasel vs Firefox"
date: 2007-07-12
forum: General Help
---

### Post by davidmorawski on 2007-07-12
I've just installed Swiftweasel on my Dell Latitude D630 running the 64-bit release of Feisty Fawn, and I immediately can recognize a difference between how text appears in Swiftweasel versus Firefox. 

I have subpixel smoothing enabled (System -> Preferences -> Font), though I'm not sure if this is related. Please find the screenshot attached. On the left is Swiftweasel--on the right, Firefox. The difference is stark. (Note: I scaled the image down from 1280x800, my native widescreen resolution, to 925x578..I hope you can still see the difference.)

Thank in advance for any insight,

Dave

---

### Post by jsage on 2007-07-13
David,

Compare the font settings within the browsers:

Edit menu -> Preferences -> Content tab -> Fonts & Colors

Also check under the "Advanced" button to the right of the font size selector.


john

---

### Post by davidmorawski on 2007-07-14
I compared Firefox's font settings versus those in Swiftweasel--and they're identical. Neither have a default font selected (It's simply blank), and both pull font settings from web pages themselves. I'm pretty sure Swiftweasel borrowed whatever config files Firefox was using, since all the preferences appear to be the same. Even bookmarks and cookie exceptions carried over.

Thanks for the thought--any other ideas?

Dave

---

### Post by jsage on 2007-07-16
David,

Make sure that you put the same default fonts in both programs, including under the Advanced button.  But if that still doesn't get you there, then remember that Iceweasel's codebase is going to be slightly different from Firefox - patches, updates, etc are on different schedules.

have fun,
john

---

### Post by davidmorawski on 2007-07-23
Found my answer on the Swiftweasel forum. There's a fix available [here]("http://sourceforge.net/forum/forum.php?thread_id=1777752&forum_id=692299") :)

Dave

---

