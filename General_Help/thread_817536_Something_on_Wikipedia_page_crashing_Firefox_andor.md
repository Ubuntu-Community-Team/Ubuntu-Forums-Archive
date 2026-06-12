---
title: "Something on Wikipedia page crashing Firefox and/or GUI"
date: 2008-06-03
forum: General Help
---

### Post by dppowell on 2008-06-03
Running 64-bit hardy.

Something about 3/5 of the way down this page is causing Firefox and/or my GUI to crash and restart:

[http://en.wikipedia.org/wiki/Wikipedia:Rfa](http://en.wikipedia.org/wiki/Wikipedia:Rfa)

I'm guessing it's some kind of graphic or special character in someone's Wikipedia sig, but for obvious reasons I can't examine the problem closely.

Can anyone duplicate this?  This page gets changed & archived on an ongoing basis, so someone viewing it in the future might see the problem in a different place or not at all.

---

### Post by ibuclaw on 2008-06-03
Yeah, I've answered a post similiar to this before:
[Read here.]("http://ubuntuforums.org/showthread.php?t=790440")

What I came to think was that it was a weird overflow of the readaheading cache which is causing the app to crash (Too much loading in the page for Firefox memory to handle?). Or in the case of the other OP, causes your user account to logout and go back to the login screen.

Best bet would be to run firefox in the terminal like so:
```
firefox http://en.wikipedia.org/wiki/Wikipedia:Rfa > ~/Desktop/firefox.log
```

And when it crashes, post it as a bug in [LaunchPad.net]("https://bugs.launchpad.net/ubuntu/hardy/+source/firefox-3.0") with the log file saved in your Desktop attached.

[EDIT]
Also, if you want to view the full page without FireFox crashing, then save it as an Offline File. ("**File>Save Page As...**")

Regards
Iain

---

### Post by dppowell on 2008-06-03
Will do, thank you very much.

---

### Post by kwaanens on 2008-08-21
Did you work this out? I have had Firefox crashing with a segfault, every single time I try to access a wikipedia page today. Never happened to me before with Firefox 3, at all.

---

