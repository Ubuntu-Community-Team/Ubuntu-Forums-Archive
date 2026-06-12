---
title: "[SOLVED] Firefox Dictionary ALL WORDS MISSPELLED"
date: 2008-03-25
forum: General Help
---

### Post by iheartubuntu on 2008-03-25
I got my dad to make the switch to Ubuntu after his laptop kicked the bucket. He just got a new DELL 1525n Inspiron laptop (very nice) with Ubuntu 7.10 factory installed and whenever he is typing an email in gmail, every single word comes up as misspelled! Any tips how to fix this for him?

Ive never had this problem on any Ubuntu set ups. I would post this in Dell threads here, but maybe this is common elsewhere?

Ive already tried deleting his dictionary languages and re-adding them, no help. Any other ideas? Thanks!

---

### Post by codeslicer on 2008-03-25
This happened to me once... but it was because I was running a really CPU-intensive program.

Perhaps you should wait for Hardy to come out - Firefox 3 may fix that problem...

---

### Post by Dojan5 on 2008-03-25
> **shirteesdotnet said:**
> II got my dad to make the switch to Ubuntu after his laptop kicked the bucket. He just got a new DELL 1525n Inspiron laptop (very nice) with Ubuntu 7.10 factory installed and whenever he is typing an email in gmail, every single word comes up as misspelled! Any tips how to fix this for him?

Ive never had this problem on any Ubuntu set ups. I would post this in Dell threads here, but maybe this is common elsewhere?

Ive already tried deleting his dictionary languages and re-adding them, no help. Any other ideas? Thanks!

Hmm.
Does he use like, err, Evolution or does he use GMail through FireFox? If he uses through Firefox id go to addons.mozilla.org and install a dictionary addon.
Though, i don't really get the question.
He types correct, but it comes up misspelled or does it just show a red underline under the word?
Else i can't be at any help and ye have to wait for someone else to reply...

---

### Post by iheartubuntu on 2008-03-25
If I type a sentence like this, like I am doing right now, all words are underlined red even though I have not misspelled a word.

"leik" should be underlined in red when I type it, but not "like" since it is spelled correctly.

---

### Post by iheartubuntu on 2008-03-25
* bumpity bump bump *

Anyone? Thanks. I feel bad I got my dad onto Ubuntu and then it doesnt work properly!

---

### Post by teryowen on 2008-03-25
How about your computers language settings? perhaps its set to something else other then english thus causing all the errors. Im not sure where to find this but look around system perfs or administration and see if you can find language settings. I think this is the cause of the problem.

---

### Post by pointone on 2008-03-25
So this is in Firefox? You can disable the spell checker with **Edit > Preferences > Advanced > Browsing > "Check my spelling as I type"**.

Changing your language setting in the **Languages > "Choose your preferred language for displaying pages"** dialog immidiately below may fix the error without having to disable the spell checker completely, though.

---

### Post by iheartubuntu on 2008-03-26
> **pointone said:**
> So this is in Firefox? You can disable the spell checker with **Edit > Preferences > Advanced > Browsing > "Check my spelling as I type"**.

Changing your language setting in the **Languages > "Choose your preferred language for displaying pages"** dialog immidiately below may fix the error without having to disable the spell checker completely, though.

Id rather not disable the spell checking feature. And Ive already tried removing and later reinstalling the preferred language with no benefit. 

Maybe I should try reinstalling Firefox?

---

### Post by Whiffle on 2008-03-26
You could try reinstalling, or maybe just the ubuntu build of it is wonky, I saw this issue before when I was running ubuntu.  I tried to reproduce it under Firefox 2.0.0.12 in Arch and it didn't do it.  I think thats the same version as is found in gutsy. Maybe try a version from the firefox website?

---

### Post by dcstar on 2008-03-26
> **teryowen said:**
> How about your computers language settings? perhaps its set to something else other then english thus causing all the errors. Im not sure where to find this but look around system perfs or administration and see if you can find language settings. I think this is the cause of the problem.

Exactly, the following terminal command will show what the system is set to:

```
locale
```

It should return a list of "en_" something entries for an English language system.

---

### Post by Giant Speck on 2008-03-26
If you are typing in Firefox and it shows every word being typed spelled incorrectly, simply right click where you are typing and go to Languages.  It will give you a choice of dictionaries.

I had that happen to me twice.  One time it thought I was typing in Russian, the next it thought I was typing in British English.

---

### Post by iheartubuntu on 2008-03-26
> **Giant Speck said:**
> If you are typing in Firefox and it shows every word being typed spelled incorrectly, simply right click where you are typing and go to Languages.  It will give you a choice of dictionaries.

I had that happen to me twice.  One time it thought I was typing in Russian, the next it thought I was typing in British English.

Many thanks for the tip. I already had english US and UK installed, but I was still getting misspellings on every word. It turns out the DELL factory had some other language selected as the default! I fixed it thanks to your tip.

---

