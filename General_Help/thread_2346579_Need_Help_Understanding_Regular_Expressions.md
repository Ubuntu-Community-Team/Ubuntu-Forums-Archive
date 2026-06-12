---
title: "Need Help Understanding Regular Expressions"
date: 2016-12-16
forum: General Help
---

### Post by AUDIOTEK on 2016-12-16
I understand the concept; Regular Expressions:Specifies a text pattern that match text values.

I've Googled it but it doesn't seem to be clear.  It's basically a command that will find a pattern of text in a text file?  What is it mainly used for?   And there's lot of options mostly when using grep

-c, -f, -i, -r and the list goes on  and on.

Is it the same thing as opening a text file and looking for a pattern of text in the actual text file? Like looking for a word in a text file then with grep or sed you modify it?

---

### Post by SeijiSensei on 2016-12-16
Regular expressions are used in a wide variety of situations where you want to find text that matches a pattern.  One example is extracting lines from a text file with grep.  Suppose you have a file of email addresses and you want to extract those from GMail.  You could use
```
grep gmail /path/to/file
```
Now suppose that someone had the address [email]gmail@example.com[/email].  That would also match the test above, so you'd need to be more specific
```
grep gmail\.com$ /path/to/file
```
That matches only addresses that end with gmail.com.  The backslash "escapes" the dot to indicate it should be treated literally rather than as its regex value as a place holder for any single character.  The dollar sign denotes the end of the line.

As you suggest, you can combine grep with other commands like sed or awk via pipes.  For instance, to change all the gmail.com addresses to example.com, you'd use
```
grep gmail\.com$ /path/to/file | sed 's/gmail/example/g' > /path/to/newfile
```

The widely-used product [SpamAssassin]("http://spamassassin.apache.org/") has many rules to identify spam that are based on regular expressions. For instance, I have this custom rule on my server to identify ZIP file attachments with a single-letter name:
```

body SINGLE_LETTER_ZIP    /filename="[a-z]\.zip"/

```
SA uses "Perl-compatible" regular expressions which are contained within a pair of "/" characters.

The only grep options I use routinely are -v which reverses the search and returns non-matching lines, and -E which tells grep to use its "extended" syntax.  (See the [manual page]("https://linux.die.net/man/1/grep") for details.) The command egrep is an alias for "grep -E".

---

### Post by AUDIOTEK on 2016-12-16
OK thanks  I think I get it now.  In other terms it's a super search engine for text files only with really advanced options?

---

### Post by vasa1 on 2016-12-16
> **AUDIOTEK said:**
> OK thanks  I think I get it now.  In other terms it's a super search engine for text files only with really advanced options?
I'd make that "it's a super search **and replace or insert or delete** engine for text files".

---

### Post by AUDIOTEK on 2016-12-16
OK perfect   thanks.  Do you guys use those on a regular basis?

---

### Post by DuckHook on 2016-12-17
> **AUDIOTEK said:**
> …Do you guys use those on a regular basis?"Regular" is a vague term.

I just used one the other day to batch rename about 150 photos that my daughter gave me, all with the wrong family name from the photographer. I remember a time in my Windows days about 25 years ago when I would have changed them one by one. ](*,)

The gurus here who work with massive lists, a dozen config files a day, etc. probably do use regexes on a regular basis. We mere mortals still find them to be absolute life-savers on those fewer occasions when they resolve a massive repetitive task like magic.

---

### Post by Keith_Helms on 2016-12-17
You can use regular expressions for other purposes than searching.   Here's an example where I'm using it in a script to verify a user option is one of x, a one digit number, or a two-digit number:
```
if [ `echo $opt | egrep "^([x]|[1-9]|[1-9][0-9])$"` ]
```

I don't know if they're technically considered regular expressions, but I use bash filename expansion all the time.  If I know that there's only one directory in a given path, I can get lazy and just use an "*".  Example:
```
cd /media/keith/*
```
or
```
cd /media/*/*
```

If I know part of the directory name is unique:
```
cd /data2/v*
```
or a filename
```
less d*conf
```

---

