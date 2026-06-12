---
title: "Any app that can provide app usage statistics?"
date: 2007-05-14
forum: General Help
---

### Post by atselby on 2007-05-14
On Windows I know I used a feature in I think it was Spybot search and destory that would tell me some basic app usage stats.  I'm now looking for something similar for my Ubuntu laptop to remove apps I don't need that I have removed from my menus etc.  I'm unsure of if there is one but figured I'd ask to see if anyone knew of one. Thanks

---

### Post by atselby on 2007-05-19
Anything? Thanks again

---

### Post by mbradlcu on 2007-05-20
cool, question!
here's a start, I'd give you a finish if I knew more but:
I have a folder in my home dir called tmp, if I run:
```
find ~/bin -amin -1
```
output:
/home/daturan/tmp
/home/daturan/tmp/tmp

if I cat a file in the dir, (in this case I 'cat'ed index.html) or run a program then run:
```
find ~/bin -amin -1
```
I get:
/home/daturan/tmp
/home/daturan/tmp/tmp
/home/daturan/tmp/index.html

indicating the file was accessed was accessed within the last 1 minute(s),
you could run this in your program directories,, ie /bin, /usr/bin,, et-cetera
here's some info from the man find:
 TESTS
       Numeric arguments can be specified as

       +n     for greater than n,

       -n     for less than n,

       n      for exactly n.

       -amin n
              File was last accessed n minutes ago.

I'm guessing programs like updatedb maybe problematic but it's a start,,
have fun

---

### Post by atselby on 2007-05-23
Interesting concept. I'll mess around with that when I get some time. Thanks

---

