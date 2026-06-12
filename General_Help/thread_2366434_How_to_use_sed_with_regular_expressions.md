---
title: "How to use sed with regular expressions"
date: 2017-07-17
forum: General Help
---

### Post by John_Patrick_Mason on 2017-07-17
I'm trying to learn how to use sed with regular expressions. The problem I'm having now is that I don't quite understand its behavior when I type:

```

sed '/'t$'/s/the/THE/' original

```

Here are the contents of the original file:

```

This part of the
document has stayed the
same from version to
version.  It shouldn't
be shown if it doesn't
change.  OTHErwise, that
would not be helping to
compress the size of the
changes.

This paragraph contains
text that is outdated.
It will be deleted in the
near future.

It is important to spell
check this dokument. On
the other hand, a
misspelled word isn't
the end of the world.
Nothing in the rest of
this paragraph needs to
be changed. Things can
be added after it.

```

When I apply the above command, it gives me:
```

This part of THE
document has stayed THE
same from version to
version.  It shouldn't
be shown if it doesn't
change.  OTHErwise, that
would not be helping to
compress THE size of the
changes.

This paragraph contains
text that is outdated.
It will be deleted in THE
near future.

It is important to spell
check this dokument. On
THE other hand, a
misspelled word isn't
THE end of the world.
Nothing in THE rest of
this paragraph needs to
be changed. Things can
be added after it.

```

In fact, I'm not even sure if I'm supposed to quote twice the regular expression. Assuming I do, shouldn't sed modify only lines that have words that end in "t"? If so, then how come the lines "compress THE size of the", "THE other hand, a" and "THE end of the world." get modified? I know lines "compress THE size of **t**he", "THE o**t**her hand, a" and "THE end of **t**he world." have a "t" in them, but shouldn't "t" be at the end of a word, for sed to work at all?

I appreciate any help I can get.

---

### Post by steeldriver on 2017-07-17
First, $ is an end of **line **marker - not an end of **word **marker - in this context

However, because of the way you quoted it (with the $ **outside **of the quotes)

```

'/'t$'/s/the/THE/'

```

bash is likely parsing the command as

```

/t

```

followed by

```

$'/s/the/THE/'

```

which (because it doesn't contain any backslash escapes) is equivalent to
```

/s/the/THE/

```

So what you effectively wrote is

```

/t/ s/the/THE/

```

in other words, it applies the substitution s/the/THE/ to any line containing the single character t

From `man bash`:

> 
 Words of the form $'string' are treated specially.  The word expands to
       string,  with backslash-escaped characters replaced as specified by the
       ANSI C standard.


---

### Post by John_Patrick_Mason on 2017-07-17
OK, so I guess that answers the double quote question. In ch. 19, in the book that I'm reading from, when they talk about using grep, they said I could specify all words that end with a "t" by typing t$, or in the example they gave:

```

grep -h 't$' file1.txt

```

Is there anyway I can do the same with the sed utility? I know that if I type:

```

sed '$s/the/THE' original

```

sed will go to the last line in the original file and replace "the" with "THE" if "the" exists. My question is, can I specify all lines that have words ending in "t" by using a basic regular expression, or is that impossible? Not trying to be nitpicky, just trying to understand, so that I can move on to the next chapter.

---

### Post by steeldriver on 2017-07-18
I can only guess that the book you're using is referring to a `file1.txt` in which there is exactly one word per line (i.e. a simple word list) - in which case there is an exact correspondence between "end of line" and "end of word"

Most regex flavors support a *word boundary* match - either \b or \<, \> which allows you to test for sequences at the beginning and/or end of words (or, more strictly, the zero-length transition from a word character to a non-word character or vice versa)

```

$ printf 'The cat sat on the mat\nThe dog jumped over the log\n' | sed '/t\b/ s/the/THE/g'
The cat sat on THE mat
The dog jumped over the log

```

See for example [Regex Tutorial - Word Boundaries](http://www.regular-expressions.info/wordboundaries.html)

Hope this helps

---

### Post by John_Patrick_Mason on 2017-07-18
Thanks steeldriver. I'll definitely check out the link you provided. I'm marking this thread as solved.

---

