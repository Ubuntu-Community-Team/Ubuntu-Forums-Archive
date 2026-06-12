---
title: "Locale tweaking"
date: 2007-09-03
forum: General Help
---

### Post by kung fu buntu on 2007-09-03
I would like to improve my locale experience since there are some settings I don't like so much. 
The problem is that man locale does not show examples of each locale, neither /usr/share/i18n/SUPPORTED. 

Before I continue I must say that my keyboard works fine (I'm using my country's keymap) but I have some problems with filenames and textfiles that were on CDs that were burned in windoze. I'm currently using en_US.UTF-8 for all settings. 

I'll state hereafter the desired behaviour of the system: 
- Digit separator is , While decimal separator is . 
- Date and Time: 2007-08-25 Saturday 22:35:43 
- First day of the week: Monday 
- Sorting: case insensitive, non-alphanumeric values (such as dot, space, minus signal, etc) appear first. Ideally it should respect my country's non-standard letters. 
- Monetary: euro 
- Messages appear in en_GB, if not available fallback to en_US 
- Paper: A4 
- Measurement: a real measurement system, like the international system  
- Keyboard should work for my country's charset. 

Now, how should I set these:
> LANG=en_GB.UTF-8:en_US.UTF-8 
LC_CTYPE=? 
LC_NUMERIC=? 
LC_TIME=? 
LC_COLLATE=? 
LC_MONETARY=? 
LC_MESSAGES=? 
LC_PAPER=? 
LC_NAME=? 
LC_ADDRESS=? 
LC_TELEPHONE=? 
LC_MEASUREMENT=? 
LC_IDENTIFICATION=? 
LC_ALL=One thing I'm not sure: does LANG processing order only affects messages or does it affect the other LC_ values as well? 
Suppose that LANG=en_US.UTF-8 and LC_MESSAGES=pt_PT.UTF-8. If a message is not available PT does it fallback to US? 

Finally, is there way to relate locale with KDE's regional settings? 
My KDE settings are working OK (maybe except for the charset that is incompatible with the one usd for filenames and textfiles that were on CDs that were burned in windoze -- but that may be a mount problem). 
Setting things in KDE is nice because I can specify how I want each aspect to behave without looking at the locale (e.g. I just pick up to use the metric system, or set the currency value to &#8364;).

Thanks [-o<

---

### Post by kung fu buntu on 2007-09-06
Anybody? [-o<

---

### Post by kung fu buntu on 2007-09-15
Last bump...
I suspect that I'll have to post this question on glibc mailing list -_-'

---

