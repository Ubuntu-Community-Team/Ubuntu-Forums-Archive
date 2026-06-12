---
title: "recursive grep"
date: 2006-11-19
forum: General Help
---

### Post by engine on 2006-11-19
In answer to another query, xenmax said:
> Pass the -r option if you want to do a recursive search i.e. traverse subdirectories of your folder too.

Looks convincing, matches what man grep says ... but doesn't seem to work for me :-{

I have a directory called mup with a subdirectory called kerkelijk. Here's some sample results from trying to use grep recursively:

```
ngn@nbox:~/mup$ grep -r define *.mup
ngn@nbox:~/mup$ cd kerkelijk
ngn@nbox:~/mup/kerkelijk$ grep define *.mup
4hand.mup:define TWO(STAVE)
4hand.mup:define FOUR(STAVE)
bist_01.mup:define BAR3
bist_01.mup:define BAR1
...
```

Am I doing something wrong? I'd find it really handy to be able to grep through a set of subdirectories. Thanks in advance for any tips.

N

---

### Post by lloyd_b on 2006-11-19
```
ngn@nbox:~/mup$ grep -r define *.mup
```

What this translates to is "recursively search in all files and subdirectories that match *.mup".  Since the directory you're interested in is named "kerkelijk", and it doesn't match "*.mup", it's never searched.

What I *think* you're trying to do would be accomplished with the following:

```
grep -r define * | grep ".mup"
```

Which translates to "recursively search all files and subdirectories for 'define', and then search through the results for '.mup'"

Lloyd B.

---

### Post by engine on 2006-11-23
Aha! Thanks for that, Lloyd - not just the answer to my question, but an interesting demonstration of how thinking sideways or even back-to-front can help make sense of the command-line.

Your code does indeed do exactly what I want; the back-to-frontness comes from the thoughtful way it starts from the string "define" and then looks for the extension ".mup"

---

