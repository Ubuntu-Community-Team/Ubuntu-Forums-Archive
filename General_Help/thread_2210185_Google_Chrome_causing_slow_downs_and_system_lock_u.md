---
title: "Google Chrome causing slow downs and system lock ups"
date: 2014-03-09
forum: General Help
---

### Post by dylan11 on 2014-03-09
Hello, I am new here, and I registered so I could ask these questions and what not, so I'm sorry if this is the wrong area.

So, I have this very large problem with google chrome. I will be on YouTube or in another tab, and at random times, Chrome will start locking up, and not only that, the computer will go with it. This happens at random times, and once it starts, I have to quit chrome to make it stop. My hardware is not failing, as I tripple boot my system, and I have had no issues in Windows 7 or Os X Mavericks. Does anyone know a solution to this? I'm not a firefox guy, but I'm being forced to use it and it's very annoying.

**edit**
I would like to point out that the system doesn't lock up instantly, Google Chrome will just start choking and then the system will too until I close Chrome, this doesn't happen in a few seconds, as it take minutes and can often lock the system up for minutes at a time.

---

### Post by newbie2244 on 2014-03-10
Try Konqueror. If problems, rename the file extension khtml --> html.

---

### Post by drew13 on 2014-03-10
Assuming that you're running on Ubuntu; are you using Google chrome or chromium? You could try re installing Chrome to see if that fixes it, or you could go to the Ubuntu software center and using chromium instead.

---

### Post by tgalati4 on 2014-03-10
Clear the cache.  Sometimes the cache gets so large that it causes the system to slow down.  How much RAM do you have?  How much RAM is in use when running chrome?

Open a terminal:

```
google-chrome --debug
```

In another terminal:

```
free
```

---

### Post by snazzierella on 2014-03-11
Chrome is very hard on your RAM, it takes a lot to run it. When I had 256 MB, it would immediately lock up when I tried to start it, and it was extremely slow when I upgraded to 1GB. It started working well when I upgraded again to 2GB. How much RAM are you working with? You may want to consider Chromium, which is a bit lighter on it, or use firefox. Firefox worked even when I only had 256 MB to work with.

---

