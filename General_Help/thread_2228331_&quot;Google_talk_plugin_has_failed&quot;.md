---
title: "&quot;Google talk plugin has failed&quot;"
date: 2014-06-06
forum: General Help
---

### Post by t0p on 2014-06-06
After a recent update (don't know what exactly was updated... but it was loads, >400 MB I think), everytime I sign into Gmail I get the error message "google talk plugin has failed". I'm not a huge google talk user, but it is my main form of communication with a few friends who live all round the world. So I don't need it, but I really want to use it.


I am using Chromium Version 34.0.1847.116 Ubuntu 12.04 (260972). Any ideas?


Cheers!

---

### Post by MgFrobozz on 2014-07-28
I'm having a closely-related (or maybe the same) problem in chrome ver 36.0.1985.125: any time mail.google.com is started or restarted, I get the error message "Google Talk Plugin has crashed."

I've tried blowing away the apt installation and re-installing from [https://www.google.com/intl/en_us/chrome/browser/desktop/index.html](https://www.google.com/intl/en_us/chrome/browser/desktop/index.html) (as suggested in the google forums), but get the same issue.

I've tried closing chrome, then moving ~/.config/google-chrome and ~/.config/google-googletalkplugin to ~/.config/google_old, then restarting chrome. In this case, mail.google.com hangs indefinitely (>5 minutes) while loading. If I issue "sudo apt-get remove google-talkplugin", then refresh mail.google.com, it will load (but of course gives the same message "Google Talk Plugin has crashed.").

chrome://flags didn't show a flag to enable logging. No relevant files in /var/log, and dmesg reports nothing relevant to chrome.

[FONT=courier new]Ubuntu 12.04.4 LTS
3.2.0-67-generic #101-Ubuntu SMP Tue Jul 15 17:46:11 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
[/FONT]

---

