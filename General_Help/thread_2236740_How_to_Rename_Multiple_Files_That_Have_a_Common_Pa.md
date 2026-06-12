---
title: "How to Rename Multiple Files That Have a Common Pattern in Their Name?"
date: 2014-07-28
forum: General Help
---

### Post by GreenRaccoon on 2014-07-28
Ok, I think I've ALMOST got this, but I can't figure out what I'm doing wrong.

I know the title is ridiculous, but I'll explain myself. I'm trying to rename a bunch of files that have a similar prefix:
```
C. S. Lewis -
```
I want to rename all of these files replacing "C. S. Lewis" with "Lewis, C. S," while also keeping the rest of the filename the same.

So for example, I want to change
```
C. S. Lewis - Perelandra.pdf
```
to
```
Lewis, C. S. - Perelandra.pdf
```

This is the my command that I thought would work, but it didn't:
```
rename C*.pdf $(echo C*.pdf | sed 's/C. S. Lewis/Lewis, C. S./g')
```
This command outputs the error
```
Bareword "C" not allowed while "strict subs" in use at (eval 1) line 1.
Bareword "S" not allowed while "strict subs" in use at (eval 1) line 1.
Bareword "Lewis" not allowed while "strict subs" in use at (eval 1) line 1.
Bareword "Narnia" not allowed while "strict subs" in use at (eval 1) line 1.
Bareword "pdf" not allowed while "strict subs" in use at (eval 1) line 1.
```
I have no idea what this means, but I do know that when I run
```
echo C*.pdf | sed 's/C. S. Lewis/Lewis, C. S./g'
```
I get the output I want, that is, it lists the new filenames that I want.

So what am I doing wrong?

---

### Post by steeldriver on 2014-07-28
Shouldn't be necessary to invoke shells and sed - assuming you are talking about the perl-based rename command you can just do

```

rename -v -n 's/^C\. S\. Lewis/Lewis, C. S./' *.pdf

```

(The -n is a 'no-op' or dry-run flag - check that the substitutions look correct and then remove it to make the changes for real)

---

### Post by TheFu on 2014-07-28
```
rename 's/C. S. Lewis/Lewis, C. S,/g' C*
```

rename is a perl tool and completely awesome for this.

---

### Post by GreenRaccoon on 2014-07-28
> **TheFu said:**
> ```
rename 's/C. S. Lewis/Lewis, C. S,/g' C*
```

rename is a perl tool and completely awesome for this.
Lol no way. That is the easiest thing ever. Thanks for the quick reply!

It worked! Thanks for your help!

---

### Post by TheFu on 2014-07-28
It uses perl regex, so you can use groups and the big regex stuff that perl is famous for.  Plus, since rename is just a perl script, you can look at the source code if anything doesn't work as expected, not that that ever happens on a computer, of course.

---

### Post by GreenRaccoon on 2014-07-29
> **TheFu said:**
> It uses perl regex, so you can use groups and the big regex stuff that perl is famous for.  Plus, since rename is just a perl script, you can look at the source code if anything doesn't work as expected, not that that ever happens on a computer, of course.
Lol I'm sensing a tiny bit of sarcasm. ](*,)

Thanks a ton for your help! I'm actually trying to figure out how to switch two groups of words around right now, so I'll check out the perl source code. I made a thread explaining my problem [here]("http://ubuntuforums.org/showthread.php?t=2236865&p=13085906") in case you feel like helping me out. [-o<

---

