---
title: "Adding headers in Thunderbird"
date: 2005-04-01
forum: General Help
---

### Post by word_virus on 2005-04-01
Hey, everybody!  Quick question here,  I dunno if I'm just experiencing a mental block or what, but can someone tell me, please, where to put "user.js" on my warty box so that Thunderbird can find it?  

I want to add a custom header for Hashcash stamps to Thunderbird, which means adding the following to user.js:

user_pref("mail.compose.other.header", "X-Hashcash");

On my WinXP box, user.js lives in the same directory as prefs.js ("\Documents and Settings\username\Application Data\Thunderbird\defaults\profile", if I recall correctly),

Thunderbird support says the path to same under Linux should be:

~/.mozilla/thunderbird/xxxxxxxx.default where "x" is a random character

but I don't have such a directory.  There's ~/.mozilla/firefox,  and I can find some thunderbird preferences under /usr/lib/mozilla-thunderbird/defaults/pref/ but creating the file in either of those places provides no results.  

Any ideas?  Thanks!!

---

### Post by word_virus on 2005-07-25
[QUOTE=word_virus]

Thunderbird support says the path to same under Linux should be:

~/.mozilla/thunderbird/xxxxxxxx.default where "x" is a random character

but I don't have such a directory.  QUOTE]

Update:

Turns out T-bird doesn't create this directory until you use the program.  So if **you're ** looking to add your own header fields after a fresh apt-get install, run the program and add your email accounts first.

---

