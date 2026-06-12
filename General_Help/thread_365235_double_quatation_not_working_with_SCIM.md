---
title: "double quatation not working with SCIM"
date: 2007-02-19
forum: General Help
---

### Post by thykun on 2007-02-19
After i installed scim, double quotation marks is not working. On my keyboard, a brazilian abtn2, there is a key on top-left with single quotation marks and as second function, double quotation marks. But the key outputs only ' and holding shift, should output ".

Any idea of whats going on?

---

### Post by iggyboy on 2007-05-08
I had the same problems ever since I install stable fiesty edition. Google and forum guides doesn't solve the problem, however just now while trying to fix my display fonts for my LCD panel, I happen to  play with KDE Control Center, I notice changing the Keyboard Layout to basic did solve my "quotation" problem.

from **KDE Control Center** > **Regional & Accessibility** >  ** Keyboard Layout** >

at the **Layout Variant** I change to **BASIC** from **INTL** :)

my command line looks like this **setxkbmap -model pc104 -layout us -variant basic**

p/s: I know this thread posted long time ago, but just in-case someone might face this problem again.

regards :)

---

