---
title: "Flash plugin problem"
date: 2015-08-15
forum: General Help
---

### Post by andfree on 2015-08-15
Flash plugin problem on ubuntu 12.04.5. I get the message "A plugin is needed to display this content" in pages like [this]("http://www.funnygames.gr/paikhnidi/merry_xsmash.html")

The browser is mozilla firefox, but I have the problem on chromium, too.

---

### Post by The Cog on 2015-08-15
You can install flash with this command:
sudo apt-get install flashplugin-installer

although the thought of visiting lots of sites like that with flash enabled makes me cringe.

---

### Post by andfree on 2015-08-15
Thank you. Now it shows that the game is loading, but it's always 0%.

What's the problem with visiting sites like this with flash enabled?

---

### Post by The Cog on 2015-08-15
I don't know how to help you with that game loading, I'm afraid.

Flash has a rotten reputation for security vulnerabilities. And I have a feeling that free games sites may well be harbouring some exploits, if only via 3rd-party advertisers: [http://arstechnica.co.uk/security/2015/08/my-browser-visited-drudgereport-and-all-i-got-was-this-lousy-malware/](http://arstechnica.co.uk/security/2015/08/my-browser-visited-drudgereport-and-all-i-got-was-this-lousy-malware/)

---

### Post by andfree on 2015-08-16
Are there such security problems even at Linux?

Should I open a new thread about loading problem? I can't believe that nobody can help me find a solution to this problem.

---

### Post by Yellow Pasque on 2015-08-16
> **andfree said:**
> Are there such security problems even at Linux?
Yes. Some of the vulnerabilities affect(ed) Linux.

> Should I open a new thread about loading problem?
Why would you? It's not like this thread is long and confusing.

> I can't believe that nobody can help me find a solution to this problem.
Patience... You may want to try creating another user and seeing if the game works for them. If it does, maybe you need to clear Flash's cache for your normal user. Another thing to try would be Chrome since it has the latest version of Flash. (Chromium has no Flash by default unless you extract it out of Chrome, and I don't think the pepperflash-installer which does that landed in the repos until Ubuntu 14.04.)

---

### Post by andfree on 2015-08-16
Today it's loading properly. I don't know why yesterday wasn't. Thanks a lot, and sorry for my impatience.

---

