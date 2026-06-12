---
title: "firefox problems, search engine, profiles.ini"
date: 2022-09-04
forum: General Help
---

### Post by porphyry52 on 2022-09-04
On Lubuntu 20.04, current

Every time firefox updates, which is often, it resets the preferred Search Engine to google, which seems ridiculous behavior on firefox part, giving aid and comfort to the enemy, as it were.

Any way to prevent that?

And lately, last month or so now, after update firefox will not run because it can't find its profiles.ini file.
The file is actually where it should be, and to get firefox to run one must do
```
rm ~/.mozilla/firefox/profiles.ini; firefox
```
That is, one must remove the file it claims it can't find.
Any way to fix that pre-emptively?

---

### Post by &amp;KyT$0P# on 2022-09-04
> **porphyry52 said:**
> Every time firefox updates, which is often, it resets the preferred Search Engine to google,

Anything [here]("https://support.mozilla.org/en-US/kb/search-engine-removal") help?

> And lately, last month or so now, after update firefox will not run because it can't find its profiles.ini file.

How did you install Firefox and what type of package did you install it as?
Do you run Firefox in some sort of custom sandbox (e.g. firejail, or custom flatpak sandbox tweaking if you have Firefox as flatpak)?

---

### Post by porphyry52 on 2022-09-06
> Anything [here]("https://support.mozilla.org/en-US/kb/search-engine-removal") help? Already looked there, it just tells you it automatically resets search engine to google, and you can manually reset it back to the engine you want, hence my remark about firefox giving aid and comfort to its own enemy, google.

 > How did you install Firefox and what type of package did you install it as?
Do you run Firefox in some sort of custom sandbox (e.g. firejail, or  custom flatpak sandbox tweaking if you have Firefox as flatpak)? 				
Installed by Lubuntu. I've no idea what any of these exotica you mention may be. All I ask of a browser is that it deliver web pages to my screen.

---

### Post by &amp;KyT$0P# on 2022-09-06
I would wonder if you've got some sort of deep rooted corruption in your Firefox user files.  Before the next scheduled Firefox update occurs (which [will be on or around 20 September]("https://wiki.mozilla.org/Release_Management/Calendar")), as a test, try completely quitting Firefox and rename [FONT=Courier New]~/.mozilla[/FONT] to [FONT=Courier New]~/.mozillaOLD[/FONT] and [FONT=Courier New]~/.cache/mozilla[/FONT] to [FONT=Courier New]~/.cache/mozillaOLD[/FONT] to let Firefox completely recreate these from scratch.  With this clean setup, when Firefox updates, does it still have the issues?

If not, then you can transfer your old data into the new Firefox profile following [this article]("https://support.mozilla.org/en-US/kb/recovering-important-data-from-an-old-profile").

---

