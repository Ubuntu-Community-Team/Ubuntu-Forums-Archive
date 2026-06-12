---
title: "Help with rename script"
date: 2006-08-08
forum: General Help
---

### Post by ewangr on 2006-08-08
I'm trying to do some renames of files in a directory, and I know the normal structure for such a script is:

```

rename 's/Phrase1/Phrase2/' *.mkv

```

However, I can't figure out what to do when the filename has a special character such as a [ or ( in it. For example:

```

rename 's/[Phrase1]_A/A/' *.mkv

```

fails miserably.

Any shell folks who can help me out here please?

---

### Post by Tomosaur on 2006-08-08
Escape characters, my friend. Example:
You've got some files ending with .[helo]
And you wanted to rename them to .txt

You'd type

rename 's/.\[helo\]/.txt/' *.\[helo\]

---

### Post by ewangr on 2006-08-09
Cool. That has worked for everything except one group of files from when I was doing some automatic time-lapses of a couple of spice plants.

On those I have the pattern:

Growth_2004_0706_01(0AE71C).mpeg

where the value in parenthesis is always a six-character alphanumeric check digit. I just want to remove the parens and the value in between so I can string these all together to create one video. But doing a * for the first part of the filename seems to confuse things (or perhaps I am still confused on how the command strip gets parsed).

TIA,
Ewan

---

### Post by Ramses de Norre on 2006-08-09
I was thinking about this:```
for i in *\(*\).mpg; do; rename 's/\([[:alnum:]]\)//' $i; done
``` but I keep getting no result when I test it, no error but the file isn't renamed..
I hope someone else sees what I'm doing wrong but this should get you in the right direction..

---

### Post by Tomosaur on 2006-08-09
I had a little try on some fake files I made, but I can't figure out a way to do this either. Are you sure you actually need to rename these files in order to string them together?

---

### Post by ewangr on 2006-08-09
Either I rename them, or I have to put together a list of all the different names as input. Hence the reason I was trying to do what would "seem" to be easier. Perhaps not though :-)

---

### Post by ewangr on 2006-08-10
SO, before I start working on building a file name list into a script, has anyone else figured out a way to get this to work?

---

