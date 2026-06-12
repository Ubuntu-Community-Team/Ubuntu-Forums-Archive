---
title: "Lost Indicator-Weather during upgrade to 13.04"
date: 2013-05-04
forum: General Help
---

### Post by David D. on 2013-05-04
When I upgraded my primary install of Ubunter from 12.10 to 13.04 I lost the weather indicator.  I can find it in the Ubuntu Software Center, but when I try to install I get a message stating that the repository cannot be found.  Does anyone have any ideas on how to get the weather indicator back?

The thing I find odd is that I also had the weather indicator installed in my test install of Raring, which I have since upgraded to Saucy.  The weather indicator still works in the Saucy install.

---

### Post by Cheesehead on 2013-05-04
Yahoo changed the URL to locate WOEIDs (locations), which broke indicator-weather.
So they pulled the indicator from 12.10 and 13.04 rather than ship a broken one. The pull was very recent - just a week or two ago.

If you already have a location stored, it does work.
But new users and new locations are broken until a developer figures out the new system. Any community member is welcome to hack at it - it's just python, and not too hard.
See [https://lists.ubuntu.com/archives/ubuntu-devel/2013-April/037049.html](https://lists.ubuntu.com/archives/ubuntu-devel/2013-April/037049.html) for some of that discussion.

---

### Post by David D. on 2013-05-05
Thank you for the information Cheesehead.

---

