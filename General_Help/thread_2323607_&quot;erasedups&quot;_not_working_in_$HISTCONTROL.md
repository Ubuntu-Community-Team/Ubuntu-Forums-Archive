---
title: "&quot;erasedups&quot; not working in $HISTCONTROL"
date: 2016-05-06
forum: General Help
---

### Post by DuckHook on 2016-05-06
I've added *erasedups* to my *.bashrc* file and```
echo $HISTCONTROL
```returns```
ignoreboth:erasedups
```... so both values are being exported to the HISTCONTROL variable. *ingnoreboth* works but not *erasedups*. This is the case in all 'buntu flavours I've tested so far and also from Trusty to Zenial. Duplicates from entries as simple as:```
ll
```...to much longer command strings continue to show up in my history file, so long as they aren't being entered successively (which gets nuked by *ignoreboth*). Is anyone else experiencing this? Is my understanding of *erasedups* flawed? If someone has managed to get it working, how did you do so?

---

### Post by QDR06VV9 on 2016-05-06
See if this helps DuckHook:  [http://unix.stackexchange.com/questions/18212/bash-history-ignoredups-and-erasedups-setting-conflict-with-common-history](http://unix.stackexchange.com/questions/18212/bash-history-ignoredups-and-erasedups-setting-conflict-with-common-history)
Down to the 43 up votes post

---

### Post by DuckHook on 2016-05-06
> **runrickus said:**
> See if this helps DuckHook...Thanks runrickus. I'll let you know how I make out.

---

### Post by DuckHook on 2016-05-06
:cool:

runrickus, you are a true scholar and a gentleman. Everything now tickety-boo.

For others who happen upon this thread: after pasting the proper string into .bashrc from runrickus's linked thread, log out, log back in, it works.

---

### Post by mc4man on 2016-05-06
Yeah - thanks _alot_ for the link, I typically carry the history forward & it gets quite large & polluted with dups. Could never get erasedups to work right before.
Seems like I need to run a command to get all of it's  dups erased, though that's pretty simple to get most quickly/
(ex. - I had 512 dch -i lines, after running now just 1

---

### Post by DuckHook on 2016-05-06
As an added bonus, my history is now available in and being appended to by different terminals! A very serendipitous solution. Way cool.

---

### Post by QDR06VV9 on 2016-05-06
I was going through all the above also and that link worked for me...And was very happy to pass it along.
Glad it it worked for all of you too.
Kind regards

---

