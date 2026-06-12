---
title: "cant install microdc"
date: 2006-10-13
forum: General Help
---

### Post by k0rv3n on 2006-10-13
Hi.

Got a problem installing microdc 0.11.0 on my ubuntu server.

I get this error after typing ./configure

"checking for the GNU Readline library... not found"
"configure: error: GNU Readline is required to build and run this project."

I have tried to install several packages named readline including the one given on microdc's homepage.

Anyone got a clue?

---

### Post by pay on 2006-10-13
Have you installed gcc? ```
sudo aptitude install build-essential
```

---

### Post by k0rv3n on 2006-10-17
Sorry for my delay on the answer... but yes I have that installed allready :(

---

### Post by k0rv3n on 2006-10-19
bump

---

### Post by k0rv3n on 2006-10-19
OK

Finally found out what I needed:
libreadline5-dev ^^

Thanks anyways guys

---

### Post by jonger on 2006-12-12
k0rv3n, Thanks a million. i was having the same problem. i tried everything else. it seems the simple solutions are the hardest to get. thanks

---

### Post by hagabaka on 2007-02-22
Does microdc's tab completion fail on Ubuntu for anyone? It should tab-complete commands and file names when browsing a user, but for me it just completes against local files in the current directory, which seems to be the default readline behavior when it's not customized. I tried microdc 0.11.0, microdc2 0.15.3 and microdc2 0.15.6, and they all exhibit the same behavior. I've used at least microdc2 0.15.3 in Slackware and the tab completion worked correctly.

I'm using Ubuntu 6.0, and I compiled those three versions of microdc(2) from source, with libreadline5 and libreadline5-dev installed.

---

### Post by Xappe on 2007-02-23
as of what I understand, microdc is no longer under development. I would try nanodc instead. Based on the windows dc++ core with ncurses ui on top.

[http://sourceforge.net/projects/nanodc/]("http://sourceforge.net/projects/nanodc/")

---

### Post by hagabaka on 2007-02-27
> **Xappe said:**
> as of what I understand, microdc is no longer under development.

microdc is no longer maintained, but microdc2 is still being developed. Much of it is based on microdc, and I have the same problem with both microdc and microdc2, so that's why I posted here. Maybe I should have started a separate thread though. But thanks, I'll try nanodc. It doesn't look quite "nano" compared to microdc, but I think an ncurses UI would be potentially more convenient.

---

