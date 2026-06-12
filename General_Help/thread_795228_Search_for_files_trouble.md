---
title: "Search for files trouble"
date: 2008-05-15
forum: General Help
---

### Post by nasaJ81 on 2008-05-15
Ok under the Places menu on the top tool bar on the desktop..you can scroll down to a search for files application..The problem im having is not with the program its..How do i delete past search inquires from the drop down list. I tried just deleting or backspacing and it only removes them for the moment while your in the box and then it brings them right back to the list. I also tried to find some kind of clearing option but did not find anything..Can anyone please help me with this? Thanks nasaj

---

### Post by tribaal on 2008-05-15
I never found an option for search history removal either...
If anybody could shed some light on this, I'd be really grateful.

A related annoyance: I cannot seem to disable the tracking of "recent documents"... There is an option to clear it manually, but I'd like a way to tell Ubuntu not to remember them in the first place...

Any ideas?

Thanks

- Trib'

---

### Post by cdenley on 2008-05-15
> **nasaJ81 said:**
> Ok under the Places menu on the top tool bar on the desktop..you can scroll down to a search for files application..The problem im having is not with the program its..How do i delete past search inquires from the drop down list. I tried just deleting or backspacing and it only removes them for the moment while your in the box and then it brings them right back to the list. I also tried to find some kind of clearing option but did not find anything..Can anyone please help me with this? Thanks nasaj

To remove your search history in hardy
```

gconftool -u /apps/gnome-settings/gnome-search-tool/history-gsearchtool-file-entry

```

---

### Post by drs305 on 2008-05-15
wiberg seems to have come up with a solution to permanently hide it here. Haven't tried it myself - I'd probably just make a shortcut with cdenley's solution. But here is the link, post #5:
[http://ubuntuforums.org/showthread.php?p=4798796](http://ubuntuforums.org/showthread.php?p=4798796)

---

### Post by aaronthomas on 2011-02-13
I'm totally new to Ubuntu/Linux. Thanks very much for this information about clearing the search for files history! What I would like to know now, is how can we advise the programmers (development team) about this issue? I used to use MS DOS in the early 90s, but some people would never understand you if you told them to "use the terminal and type this in the command line..." So we need to *Ubuntunize* little things like this for our more illiterate peers. :D

---

