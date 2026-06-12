---
title: "Bulk rename to remove a timestamp on files, from BASH"
date: 2018-03-21
forum: General Help
---

### Post by friarlawless on 2018-03-21
Hi there. I'm a reasonably competent Linux user but my BASH-fu is not strong enough for this one. I have several directories full of files that came off of an old backup drive, which unbeknownst to me at the time appended a rather long timestamp onto the end of every single file. It looks something like this:

```
foobar (01-12-2017-15:43CST).txt
```

I'd like to avoid having to manually go in and rename all hundred or so files from Nautilus, so I wondered if there was a way to do this with a shell script. Ideally what I want to do is remove everything between the parentheses (and the parens themselves) and be left with just "foobar.txt" at the end. All of the files have their timestamps inside of parens, and no valid filenames have parens in them AFAIK, so it's probably safe to key off of that. What say you, BASH ninjas?

---

### Post by steeldriver on 2018-03-21
I assume from the example you also want to remove whitespace before the parenthesized timestamp?

It would be possible to do with a pure shell loop e.g.

```

for f in *\(*\).txt; do echo mv -n -- "$f" "${f/ (*)/}"; done

```

(remove the `echo` once you're convinced it's doing the right thing). The `-n` (no-clobber) option prevents overwriting in the event of a name collision.

I'd probably use the perl-based rename command

```

rename -n -- 's/ \(.*\)//' *\(*\).txt

```

The filename glob *\(*\).txt could be a simple *.txt since the regex will skip non-matching files however it doesn't do any harm to restrict the number of files that need to be processed. In this case, remove the `-n` once you've checked the functionality.

---

### Post by friarlawless on 2018-03-21
Cool. I'll make a copy of one of my directories and play with this later tonight. Thanks!

UPDATE - Worked like a charm! Thanks again. I'll save this off into my script war chest.

---

