---
title: "Question on where preferences are kept in browsers and mail program"
date: 2015-08-03
forum: General Help
---

### Post by michael-piziak on 2015-08-03
Hi,

I use Google Chrome (and Firefox on occassion).  I also use Thunderbird mail.

I back up my entire home folder on a 128 gig flash drive, so everything is there including the preference files - my settings.

When I do a reinstall on occassion, and wipe everything out, and just install the browsers, and thunderbird mail, from the software center, I would like to know exactly where the preferences are held for my browsers and thunderbird - so that I can just copy the preferences over and thus retain all the email addresses and settings and the passwords the browsers remember.

I did do this once, but I forget where they are located.

Michael

---

### Post by howefield on 2015-08-03
Chromium is in ~/.config/chromium - I'd expect that chrome is similar. 
Firefox is ~./mozilla.
Thunderbird is on ~/.thunderbird

---

### Post by Bashing-om on 2015-08-03
michael-piziak; Hello;

Yeah as howefield advises, I can confirm, as I too run google-chrome.
```

sysop@1404mini:~$ ls -al ~/.config/
<snip>
drwx------  9 sysop sysop 4096 Aug  3 16:00 google-chrome
<snip>

```

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by michael-piziak on 2015-08-03
thanks all!
marking this thread as solved

---

