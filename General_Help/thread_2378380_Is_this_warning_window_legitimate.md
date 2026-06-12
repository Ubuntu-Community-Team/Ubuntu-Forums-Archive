---
title: "Is this warning window legitimate?"
date: 2017-11-22
forum: General Help
---

### Post by steve169 on 2017-11-22
I run fully updated Ubuntu 16.04 on a Dell desktop PC.

Lately, this window pops up every time I boot:

[ATTACH=CONFIG]277639[/ATTACH]

When I click "Report problem," I get a window asking for my password:

[ATTACH=CONFIG]277640[/ATTACH]

I'm afraid this might be malware. Is this a legitimate warning from Ubuntu?

---

### Post by mc4man on 2017-11-22
It's  legitimate, asks for password because it (the so-called crash) occurred during boot. So enter password & let it send the report in & hopefully it won't bother you anymore.
(- if curious, after entering password & before clicking to submit the report,  click on the details button. Most likely the crash concerns plymouth & is of no concern, been happening for years..

---

### Post by ChuangTzu on 2017-11-22
does it list what problem(s) occurred?  Is there a "details" button?  
post your repo list with code tags...
```
grep -r --include '*.list' '^deb ' /etc/apt/sources.list /etc/apt/sources.list.d/
```

---

### Post by ChuangTzu on 2017-11-22
on second thought mc4man is most likely spot on.

---

### Post by steve169 on 2017-12-12
All's well now. Thanks to both of you.

---

