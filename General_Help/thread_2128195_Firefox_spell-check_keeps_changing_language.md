---
title: "Firefox spell-check keeps changing language"
date: 2013-03-22
forum: General Help
---

### Post by Paddy Landau on 2013-03-22
I am in the UK, and so I have my Firefox spell-checker set to "English (United Kingdom)".

However, frequently I find a word highlighted as misspelled, and discover that Firefox has reset my spell-checker to "English (Canadian)". (Frustratingly, it has just done it again!)

This is only a minor irritation, of course, but how can I stop Firefox from doing this?
[ATTACH=CONFIG]240433[/ATTACH]

---

### Post by dcstar on 2013-03-23
> **Paddy Landau said:**
> I am in the UK, and so I have my Firefox spell-checker set to "English (United Kingdom)".

However, frequently I find a word highlighted as misspelled, and discover that Firefox has reset my spell-checker to "English (Canadian)". (Frustratingly, it has just done it again!)

This is only a minor irritation, of course, but how can I stop Firefox from doing this?
[ATTACH=CONFIG]240433[/ATTACH]

```
Edit-Preferences-Content-Languages
```
And delete the ones you don't want.

---

### Post by dcstar on 2013-03-23
> **Paddy Landau said:**
> I am in the UK, and so I have my Firefox spell-checker set to "English (United Kingdom)".

However, frequently I find a word highlighted as misspelled, and discover that Firefox has reset my spell-checker to "English (Canadian)". (Frustratingly, it has just done it again!)

This is only a minor irritation, of course, but how can I stop Firefox from doing this?
[ATTACH=CONFIG]240433[/ATTACH]

```
Edit-Preferences-Content-Languages
```
And delete the ones you don't want.

You may also have to manually delete the unwanted Dictionary files from your system.

Also in Firefox "about:config" look for the key "spellchecker.dictionary" and reset it (if necessary).

Another solution is: [https://support.mozilla.org/en-US/questions/953907](https://support.mozilla.org/en-US/questions/953907)

---

### Post by Paddy Landau on 2013-03-23
> **dcstar said:**
> Edit-Preferences-Content-Languages
That section already had what I wanted:
```
English/United Kingdom [en_gb]
English [en]
```

> **dcstar said:**
> Also in Firefox "about:config" look for the key "spellchecker.dictionary" and reset it (if necessary).
That was [FONT=lucida console]en_CA[/FONT], which explains the problem (but what set it to [FONT=lucida console]en_CA[/FONT] in the first place?). I reset it to [FONT=lucida console]en_GB[/FONT]. Strangely, restarting Firefox did not solve the problem, but restarting the computer did!

So, that solved the problem, thank you. If it should resurface, I'll have a look at the other options you gave.

---

### Post by dcstar on 2013-03-27
> **Paddy Landau said:**
> .........
That was [FONT=lucida console]en_CA[/FONT], which explains the problem (but what set it to [FONT=lucida console]en_CA[/FONT] in the first place?). I reset it to [FONT=lucida console]en_GB[/FONT]. Strangely, restarting Firefox did not solve the problem, but restarting the computer did!

So, that solved the problem, thank you. If it should resurface, I'll have a look at the other options you gave.

The latest versions of Linux Firefox also broke my Australian spelling settings, I'd say someone made a mistake........

---

### Post by Paddy Landau on 2013-04-02
And it has just happened again, today! So weird!

Fixing the [FONT=lucida console]spellchecker.dictionary[/FONT] in [FONT=lucida console]about:config[/FONT] fixed it. Again.

Do you know if there is a bug reported for this?

---

