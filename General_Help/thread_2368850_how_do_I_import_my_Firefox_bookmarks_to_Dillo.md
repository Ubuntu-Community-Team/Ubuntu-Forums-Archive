---
title: "how do I import my Firefox bookmarks to Dillo?"
date: 2017-08-15
forum: General Help
---

### Post by ardouronerous on 2017-08-15
how do I import my Firefox bookmarks to Dillo? Thanks.

---

### Post by vasa1 on 2017-08-16
I'd be pleasantly surprised if that's possible.

Anyway, in addition to *man dillo*, there's online help as well. For example, [https://www.dillo.org/dillo3-help.html](https://www.dillo.org/dillo3-help.html)

---

### Post by ardouronerous on 2017-08-16
After Googling around, I found this:
[https://groups.google.com/forum/#!topic/dillo/1x2LwqaaMJQ](https://groups.google.com/forum/#!topic/dillo/1x2LwqaaMJQ)

It's a perl script that converts FF bookmarks.html to Dillo format bm.txt.

I'm not sure how to implement this though.

---

### Post by Andreyshel on 2017-08-16
> [COLOR=#000000]I'm not sure how to implement this though.[/COLOR]
You can export bookmarks using [this instructions]("https://support.mozilla.org/en-US/kb/export-firefox-bookmarks-to-backup-or-transfer")
Convert and import them then.

Convertation command

./ff_to_bm.pl >> bm.txt

bookmarks.html should be placed in same directory with the script

---

### Post by ardouronerous on 2017-08-16
How do I run the ff_to_bm.pl?

So I'm suppose to run this command:
```
 ff_to_bm.pl >> bm.txt
```
on the Terminal?

---

### Post by Andreyshel on 2017-08-16
Yes. But it is important to run
chmod +x [COLOR=#000000][FONT=&amp]ff_to_bm.pl first to permit script to run.

Also do not forget ./ before script name[/FONT][/COLOR]

---

### Post by ardouronerous on 2017-08-16
Okay, so I put bookmarks.html and [COLOR=#000000][FONT=&amp]ff_to_bm.pl[/FONT][/COLOR] in /home/~/.dillo/ folder and I open the Terminal the same folder.

Then I run these commands:
```
**~/.dillo$** chmod +x [COLOR=#000000][FONT=&amp]ff_to_bm.pl[/FONT][/COLOR][B]
~/.dillo$[/B] ./ff_to_bm.pl >> bm.txt
```

Should I run these commands as sudo?

---

### Post by Andreyshel on 2017-08-16
no you can run it as ordinary user.

---

### Post by ardouronerous on 2017-08-16
Okay, I'll be testing this out when I get home from work, thanks for the help :)

Alright! It worked!  Thanks so much! :)

---

