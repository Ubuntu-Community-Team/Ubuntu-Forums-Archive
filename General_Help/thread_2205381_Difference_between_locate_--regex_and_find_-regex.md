---
title: "Difference between locate --regex and find -regex"
date: 2014-02-13
forum: General Help
---

### Post by cogset on 2014-02-13
I would have posted this in Development & Programming but I guess it's just too much of an obvious question to go there:
how come that if I search for,say,firefox and thunderbird archives using 
```
locate --regex '(firefox.*|thunderbird.*)\.bz2$'
```
I get the results I'm after,i.e. stuff like:
[B]/home/user/Downloads/firefox-25.0.tar.bz2
/home/user/Downloads/firefox-26.0a1.en-US.linux-x86_64.tar.bz2
/home/user/Downloads/thunderbird-10.0.6esr.tar.bz2
/home/user/Downloads/thunderbird-20.2.0.tar.bz2[/B]

but if I use```
 find ~ -regex '(firefox.*|thunderbird.*)\.bz2$'
```
I actually get nothing instead?
What am I missing here?

---

### Post by drmrgd on 2014-02-13
The problem is the regex engine that find uses compared to locate.  From the man pages for find (specifically the 'regextype' option):

> 
-regextype type
              Changes the regular expression syntax understood by -regex and -iregex tests which occur later on the command line.
              Currently-implemented  types  are  emacs  (this  is  the  default),  posix-awk, posix-basic, posix-egrep and posix-
              extended.


I'm not at all a regex master and really only know perl regex syntax.  From the GNU docs for find there are some hints, but from a few minutes of playing around, I can't seem to get it to match even following the advice there (e.g. use '\|' instead of just '|' for alternation, and start your grouping with '\(...\)', etc):

[http://www.gnu.org/software/findutils/manual/html_mono/find.html#Regular-Expressions](http://www.gnu.org/software/findutils/manual/html_mono/find.html#Regular-Expressions)

Quite possibly someone here more versed in emacs regex syntax (or one of the other flavors available with the '-regextype' option) will be able to help get it right.

---

### Post by steeldriver on 2014-02-13
... another factor may be that find -regex is a *path *match - so you'd need something like '**.*/**firefox.*'

```
find . -regex '.*/\(firefox\|thunderbird\).*'
```

---

### Post by cogset on 2014-03-01
Yes! That one above works,I've just added** \.bz2$** to your expression,so that it looks like this
```
find . -regex '.*/\(firefox\|thunderbird\).*\.bz2$'
```
and it finally finds what I'm after.

Still,I'm not able to figure out why the slashes are needed:is it to escape the brackets?

---

### Post by Vaphell on 2014-03-01
there are flavors of regexes which differ in power and their chosen defaults.
Some chars like [](){}*+?.| have regex related meaning. The problem is some flavors of regexes consider lets say ( as a literal char first and to get regex grouping parentheses you need to escape it explicitly.

That's exactly what happens in **posix-basic** which is default flavor used in find: ()| require \ to switch to regex meaning from literal meaning.

if you used **-regextype posix-extended**, you would be able to use the clean form of regular expression with no escaping (unless you needed literals, though in that case i put everything in char class [], eg **[.]** is equivalent to **\.** and **[|]** to **\|**)

```
find . -regextype posix-extended -iregex '.*/(firefox|thunderbird).*[.]bz2$'
```

same deal is with grep.
By default it uses basic, but you can switch to extended with -E or to the most powerful of all from perl with -P

```
$ echo abc | grep '(ab)c'
$ echo abc | grep '\(ab\)c'
abc
$ echo abc | grep -E '(ab)c'
abc
$ echo abc | grep -P '(ab)c'
abc
```

---

### Post by cogset on 2014-03-02
Thank you so much,that really sheds some light on the subject.
I see regular expressions can do a lot,but they are indeed complicated to master.

---

