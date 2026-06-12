---
title: "Firefox:  You're using an older version of Mozilla Firefox that we'll soon stop suppo"
date: 2015-02-02
forum: General Help
---

### Post by cwmoser on 2015-02-02
Firefox: 35.0.1

On Youtube, I get this message:
[B]You're using an older version of Mozilla Firefox that we'll soon stop supporting.
Please _update your browser_ to the latest version.[/B]

What is going on here?

Carl

---

### Post by Bucky Ball on 2015-02-02
*Thread moved to **General Help**.*

That is peculiar. I can confirm that I am using the exact same Firefox release (35.0.1) and am getting no such message. Which release/flavour of Ubuntu are you using?

---

### Post by cwmoser on 2015-02-02
I'm using Ubuntu 14.04, 64-bit, Mate Desktop.
Usually the warning message appears when I'm in You Tube.

---

### Post by buzzingrobot on 2015-02-02
[COLOR=#000000] 35.0.1 is the current version available from Mozilla and in the Trusty repos. 

I'm on 34.0 with 15.04 here and don't see that message about an old version.  YouTube works per normal.

Perhaps the problem is a bug at Youtube?

The standard gambit with Firefox oddities is to disable all extensions and see what happens, then enable each, one at a time, looking for a bad actor.[/COLOR]

---

### Post by monkeybrain20122 on 2015-02-02
I cannot reproduce it with FF 35.0.1 64 bits from standard trusty repo. Do you have a user agent switcher on?

Try test with a new profile. Close Firefox, go to your home, press ctrl+h or choose 'show hidden' from file manager's menu, locate the hidden folder .mozilla, rename it to someting like .mozilla-old, now start FF and go to Youtube and see if you still get the warning. To revert to old profile, simply close FF, delete .mozilla and rename .mozilla-old back to .mozilla.

---

