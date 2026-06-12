---
title: "Firefox only adds .com suffix when I type something into location bar"
date: 2008-04-26
forum: General Help
---

### Post by SlugO on 2008-04-26
As you all know, when you type something other than a full address to Firefox's location bar you get the best matching address that is probably equivalent to Google's "I'm feeling lucky" search.

But for some reason this doesn't work for me anymore. After a few hours of using a fresh Hardy installation Firefox now only stupidly adds .com suffix to what I write in the location bar. This is really annoying cos now it's trying to go to addresses like ubuntuforums.com and yle.com when the correct suffixes for those addresses are .org and .fi.

So what's wrong with Firefox? There isn't an option for changing this and I've made sure that I haven't put anything like that into about:config either. The problem also seems to affect every profile, even though I've only used Firefox in one of them so far. I've never had this problem even with nightly Minefield builds in Windows.

Somebody please help. I'm way too lazy to start typing fully correct URLs again :)

---

### Post by FastZ on 2008-04-26
That's odd and I wish I could help you, but the only thing I can add to this is that when I type "ubuntuforums" in my URL bar on FF3b5, it still sends me to ubuntuforums.org.

---

### Post by SlugO on 2008-04-26
> **FastZ said:**
> That's odd and I wish I could help you, but the only thing I can add to this is that when I type "ubuntuforums" in my URL bar on FF3b5, it still sends me to ubuntuforums.org.Me too eventually but that's only because ubuntuforums.com redirects to ubuntuforums.org.

---

### Post by SlugO on 2008-04-27
Well I managed to solve it :)

Seems like the problem was the default localization that was installed in Firefox called Firefox (fi) 3.0b5. Disabling it made the location bar work fine but also switched Firefox's language to English. I solved this by getting a language pack from [here]("http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0b5/win32/xpi/") and installing it.

So if anyone encounters a similar problem you should do the same :)

---

