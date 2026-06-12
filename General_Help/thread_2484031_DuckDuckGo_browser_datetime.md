---
title: "DuckDuckGo browser date/time"
date: 2023-02-15
forum: General Help
---

### Post by santloufl on 2023-02-15
Hi, 

I'm running Ubuntu Desktop v22.04.1 LTS.  I am using several web browsers (chrome, firefox and DuckDuckGo).  

I've been noticing that on many sites including social media, chat and other sites, that the Time of my posting activity is incorrect.
However, it is only incorrect when I use DDG.  It's fine when I use Chrome and Firefox.

This happens almost in every site.  Specifically, when I look at my Facebook Activity Log, I see different times for the same activity.

I've attached a side-by-side image showing this example.
You can see for the same activity, the time on the left shows the activity list in DDG and the right side shows it in Chrome.  
Here the DDG time says I performed a search at 4:37PM and on Chrome, it says 9:37PM. Chrome is correct.
But I can't figure out why DDG is showing the incorrect time.  I don't see any DDG settings that relate to this.

My system time is accurate and I have no problem with my ubuntu calendar.  



[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291781&stc=1[/IMG]

---

### Post by #&amp;thj^% on 2023-02-15
As you have found on your own>>>Time Zone is not controlled by any browser. It all depends on the site/s itself. It may display time based on your computer time zone or server defined time zone.
As an exercise in TS, try Un-installing DDG, clear your browser cache and history, then reinstall DDG
See this for example for this forum>>"Message originally posted by 1fallen on February 15th, 2023 at 09:14 PM: "
When my time is:
```
date
Wed Feb 15 02:16:12 PM MST 2023

```

---

### Post by Impavidus on 2023-02-16
Neither of them can be proven correct or incorrect, as both are ambigious. They don't specify a time zone.

I think that somewhere in the long list of http headers, there's one that can be used by your browser to tell the server which timezone you use. Maybe DDG doesn't tell the server and the server then assumes some default.

---

