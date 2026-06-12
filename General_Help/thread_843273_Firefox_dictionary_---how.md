---
title: "Firefox dictionary ---how??"
date: 2008-06-28
forum: General Help
---

### Post by antmenj on 2008-06-28
Ok I'v tryed to install Australian english dictionary in fire fox.  That didn't work so I uninstalled it and tryed british english.  That didn't work.  I restarted firefox between installed and even tryed a total reboot once.
Its an 8.04 LTS install with all updates done.

What could I be doing wrong?:confused:

---

### Post by Darkade on 2008-06-28
are you installing the dictionaries from the firefox web page?

[https://addons.mozilla.org/en-US/firefox/browse/type:3](https://addons.mozilla.org/en-US/firefox/browse/type:3)

I must say I have about four dictionaries installed and all of them work fine

---

### Post by antmenj on 2008-06-29
Yes thats the page.  In fact I just installed the aussie one as well as UK english now using your link and its still not working.

Screen shot attached

---

### Post by bikeboy on 2008-06-29
Have you right clicked in a text box, made sure check spelling is ticked and then selected the language you want to use?

---

### Post by antmenj on 2008-06-29
G'day bikeboy.  A local:)


For a moment there I was geting excited but no thats still not it.

For example I type colour and color.  Colour gets underlined but color dosn't. [see above screen shot]

It seems Rightclick text box> Check spelling does the same as Edit> Preferences> Advanced> Check my spelling as I type.

Hmm........

---

### Post by bikeboy on 2008-06-29
> **antmenj said:**
> It seems Rightclick text box> Check spelling does the same as Edit> Preferences> Advanced> Check my spelling as I type.

Hmm........

Yeah it does more or less. Some text boxes aren't spell checked by default so I was just making sure it was on for the box you were testing with - because if not on for that box you can't select the language.

Are you using the Ubuntu version of Firefox or did you download it from Mozilla? It seems strange that is isn't working, I'm out of ideas for now. It lets me use plenty of colourful language ;)

edit: go to about:config and check the value of *spellchecker.dictionary* to see that it's using en-AU - that's what mine has.

---

### Post by Darkade on 2008-06-29
yes he is using firefox from the ubuntu repos, you can tell from his screenshot. He's got ubufox addon

---

### Post by antmenj on 2008-06-29
Yes its a the standard firefox that goes with the distro.  When I did updates it went from version 3 beta to 3.

I was just thinking it may be time to have a dig in about:config .  I wouldn't have expected I'd have to but then again I wouldn't have expected the default mode to be offline mode eather.

*So do you thing 6.06 is about ready for release now its out of the beta stage :lolflag:*

Will have a go when I get home again.

---

### Post by antmenj on 2008-06-30
Ok I'v looked in about:config and found this:

browser.dictionaries.download.url       [https://%LOCALE%.add-ons.mozilla.com/%LOCALE%/firefox/%VERSION%/dictionaries/](https://%LOCALE%.add-ons.mozilla.com/%LOCALE%/firefox/%VERSION%/dictionaries/)

1 Is that what we are looking for

2 If so does it look right

---

### Post by Ozdemon on 2008-06-30
Which version of Firefox did you download.  I installed the English (British) version from:
[http://www.mozilla.com/en-US/firefox/all.html](http://www.mozilla.com/en-US/firefox/all.html)

I am now typing color. It is underlined as misspelt (to me anyway).  If it is not in yours, right-click in the text area of your Firefox message and check that under languages you have enabled en_GB.

---

