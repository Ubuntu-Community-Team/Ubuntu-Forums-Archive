---
title: "Copy just my config files"
date: 2007-02-26
forum: General Help
---

### Post by cookfromfrozen on 2007-02-26
Hi

I want to copy just my configuration files (i.e. just the directories starting with a . dot), to another  folder to back them up.

I tried this:

```
cp .* BackedUpConfig
```
But it copies everything (not just the hidden dirs starting with a dot.)

How do I copy just the hidden dirs?

---

### Post by kidders on 2007-02-27
Hi there,

Don't forget that every directory contains a reference to itself called '.', so typing '.*', matches that as well. Worse, it will also match '..', the reference to the parent directory.

To prevent '.*' from matching '.', you could require one more character after the '.', by writing '.?*'. Of course, that will still match '..'. To prevent *that* ...

[LIST]
[*]You could require matches to be three characters long, by writing '.??*'. Depending on your filenames, that would miss a few things.
[*]You could explicitly disallow files that have any more than one dot in them by writing '.[^.]*'. Again, depending on your filenames, some stuff could get missed.
[/LIST]

In *my* home dir, **cp -R .[^.]* BackedUpConfig** would work. Other possible solutions involve the use of **find**, which can be useful if you want more elabourate control over the copy operation. Basically, the solution depends on being able to find a filespec that describes only those things you want to copy. Sometimes the right thing to write isn't immediately obvious.

(All the dots and stars in this post are terribly confusing ... I hope you can make sense of it!)

---

### Post by cookfromfrozen on 2007-02-27
Thank you very much, that works great.

Much appreciated.

---

