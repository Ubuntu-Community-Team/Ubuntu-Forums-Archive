---
title: "Chrome and Firefox redirect to unwanted sites"
date: 2018-03-16
forum: General Help
---

### Post by elpidiovaldez5 on 2018-03-16
When browsing the web I find that some sites mysteriously send me to random advertising sites.  Both Firefox and Chrome do the same thing.  Also I get the sense that it is related to baidu - I seem to get the problem every time I start searching for information on Baidu's open source text-to-speech work for Linux.  If I look at Google's cache for the sites I see something sensible, but if I click the link I get porn or stupid get-rich-quick scams.  I guess I can live with the porn :)

It's driving me crazy.  I have tried deleting google and chrome configuration files in ~,  changing some settings in chrome but nothing works.  I have seen comments about a Skype/Baidu virus, but that seems to be just Windows. My searches on the internet produce too much information so I don't even know where to start.   I need to track this down in a logical manner.  Can anybody suggest a procedure.

---

### Post by Olav on 2018-03-16
You've likely caught some browser bug/virus, usually in the form of an unwanted toolbar or addon. Deleting the directories ~/.mozilla ~/.config/google-chrome ~/.cache/mozilla ~/.cache/google-chrome should help to get rid of it. You will also lose your bookmarks and other personalised configuration.

You're asking for some kind of procedure but I don't know of any. I do know it is unwise to use a web browser without added protection like adblockers. uBlock Origin is probably the best at this moment.

---

### Post by raleigh3 on 2018-03-16
For firefox, you can set it to autoexport the bookmarks file by using about:config.

And then import them later.

---

### Post by raleigh3 on 2018-03-16
For firefox, you can set it to autoexport the bookmarks file by using about:config.

browser.bookmarks.autoExportHTML = true

And then import them later.

---

### Post by Hat-trick on 2018-03-17
> **raleigh3 said:**
> For firefox, you can set it to autoexport the bookmarks file by using about:config.

browser.bookmarks.autoExportHTML = true

And then import them later.

Where do they go to?

---

### Post by elpidiovaldez5 on 2018-03-18
In the end I did what Olav recommended and then I removed and re-installed Chrome.  So far so good, although a lBaidu speech ink that was re-directing me to random sites no longer shows up in my Google search.  I don't know whether it disappeared because of what I did or other factors. Any thanks for the help.

---

