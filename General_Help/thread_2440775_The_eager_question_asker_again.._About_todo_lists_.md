---
title: "The eager question asker again.. About todo lists and working lists."
date: 2020-04-15
forum: General Help
---

### Post by xcfstarflight1 on 2020-04-15
Hi! I am looking for a program that I can make a "tomorrow list". I have been reading about better management and coaching 
and picked up some tricks and tips for managing the daily work.
The todo list that is standard in Ubuntu is really good, but perhaps there are one better?
I just need to make a list of work to do on different dates actually and well, todo works fine.. But allways after the best I guess..

---

### Post by TheFu on 2020-04-15
Everyone has their own favorites.

I follow the GTD method.  The fuller my plate is, the more I depend on it.  I've not found anything better than a spreadsheet with multiple tabs for each "context" to meet my needs.  The column headers are:
```
Context	Priority	 Description	Extra Info
```
I used to have all sorts of date tracking, but ended up putting things that are date sensitive into my calendar instead. Seems date stuff belongs there.

But I use **todo.sh** when my plate isn't very full at all. [https://github.com/todotxt/todo.txt-cli](https://github.com/todotxt/todo.txt-cli)  The great thing about todo.sh is there's only 1 file and it can be moved around as needed (or use a dropbox/nextcloud/seafile replication tool) to have it available on any platform you use. Normal Unix text processing tools are the only requirements.  sed, cut, grep, tr, .... you get the idea.

I was addicted to "I want Sandy",  [https://boingboing.net/2007/11/14/i-want-sandy-perfect.html](https://boingboing.net/2007/11/14/i-want-sandy-perfect.html) I still miss it since it closed for simple things like shopping lists, contacts, and daily reminders about b'days.

Dont get too stuck on fancy programs.  They can easily become an excuse instead of an aid to productivity. We all seem to head down the "tools" pit then get so connected to only that solution that only works with $200 paid and has incompatible data files. My spreadsheet has a 1-page summary that could be printed, then folded into wallet-sized for taking on the go even when I'll be completely off-the-grid, no access at all.  Great for travel planning. Google "pocketmod" for that.

For a time, I used a self-contained javascript web html file from tiddlywiki. That turned out to be a really bad idea, but it was pretty.

[http://rtalbert.org/plaintext-gtd/](http://rtalbert.org/plaintext-gtd/)  he went back to plain text files too. todo.sh is very powerful, but bonehead.

Whatever works for you. That's the point.  If you like, I'd be willing to share my GTD spreadsheet template.xls file over [s]wormhole[/s]. Seems my systems are all too old to use a simple *apt install* and the *pip install* is failing (not interested in fighting with python crap) AND the snap package is broken so the enabling a wormhole doesn't work.  I thought snaps were supposed to **just work**, always?  Guess not.  [https://github.com/warner/magic-wormhole/issues/364](https://github.com/warner/magic-wormhole/issues/364)  I'll just post it somewhere public for a month or perhaps as an attachment here.

---

### Post by xcfstarflight1 on 2020-04-16
I am interrested in that template.xls using OnionShare?

---

### Post by TheFu on 2020-04-17
I quickly looked a OnionShare. Seemed like much more software than needed.  Wormhole wouldn't work on my systems. Seems snap packages **don't** *just work*.

Attached the template I created, well, long, long, ago.  Hope it is useful to someone.  Gunzip it first.  There shouldn't be any macros. Works in libreoffice last time I checked.  

My current GTD.xls isn't .xls anymore, is full of private information and has been customized by 15+ yrs of use at this point.

The Calendar tabs are just the output from **cal yyyy**, copied and pasted with a non-proportional font.

---

