---
title: "No text in firefox and text in email partly missing"
date: 2014-05-19
forum: General Help
---

### Post by jan-bol on 2014-05-19
Hi!

At the same time the text in my browser and partly the text of my incoming emails went missing.

_Browser (Firefox)_
- Only graphic elements, backgounds, border images, etc. are shown but all the text is missing
- Firebug shows many errors like "Use of getAttibuteNode() is deprecated. Use getAtTribute instead"
- Menu tabs are shrunk to a minimum size, so the text is not only not shown but it is not loaded

_Email (Thunderbird)_
- Some emails are completely blank. Missing all text.
- Some emails miss the text above the sender
- When I answer an email the text reappears as usual in contained part of the incomming email
- It only happens to incoming emails

_Configuration_
- Ubuntu 14.04 Lts x86 64 bits (installed yesterday)
- Firefox 29.0
- Thunderbird 24.5.0
- Desktop 64 bits dual core. I have the impression it is not hardware related, but if more info is required pls let me know

_What happened?_
As I just installed 14.04 I was working on getting everything up and running again. Some actions that I did roughly at the time the problem appeared:
- copy/pasted the old default profile to thunderbirds
- Imported a bunch of emails from thunderbird from my (windows) laptop
- Imported the font set from my laptop using following instructions (from this [page]("http://www.enqlu.com/2014/04/how-to-install-apple-mac-osx-fonts-in.html"))
```
[I][B]
sudo cp -r fonts/ /usr/share/fonts/[/B][/I][I][B]
sudo fc-cache -f -v[/B][/I]
```
- While I was at this site I decided to install the mac fonts offered at this page as well.

So I am not sure which of both actions caused the problem. I think it was installing the fonts, because this appeared to have failed as I don't see the fonts in the font viewer.

I googled on the subject but could not find posts about this. I find some post relating to hardware acceleration, but I dont think that is the issue here (IMHO)

Any help would be highly appreciated! :) Thanks in advance!

---

### Post by jan-bol on 2014-05-19
Sometimes I surprise myself :D

Browsing the font folder in usr/share/fonts i noticed there was a subdirectory fonts that had limited permissions. I changed the permissions for Group and Others to Access files and, lo and behold, the problem is gone. Text in websites is back and emails show text again. The only thing is that the font in emails is different now and less legible, but basically this issue is solved.

---

