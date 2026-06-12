---
title: "Firefox 2 Spell Check"
date: 2006-10-17
forum: General Help
---

### Post by TrendyDark on 2006-10-17
Firefox 2 RC2 is supposed to have a built in spell checker that checks your spelling as you type. I indeed have the option checked in my preferences, but unlike it's Windows cousin, Firefox doesn't seem to underline my typos.

Does anyone else have this problem, or a solution?

---

### Post by JonahRowley on 2006-10-17
It works for me in some places, not in other places.  For example, here in the quick reply on these forums, it doesn't work.  Does it work at all for you in any place?

---

### Post by Kateikyoushi on 2006-10-17
I do not often use it but it worked for me on this forum, even in the reply to thread window.

---

### Post by fragos on 2006-10-17
The automatic spell check doesn't seem to do anything even though selected in preferences.  Spell check in my Google bar does work.  I wonder if there's some form of conflict?

---

### Post by makhand on 2006-10-27
Mine seems to work 'too well'. apparently i misspell every single word i type!

EDIT: on further investigation, the spell check seems to expect everything to be in Russian. &#1042;&#1080;&#1076;&#1080;&#1084;&#1086; &#1101;&#1090;&#1086; &#1087;&#1088;&#1077;&#1076;&#1083;&#1086;&#1078;&#1077;&#1085;&#1080;&#1077; &#1073;&#1077;&#1079; &#1086;&#1096;&#1080;&#1073;&#1086;&#1082;! Does anyone know how to switch that sort of thing?

EDIT #2: Figured out my problem. To switch which language firefox is checking your spelling against, simply right click over the text box to find a 'Languages >' entry in the menu. Highlight that and then choose your preferred language from the resulting drop down menu. Great new feature! Now i don't have to use google toolbar's spellcheck at the end but can have my spelling checked as i type.

---

### Post by _simon_ on 2006-11-03
Despite spell check being enabled in preferences I still have to right click and select "Spell check this field" every single time.

Is there a fix for this?

I've tried disabling and re-enabling but no joy.

---

### Post by soze on 2006-11-03
> **_simon_ said:**
> Despite spell check being enabled in preferences I still have to right click and select "Spell check this field" every single time.

Is there a fix for this?

I've tried disabling and re-enabling but no joy.

The normal behavior is to only spellcheck multi-line text fields. If you want to have it always spellcheck all text fields you need to:

1. Go to about:config
2. Change the value of spellcheckDefault to 2

---

### Post by _simon_ on 2006-11-03
I haven't got a "spellcheckDefault" but I do have a "layout.spellcheckDefault", however changing the value to 2 for this has made no difference (I have tried restarting FF)

:confused:

EDIT: Spellcheck only seems to be active in single field lines i.e. when entering a topic title, but not in the forum reply boxes unless I right click and select it.

EDIT: It's only on certain forums this happens! For example, custompc forum, the spellcheck works fine but on the ubuntu forum I have to manually start it.

EDIT: Now very confused. My partner has just tried her FF2 on this forum and hers is spellchecking by default ](*,)

EDIT: SOLVED! It's down to User CP settings on individual forums. If it's set to Enhanced Editor then FF won't spellcheck by default, it has to be Standard or basic editor.

---

### Post by abbot on 2006-11-07
I'm having a different problem.  FF2 is underlining my misspelled words just fine, but when I right click on them it doesn't give me any suggested correct spellings.  It's supposed to do that right?  The spell check feature would seem a bit less useful without that.  In my right click menu I'm only given the option to turn spell check on/off or switch the dictionary language.

---

### Post by fragos on 2006-11-07
Very strange it seems to work for me.  I verified again in this response and a deliberately misspelled wasn't underline.  I right clicked it anyway and noticed a "Spell check this field" check box.  After checking it all is well.

---

### Post by babooka on 2006-11-07
Works great. With both of the languages that I've got installed.

Just right click and select "Languages" if you want to add/remove languages or enable/disable the spellcheck...

---

### Post by soze on 2006-11-08
> **abbot said:**
> I'm having a different problem.  FF2 is underlining my misspelled words just fine, but when I right click on them it doesn't give me any suggested correct spellings.  It's supposed to do that right?  The spell check feature would seem a bit less useful without that.  In my right click menu I'm only given the option to turn spell check on/off or switch the dictionary language.

Are you using the "All-in-one Gestures" add-in?
If so, it breaks the spell checker in exactly the manner you described.

---

### Post by abbot on 2006-11-09
> **soze said:**
> Are you using the "All-in-one Gestures" add-in?
If so, it breaks the spell checker in exactly the manner you described.

I am in fact using that extension.  Can you recommend another extension that will give me the ability to navigate Forward & Back using the same method (hold right mouse button & click left mouse button and vice versa)?  Thanks a lot for the info soze.

---

### Post by soze on 2006-11-16
> **abbot said:**
> I am in fact using that extension.  Can you recommend another extension that will give me the ability to navigate Forward & Back using the same method (hold right mouse button & click left mouse button and vice versa)?  Thanks a lot for the info soze.

There is an add-in called simply "Mouse Gestures" that does the exact same thing and does not break the spell checker.
-Alan

---

### Post by sh4d3z on 2007-03-02
ltes see npoe hvaing smae porbelm
it was working fine when i first installed... then i went thru all these attempts to get avi playback in totem
somewhere along the way i noticed yesturday the spellcheck stopped working (ooops yesturday should be yesterday)
not even the spell check this field is working

---

### Post by uamuzeme on 2007-05-15
I just wanted to add to the this thread, because I was having the same issue, spell check was not working at all. What solved it was installing a dictionary from here: [https://addons.mozilla.org/en-US/firefox/browse/type:3](https://addons.mozilla.org/en-US/firefox/browse/type:3) then I restarted firefox and all works as expected.

---

### Post by vtel57 on 2007-05-15
> **uamuzeme said:**
> I just wanted to add to the this thread, because I was having the same issue, spell check was not working at all. What solved it was installing a dictionary from here: [https://addons.mozilla.org/en-US/firefox/browse/type:3](https://addons.mozilla.org/en-US/firefox/browse/type:3) then I restarted firefox and all works as expected.

Good for you! That is absolutely correct! You must have a dictionary installed in FF for SpellCheck to work.

---

### Post by bodhi.zazen on 2007-11-22
> **uamuzeme said:**
> I just wanted to add to the this thread, because I was having the same issue, spell check was not working at all. What solved it was installing a dictionary from here: [https://addons.mozilla.org/en-US/firefox/browse/type:3](https://addons.mozilla.org/en-US/firefox/browse/type:3) then I restarted firefox and all works as expected.

THANK YOU !!!

I did a minimal install of Ubuntu and spelling was not working :(

Working now

---

### Post by Ian Clark on 2008-02-20
> **soze said:**
> There is an add-in called simply "Mouse Gestures" that does the exact same thing and does not break the spell checker.
-Alan

That's exactly it for me.:)

---

