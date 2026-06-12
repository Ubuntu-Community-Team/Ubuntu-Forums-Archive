---
title: "Firefox tab bar color changing"
date: 2013-04-10
forum: General Help
---

### Post by Ketsundere on 2013-04-10
I'm using the Ambiance theme on Ubuntu 12.04, and this is what I normally see when I open Firefox:

[IMG]http://i.imgur.com/RBHCmXx.png[/IMG]

However, sometimes it changes to this:

[IMG]http://i.imgur.com/xNVet88.png[/IMG]

which is really annoying. I find it aesthetically unpleasing and as you can see the title text of background tabs remains light-colored, thus becoming unreadable on this light background. It used to only happen when I added or modified a bookmark, so I just didn't do so, but ever since I upgraded to Firefox 20.0 earlier today it's been doing it whenever I download a file and sometimes when I open a new tab. (Also, as you can see I don't use the bookmarks toolbar or any other optional toolbars; this is because they appear with the same light background color that the tab bar background sometimes changes to.)

It doesn't seem to do this on Radiance or either of the High Contrast themes, if that helps. Can anyone help?

---

### Post by blackbird34 on 2013-04-11
Have you been adding a lot of desktop environments and tweaking a lot? Sometimes they interfere with each other. Ubuntu's default Unity theme shouldn't do this, but Canonical can't test every combination of configurations every Linux user creates - it would be impossible ;)

---

### Post by Ketsundere on 2013-04-11
No, I haven't. The only thing I can think of that I've changed from the default setting is the size of the launcher icons.

---

### Post by sambody on 2013-05-17
I have exactly the same problem.
It only happens when I use the Ambiance theme though (selected using Ubuntu Tweak).

---

### Post by sambody on 2013-05-17
I found two possible solutions/ workarounds:
- change theme, use something else than Ambiance (but I like the dark colors of Ambiance)
- in firefox, in auto:config, set browser.download.useToolkitUI to true (which gives the classic download window). The tab color change disappeared - problem solved.

---

### Post by zemega on 2013-05-17
You could try giving firefox a theme as well. I use FT Deep Dark theme. Simple smooth black theme for Firefox.

---

### Post by Ketsundere on 2013-05-21
Thank you, sambody!

In the meantime I had switched to Radiance and found that the same thing does happen on that theme, but the usual color is similar enough to the color it changes to that I hadn't noticed at first.

---

