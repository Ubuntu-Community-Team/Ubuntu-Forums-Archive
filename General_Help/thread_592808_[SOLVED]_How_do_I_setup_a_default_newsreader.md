---
title: "[SOLVED] How do I setup a default newsreader?"
date: 2007-10-26
forum: General Help
---

### Post by CoolDreamZ on 2007-10-26
I use Firefox as my browser and when I click on a link such as [news://xyz](news://xyz) I would like a newsreader to open (in my case Thunderbird) at the moment nothing happens. I can't see any options in the Gnome preferred applications or Firefox for this. I have searched these forums and the Mozilla forums and have drawn a blank.

---

### Post by brownbat on 2007-10-28
1. Type **about:config** in the address bar.
2. Right-click, choose new -> string.
3. Set the Preference Name: network.protocol-handler.app.news
4. Set the Value: /path/to/newsreader

Stole this advice from [here]("http://blog.ryaneby.com/archives/firefox-protocol-handlers/"), let us know if it works.

---

### Post by CoolDreamZ on 2007-10-29
That did the trick, thanks!! :)

---

