---
title: "use &quot;sed&quot; to find and replace &quot;exact word&quot; in txt files?"
date: 2024-01-13
forum: General Help
---

### Post by 777funk on 2024-01-13
I have a case where I'm replacing the word "ass" with donkey over the course of several txt files for my kid's ipods. This worked pretty well using Mousepad (find and replace). 

But... I happened across the nice command line tool sed. This is even better because it can do a complete directory of files at once. However, it seems to not work too well because it replaces the character string instead of EXACT words and I end up with things like:

"and it came to pass"

turns into:

"and it came to pdonkey"

which is kind of funny but not quite what I was after...
Here's how I was using sed:
```
find '/home/user/Documents/Rockbox/test.txt'   -type f -exec sed -i 's/ass/donkey/g' {} \;

```

I'd like to replace when matching whole word and not parts of words. Is there a command for this?

---

### Post by The Cog on 2024-01-13
```
sed 's/\bass\b/donkey/'
```
the \b means "word boundary". It'll stop it changing mass, assess etc.

---

### Post by 777funk on 2024-01-13
> **The Cog said:**
> ```
sed 's/\bass\b/donkey/'
```
the \b means "word boundary". It'll stop it changing mass, assess etc.

Thank you! You are the best!!

```
sed 's/\are the best!!\b/Rock!!/'
```

---

### Post by The Cog on 2024-01-13
Oh stop it... you're making me blush!

That text search pattern matching that sed uses (also awk and grep which are other text processing utilities) use pattern matching called regular expressions. If you are likely to do a lot of text searching, it would be worth reading up about them - they are astonishingly powerful. But somewhat cryptic - don't try to memorise all the options etc. -  but it's worthwhile knowing roughly what kind of things regexes can do - knowing when they might be the tool you need.

---

### Post by SeijiSensei on 2024-01-13
[https://www.regular-expressions.info/](https://www.regular-expressions.info/)

---

### Post by TheFu on 2024-01-14
Beware that there are many different regex engines. They aren't the same and while **sed**'s is powerful, it doesn't support some of the standard things that **python**, **perl**, **ruby** and **egrep** support.  **egrep** and **grep** use different regex engines, for example.

I get burned by sed's powerful, but lacking, regex support far too often.

---

### Post by 777funk on 2024-01-15
> **The Cog said:**
> Oh stop it... you're making me blush!

That text search pattern matching that sed uses (also awk and grep which are other text processing utilities) use pattern matching called regular expressions. If you are likely to do a lot of text searching, it would be worth reading up about them - they are astonishingly powerful. But somewhat cryptic - don't try to memorise all the options etc. -  but it's worthwhile knowing roughly what kind of things regexes can do - knowing when they might be the tool you need.

Excellent! Thank you for the tips. Will look up awk and grep. 

I'm very glad that for niche needs like this, there is help available from someone more knowledgeable. Such a huge help. I can't imagine editing all of these txt files individually. So helpful!!

---

### Post by 777funk on 2024-01-15
> **SeijiSensei said:**
> [https://www.regular-expressions.info/](https://www.regular-expressions.info/)

Thank you!!!

---

### Post by 777funk on 2024-01-15
> **TheFu said:**
> Beware that there are many different regex engines. They aren't the same and while **sed**'s is powerful, it doesn't support some of the standard things that **python**, **perl**, **ruby** and **egrep** support.  **egrep** and **grep** use different regex engines, for example.

I get burned by sed's powerful, but lacking, regex support far too often.

Excellent and great point. I will look a little deeper. sed was the first tool I'd found and for this one somewhat simple task it did a nice job! I sure couldn't imagine trying to go through a full directory of txt files without a mistake. And what a time savings!

---

### Post by TheFu on 2024-01-15
If this is solved, please use the thread tools button and mark it SOLVED to help save the community time.

---

### Post by 777funk on 2024-01-23
Marked as solved and thanks to all! For future reference here are the  commands I ended up using to edit all the text files in the folder:

find </location/on/disc>  -type f -exec sed -i 's/\bexactoldstring\b/newstring/g' {} \;

---

