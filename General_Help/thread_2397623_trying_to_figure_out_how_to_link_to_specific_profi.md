---
title: "trying to figure out how to link to specific profile to Firefox ESR"
date: 2018-08-01
forum: General Help
---

### Post by ardouronerous on 2018-08-01
I have Firefox and Firefox ESR installed and I want to do is create a desktop launcher for Firefox ESR to link to a specific profile without any intervention from me, and these are the combinations of commands I've run on the Terminal and they all failed:

```
firefox-esr -p -no-remote xxxxxxxx.Default User

firefox-esr -p -no-remote Profile1

firefox-esr -p Profile1

firefox-esr Profile1

firefox-esr -new-instance -P "xxxxxxxx.Default User"

firefox-esr -P "xxxxxxxx.Default User"

firefox-esr -p -no-remote "xxxxxxxx.Default User"
```

They bring up the Choose User Profile prompt. I want to bypass this so Firefox ESR can go directly into my desired profile.

---

### Post by dragonfly41 on 2018-08-01
I have not used Firefox for some time.
However I read here [https://support.mozilla.org/en-US/kb/profile-manager-create-and-remove-firefox-profiles](https://support.mozilla.org/en-US/kb/profile-manager-create-and-remove-firefox-profiles)
that there is a box to tick on first use of profile manager ..
"Use the selected profile without asking at startup"

And -P should be upper case.

---

### Post by ardouronerous on 2018-08-01
Checking the option "Use the selected profile without asking at startup" affected both Firefoxes.

---

### Post by Holger_Gehrke on 2018-08-01
The  Option "Use the selected profile without asking at startup" sets the chosen profile as the default profile in the file '~/mozilla/firefox/profile.ini" (a line saying "Default=1" gets put under the heading for the chosen profile and removed from any profile that had such a line previously).
Since I can start my "normal" Firefox this way with may secondary profile without going through the profile manager, it should be
```
firefox-esr -no-remote -P "Play"
```
('Play' in this case obviously is the name of my secondary profile ...)

Holger

---

### Post by ardouronerous on 2018-08-01
Thank you that worked :) Making this as solved! :)

---

