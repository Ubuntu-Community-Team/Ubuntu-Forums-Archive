---
title: "Rename / Regex Question"
date: 2007-09-09
forum: General Help
---

### Post by arsenic23 on 2007-09-09
Ok, I've ran into some rename behavior that I can't figure out, so I'm hoping someone here can explain why the following behaves as it does.

Ok, I was testing out some rename commands that I intended to use on a larger group of files. For my test I was using these two files:
```
Gurren Lagann 17[Freelance][BBS].***  
[Nyoro~n Subs] Gurren Lagann 02 [1280x720][x264][OGG].mkv
```

I tired the command ```
rename 's/\[[^\]]*]//' *
``` multiple times to remove everything between the [ ], including those characters themselves.  When that worked to my satisfaction I reset my test files and ran rename with a *y* instead of an *s*.

But ```
rename 'y/\[[^\]]*]//' *
``` fails to change the files at all.  Why is that ?

--------------------------
*EDT:  Also, lol - the language filter on the board edits out the file extention on a subtitle file.*

---

### Post by arsenic23 on 2007-09-15
And the answer is: because y/ doesn't work that way.  I instead of 
```
rename 'y/\[[^\]]*]//' *
```

I should have used
```
rename 's/\[[^\]]*]//g' *
```

After a good bit of reading I discovered that y/ is used as a transform instead of a global replacement, unlike I previously thought. s///g is the proper way to replace something globally.


So while I have this thread sitting here taking up space let me ask this:
**[COLOR="DarkRed"]Why do many other distros use a different form of the rename command then Ubuntu?[/COLOR]**  I was recently doing some work at a chums home (using his Fedora installs) when I noticed that his rename command didn't have the sed like functionality of the Ubuntu rename.

---

