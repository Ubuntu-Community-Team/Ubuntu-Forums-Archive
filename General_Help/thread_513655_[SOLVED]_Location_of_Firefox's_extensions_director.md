---
title: "[SOLVED] Location of Firefox's extensions directory"
date: 2007-07-30
forum: General Help
---

### Post by Jong on 2007-07-30
When I'm searching for Firefox's extensions directory, multiple appears. I went through them all, though I cannot seem to find the right one.

I want to edit an extension named Thinger (at) blueprintit (dot) co (dot) uk (titled as so in Windows), but searching for it returns no result. It's installed correctly and in use.

In /usr/lib/firefox it's not, neither in /usr/share/firefox

Where should I look for it?

---

### Post by aysiu on 2007-07-30
Look in ~/.mozilla or /home/*username*/.mozilla

.mozilla is a hidden directory. Press Control-H to see it.

For example, my extensions are in ```
~/.mozilla/firefox/11kfdfrr.default/extensions
```

---

### Post by mikecool36 on 2007-07-30
From what I know about firefox is that it normally keeps these kind of settings inside a profile.  That way if for some reason a extension messes up firefox you just create a new profile and can start using it again.

I have had a look on my system and think I may have found what you are looking for.  Go to your home directory and make sure you can view hidden files.  

Then go to ..mozilla/firefox/(profile name)/extensions and that extension you were talking about should be there.

---

### Post by mikecool36 on 2007-07-30
> **aysiu said:**
> Look in ~/.mozilla or /home/*username*/.mozilla

.mozilla is a hidden directory. Press Control-H to see it.

For example, my extensions are in ```
~/.mozilla/firefox/11kfdfrr.default/extensions
```

you beat me to it lol

---

### Post by Jong on 2007-07-30
Thank you both :)

---

