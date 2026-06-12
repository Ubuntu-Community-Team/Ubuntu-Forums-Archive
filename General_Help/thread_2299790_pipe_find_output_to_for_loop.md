---
title: "pipe find output to for loop"
date: 2015-10-21
forum: General Help
---

### Post by Drenriza on 2015-10-21
Hey all

Anyone who can educate me in how you would run the following command
```
find . -maxdepth 4 -name *15-10-21* |sed 's/^.//'
```
and output this into a for loop?

**The goal** is to check the sizes of my daily backups. So the above find all my daily backups that i would like to pipe into a "for each line; do du -csh $line; done"

Also how one (in the terminal - one liner) can take the output of the date command and pipe it into find.

Hope someone can give me an indication to how this is done and or what i should read (articles / tutorials / websites) to get a better idea on the above as a whole.
piping output from one command into another in the cli.

Thanks on advance all!! :KS
Kind regards

---

### Post by Drenriza on 2015-10-21
Played around with it a bit.
Is their a better / cleaner way of doing the above than
```
DATE=`date +"%y-%m-%d"`; list=`find /srv/ -maxdepth 4 -name *${DATE}*`;for line in ${list};do du -csh ${line};done
```

---

### Post by Lars Noodén on 2015-10-21
Hi again.  

```
find . -maxdepth 4 -name "*$(date +'%y-%m-%d')*" | sed 's/^[color=blue]\[/color].//'
```

[date](http://manpages.ubuntu.com/manpages/trusty/en/man1/date.1.html) can output any format.   Then wrap that in $( ... ) for [command substitution](http://mywiki.wooledge.org/CommandSubstitution) to use the output of date as if you had typed it in yourself.

Backticks still work, but the $( ... ) syntax is considered easier to read and, unlike the backticks, is nestable.  Though I'm not sure how good an idea that latter level of complexity is.

Edit: I see the second post now.  It is also a good idea to quote variables, too, just in case there are spaces or other weirdness, so you are protected from word splitting.

---

