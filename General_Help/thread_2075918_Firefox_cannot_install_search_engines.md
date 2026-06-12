---
title: "Firefox cannot install search engines"
date: 2012-10-24
forum: General Help
---

### Post by loopinaloop on 2012-10-24
Hi!
The problem seems to have more with latest Ubuntu 12.10 then with Firefox itself. When I choose to add new search engines, I click the green "+ Install" button but nothing happens. Adding other add-ons works just fine.

I have formated my computer and installed fresh Ubuntu but this problem remains. Anyone else experiencing it? Does anyone knows what's happening and how to fix it?

P.S. How to add Google Plus to the Unity's bar? Automatic pop-up doesn't appear for G+ but it does for Gmail. That's odd, previously it worked.

---

### Post by zeroseven0183 on 2012-10-25
Hi loopinaloop. What's your Firefox version? Have you tried upgrading Firefox to the latest version (16.0.1)?

You may also want to follow the instructions from Mozilla Support's KB article on how to add search engines [https://support.mozilla.org/en-US/kb/search-bar-easily-choose-your-search-engine?esab=a&s=search+engine&r=1&as=s#w_adding-search-engines](https://support.mozilla.org/en-US/kb/search-bar-easily-choose-your-search-engine?esab=a&s=search+engine&r=1&as=s#w_adding-search-engines)

---

### Post by loopinaloop on 2012-10-25
> **zeroseven0183 said:**
> Hi loopinaloop. What's your Firefox version? Have you tried upgrading Firefox to the latest version (16.0.1)?

You may also want to follow the instructions from Mozilla Support's KB article on how to add search engines [https://support.mozilla.org/en-US/kb/search-bar-easily-choose-your-search-engine?esab=a&s=search+engine&r=1&as=s#w_adding-search-engines](https://support.mozilla.org/en-US/kb/search-bar-easily-choose-your-search-engine?esab=a&s=search+engine&r=1&as=s#w_adding-search-engines)

My FF ver. is 16.0.1. From your link, step 3 is not working. I mean, I click "Add to Firefox" and nothing happens.

---

### Post by loopinaloop on 2012-11-13
HELP!
I haven't solved my problem yet. I click "Add" or "Install" (not sure, I have Polish version) search engines but nothing happens. I've successfully installed other add-ons but when it comes to search engines, it's just not working.

It's very odd. Any tips?

---

### Post by mardybear on 2012-11-13
Hi loopinaloop.

Have you tried a new Firefox profile?

An easy way i use for troubleshooting:

Close firefox

Rename /home/your_user_name/.mozilla/firefox/XXXXX.default (your profile) to XXXX.default.original

Rename /home/your_user_name/.mozilla/firefox/profiles.ini to profiles.ini.original

Re-open firefox (new profile automagically created) and try adding search engines

If no fix, simply delete new the newly created profile data and remove '.original' from the previously renamed file/folder to reactivate your original profile

mardybear

---

