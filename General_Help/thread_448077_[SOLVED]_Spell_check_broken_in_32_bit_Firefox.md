---
title: "[SOLVED] Spell check broken in 32 bit Firefox"
date: 2007-05-18
forum: General Help
---

### Post by noerrorsfound on 2007-05-18
When using the 32 bit version of Firefox 2.0.0.3, misspelled words are not underlined in red as they are when using the 64 bit version. I now use only  the 32 bit version because I don't want to switch whenever I need to use the Flash plugin.

---

### Post by vtel57 on 2007-05-19
Do you have a dictionary installed for your spellcheck extension?

See [HERE](http://dictionaries.mozdev.org/installation.html)

Luck!

---

### Post by noerrorsfound on 2007-05-19
Thank you for attempting to help me, but unfortunately that did not fix the problem. I even ran firefox32 using sudo and installed it that way but it still did not work.

---

### Post by vtel57 on 2007-05-19
Do you have an entry in Firefox --> Tools --> Addons --> Extensions for SpellBound II 2.1? If so, check the Preferences on that extension and make sure that a dictionary is in use for the extension.

---

### Post by noerrorsfound on 2007-05-19
> **vtel57 said:**
> Do you have an entry in Firefox --> Tools --> Addons --> Extensions for SpellBound II 2.1? If so, check the Preferences on that extension and make sure that a dictionary is in use for the extension.
Apparently I don't have SpellBound installed at all, which is odd because the spell checker is supposed to be included in Firefox 2.

I went here to install it:
[http://spellbound.sourceforge.net/index](http://spellbound.sourceforge.net/index)

When installing I was told that it's not compatible.

---

### Post by vtel57 on 2007-05-19
Hmm... FF 2.0 was supposed to include SpellBound as the default spell checker. I'm afraid I'm stumped at this point. :(

You might try searching the [Mozillazine Forums](http://www.mozillazine.org/) for similar posts to what you're experiencing.

---

### Post by noerrorsfound on 2007-05-19
> **vtel57 said:**
> Hmm... FF 2.0 was supposed to include SpellBound as the default spell checker. I'm afraid I'm stumped at this point. :(

You might try searching the [Mozillazine Forums](http://www.mozillazine.org/) for similar posts to what you're experiencing.
I found this link to Spellbound-II-2.2 from a quick search on those forums:
[http://webdesigns.ms11.net/chromeditp.html#spellbound](http://webdesigns.ms11.net/chromeditp.html#spellbound)

It has replaced the default spell check although it does not underline words in text boxes as it's supposed to. I can, however, right click in the text box and click Check Spelling, which is better than nothing.

---

### Post by vtel57 on 2007-05-19
> **noerrorsfound said:**
> I found this link to Spellbound-II-2.2 from a quick search on those forums:
[http://webdesigns.ms11.net/chromeditp.html#spellbound](http://webdesigns.ms11.net/chromeditp.html#spellbound)

It has replaced the default spell check although it does not underline words in text boxes as it's supposed to. I can, however, right click in the text box and click Check Spelling, which is better than nothing.

I'm running FF 2.0 in seven GNU/Linux distributions (Ubuntu, Debian, Fedora Core, OpenSuSE, Slackware, Mepis, and Mandriva) and one WinXP Pro install. In **every one** of those operating systems, my FF underlines misspelled words.

Here's something... check this:

Firefox --> Edit --> Preferences --> Advanced --> General tab --> Browsing (middle of the window) --> make sure "Check my spelling as I type" is checked.

---

### Post by noerrorsfound on 2007-05-20
> **vtel57 said:**
> Firefox --> Edit --> Preferences --> Advanced --> General tab --> Browsing (middle of the window) --> make sure "Check my spelling as I type" is checked.
That was the problem. For some reason that was not checked, and I don't remember unchecking it (I would not have done it on purpose).

The solution was so simple, yet I somehow didn't see that check box when looking over the preferences. #-o

---

### Post by vtel57 on 2007-05-20
Heh! After spending 20+ years in component level repair of RF Comm (radio) and Audio electronics devices, I can tell you that the number one troubleshooting step is to look for the simple things first. ;)

Glad that fixed it for you! 

Enjoy your GNU/Linux experiences! :)

~Eric

---

