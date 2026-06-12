---
title: "[SOLVED] Adding unicode characters to gucharmap?"
date: 2007-09-23
forum: General Help
---

### Post by FuturePilot on 2007-09-23
Is there any way to add more Unicode characters to gucharmap? As you can see in the screenshot some don't show up. I'm guessing they're in a package somewhere in the repos, but I'm not sure which one. Any help?

---

### Post by FuturePilot on 2007-09-24
Bump [SIZE="5"]&#8593;[/SIZE]

---

### Post by Gwasanaethau on 2007-09-24
All you need to do is download a unicode font that covers the area you're looking for, i.e. Mathematical Alphanumeric Symbols in your example. A quick search on Google usually pulls something up - many of them are free to download. Make sure they're unicode fonts, though! Once you have the font you like, simply stick it into your ~/.fonts folder.

You may need to run the following command to update your font cache afterwards, but from what I can remember I don't think I had to do that...sure, it updates on reboot anyway. ;)

```
sudo fc-cache -f
```

---

### Post by FuturePilot on 2007-09-24
Yep, that did it. I even found the ones that were missing in my screenshot. Didn't even have to update the font cache. Thanks for the help!
[SIZE="7"]&#61446;[/SIZE] <---lol :lolflag:

---

### Post by Gwasanaethau on 2007-09-25
Not a bother 'tall 'tall! You're welcome! ;)

---

