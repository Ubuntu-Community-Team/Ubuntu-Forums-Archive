---
title: "perl rename not doing what I want"
date: 2013-08-17
forum: General Help
---

### Post by Paul_Davison on 2013-08-17
I'm struggling to write a one-liner to do a renaming task. I want to rename video files to SxxEyy format and make sure the numerical bits are padded to 2 digits.

I tried this:

```
rename 's/(S|E)(\d)(\D)/${1}0$2$3/g' *
```

Which gives:

```
Prog_S5_E3.mp4 renamed as Prog_S05_E03.mp4
Prog_S5E3.mp4 renamed as Prog_S05E3.mp4
```

I can see why this happens, because with the 'g' flag set at the end the regex engine starts searching again from the end of the previous successful search, which includes the 'E' in the second file.

An obvious solution would be to have two separate commands, one to pad the S and another to pad the E. But surely there must be a way of doing this in a single run.

---

### Post by Dave_L on 2013-08-17
> **Paul_Davison said:**
> An obvious solution would be to have two separate commands, one to pad the S and another to pad the E. But surely there must be a way of doing this in a single run.

A quick solution is to use two shell commands on one line:

rename REGEX1 *; rename REGEX2 *

---

### Post by Vaphell on 2013-08-18
with pure regex it's not trivial, but you can use perl sprintf
```
$ rename -vn 's/[Ss](\d+)[Ee](\d+)/sprintf("S%02dE%02d", $1, $2)/ge' *
AAA S1E4.txt renamed as AAA S01E04.txt
AAA S2E41.txt renamed as AAA S02E41.txt
```

---