### Post by DuckHook on 2016-12-17
> **Keith_Helms said:**
> …I don't know if they're technically considered regular expressions, but I use bash filename expansion…Technically, bash filename expansion is globbing. Regex is text manipulation within an app or function. But if the two are not the same, they are pretty much identical twins. &#8213;Just learned this myself from Vasa1 a few weeks ago ;)&#8213;

---

### Post by untrustytahr on 2016-12-17
> **DuckHook said:**
> Technically, bash filename expansion is globbing. Regex is text manipulation within an app or function. But if the two are not the same, they are pretty much identical twins. &#8213;Just learned this myself from Vasa1 a few weeks ago ;)&#8213;

There is a small, but significant difference between the two.  An asterisk in globbing matches _**any **_character but in regex it matches zero of more of the **_preceding_** character.  That was one of those differences that took me a while to realize.

 As for the OP asking about when to use them... I use them ALL the time grepping through logs to find the significant entries that I need to troubleshoot problems.

---

### Post by AUDIOTEK on 2016-12-17
I assume you guys are all Linux system administrators?

---

### Post by 1clue on 2016-12-17
@AUDIOTEK,

Answering your last post first, we probably all own Linux boxes, which means we're Linux system administrators. 

Regular expressions (regex) match patterns in text. Regex is used in programming for all sorts of reasons, some of which are searching, replacement, or validation.  An example of the latter would be to check that a phone number follows a phone number format. They let you search and replace not only the text you're matching but possibly what might be immediately before or after, or on the same line.

Regex is found in text editors, mail apps, all sorts of places. Often the regex functionality is present even if many of the users of whatever application don't realize it.

Regex is used widely in any operating system and almost every programming language, at least by a library extension. Unfortunately not all scenarios use the same rules for regular expressions, making them harder to learn.  That said, if you can climb the learning curve then regex is well worth your effort.

There are dozens of books written about regular expressions. I've owned several. I don't think this particularly makes me an expert, but I call myself an enthusiast.

---

### Post by vasa1 on 2016-12-17
> **1clue said:**
> ... Unfortunately not all scenarios use the same rules for regular expressions, making them harder to learn. ...
very +1.

Even the tools can be different! mAWK, nAWK, and gAWK are some variants of AWK. If you ask for help in a general Linux forum, it would be wise to specify your distro and, ideally, the specific variant of the tool you're using. This maybe of interest: [http://unix.stackexchange.com/questions/236655/how-to-programmatically-detect-awk-flavor-e-g-gawk-vs-nawk](http://unix.stackexchange.com/questions/236655/how-to-programmatically-detect-awk-flavor-e-g-gawk-vs-nawk).

I think most Ubuntu flavors come with the GNU version (gAWK?). But, at least at one time, Ubuntu Mate came with two AWK's pre-installed. I don't know what they do currently.

---

### Post by DuckHook on 2016-12-17
> **AUDIOTEK said:**
> I assume you guys are all Linux system administrators?Just an ordinary sinner here. No accreditations, no special training or professional learning&#8213;just a retired grandpa with lots of time on his hands, a power user of sorts, years of trial and error, a thirst for further knowledge and a desire to help. Like a lot of others on this forum, actually.

When I started out, Linux looked like this impossibly big mountain to climb. I'm still climbing, but it didn't turn out to be nearly as difficult as I had once feared. Looking back, it's amazing how high you can get just taking one small step at a time.

---

### Post by AUDIOTEK on 2016-12-18
> **DuckHook said:**
> Just an ordinary sinner here. No accreditations, no special training or professional learning&#8213;just a retired grandpa with lots of time on his hands, a power user of sorts, years of trial and error, a thirst for further knowledge and a desire to help. Like a lot of others on this forum, actually.

When I started out, Linux looked like this impossibly big mountain to climb. I'm still climbing, but it didn't turn out to be nearly as difficult as I had once feared. Looking back, it's amazing how high you can get just taking one small step at a time.

That's awesome!!!   I'm in my mid 40's doing my Linux+ LPIC 1 course for career advancement but also like you said for a thirst for further knowledge.   I don't really want to be a sysadmin but the more knowledge you have the better it is.  Next will be Newtwork+ then some C, Node.js and in between some different certifications.  I was looking at AWS training also.  I've been a Ubuntu users for a few years but it seems that knowing Linux really separates you from the pack now.

---

