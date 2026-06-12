---
title: "Firefox lanugage has been changed."
date: 2015-03-09
forum: General Help
---

### Post by steve69 on 2015-03-09
I'm running 14.04 LTS.  My firefox (version 36) language was changed to turkish on Sunday, March 8 2015.  This happened the same day...I think...that I performed an update.  I searched the forums and there was a similar thread, but it has since been closed.  There were two replies to the thread that were "me too" replies.  There were no replies that offered an explanation or a solution.

Is this a bug, or does this represent a security breach?  If it's not a breach, is there a fix, or is it still be worked on?

Thanks.

---

### Post by sandyd on 2015-03-09
Please post the output of the following command:
```

dpkg -l | grep "language-pack\|firefox-locale"

```

Thanks!

---

### Post by steve69 on 2015-03-09
ii  firefox-locale-en                                     36.0+build2-0ubuntu0.14.04.4                        amd64        English language pack for Firefox
ii  language-pack-en                                      1:14.04+20150219                                    all          translation updates for language English
ii  language-pack-en-base                                 1:14.04+20150219                                    all          translations for language English
ii  language-pack-gnome-en                                1:14.04+20150219                                    all          GNOME translation updates for language English
ii  language-pack-gnome-en-base                           1:14.04+20150219                                    all          GNOME translations for language English

---

### Post by eismcsquare on 2015-04-06
I am seriously getting fed up with Firefox on Ubuntu. First, it was the spelling autocorrect not selecting the right language. Now the start page has changed to Turkish for no reason.

Has anyone figured this out?

And I have the right language pack installed:

[FONT=Courier New]$ dpkg -l | grep "language-pack\|firefox-locale"
ii  firefox-locale-en                                     35.0.1+build1-0ubuntu0.14.04.1                      amd64        English language pack for Firefox
ii  language-pack-en                                      1:14.04+20141110                                    all          translation updates for language English
ii  language-pack-en-base                                 1:14.04+20140707                                    all          translations for language English
ii  language-pack-gnome-en                                1:14.04+20141110                                    all          GNOME translation updates for language English
ii  language-pack-gnome-en-base                           1:14.04+20140707                                    all          GNOME translations for language English[/FONT]

---

### Post by haplorrhine on 2015-04-08
[INDENT]ii firefox-locale-en 37.0.1+build1-0ubuntu0.14.04.1 amd64 English language pack for Firefox
ii language-pack-en 1:14.04+20150219 all translation updates for language English
ii language-pack-en-base 1:14.04+20150219 all translations for language English
ii language-pack-gnome-en 1:14.04+20150219 all GNOME translation updates for language English
ii language-pack-gnome-en-base 1:14.04+20150219 all GNOME translations for language English
[/INDENT]
 
Outputs are identical in all but version.  I think the 8-digit sequence is when I downloaded the Ubuntu image.
Might we reinstall and direct tripwire onto these packages?  I'll reinstall regardless, and I could take the opportunity to learn basic tripwire.

---

