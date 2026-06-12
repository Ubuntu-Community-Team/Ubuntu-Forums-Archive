---
title: "Quotes and Tab Completion"
date: 2013-05-20
forum: General Help
---

### Post by Gwasanaethau on 2013-05-20
Hi all,

It’s been a long time since I last posted on these fora, but I’ve recently come back to Ubuntu with a fresh install of 12.04 LTS and I’m having a slight problem with tab completion when using double quotes. For example:
```
cd ~/"Test<TAB>
```
expands to:
```
cd ~/"/home/gwasanaethau/"Test Directory"/
```
instead of just:
```
cd ~/"Test Directory"/
```
or
```
cd /home/gwasanaethau/"Test Directory"/
```
like it used to. Does anyone have any ideas what might be causing this?

---

### Post by Cheesemill on 2013-05-20
I have the same behaviour on my machine, but I've never tried using that method before so I'm not sure if it used to be like that.
It makes sense that it doesn't work though, as when you are quoting a path you should start with a " at the beginning, not halfway through the path.

The following still works as expected though...
```
cd ~/Test<TAB>
```
expands to...
```
cd /home/rob/Test\ Directory/
```

Also...
```
cd "/home/rob/Test<TAB>
```
expands to...
```
cd "/home/rob/Test Directory/"
```

---

