---
title: "bash way to deal with filenames containing &quot; OR invoke properties gui from script"
date: 2014-01-05
forum: General Help
---

### Post by Dreamer Fithp Apprentice on 2014-01-05
Happy New Year, y'all!

My immediate goal is to get  a nasty filename like```
copy of 0 test folder "  ' ? * with dirt
```into the xclip selection buffer with a script called by a thunar custom action. The REASON I want to do that is that if I can get it into the buffer I can tr the naughty characters into nice ones and rename the file all in one right click menu item. I haven't figured out any scriptable way to deal with the " character. If I could make the properties gui dialogue pop up from a command in a script I think that would automatically put the filename in the selection buffer. Renaming such a file manually is easy enough but my challenge is to make a thunar custom action to call a script so that a right click menu item will rename the file replacing all the naughty characters. My original objective was to make a script that would recurse down through a directory hierarchy, find such files, and pop up a renaming dialogue with a default suggested sanitised name but that began to seem impossibly difficult. So I decided to try this more modest goal first, reasoning that if I can't make this work there isn't much chance I can do the more ambitious script, that if it does work it will at least be useful in itself, and finally that it might be a step in the direction of the recursing script.

Any suggestions or thoughts would be appreciated.

---

