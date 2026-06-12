---
title: "Lightning 0.7 and Gutsy"
date: 2007-10-28
forum: General Help
---

### Post by michaelzap on 2007-10-28
I have a (relatively) fresh install of Gutsy with Thunderbird 2 and Lightning (both installed via Synaptic). All was fine until a couple days ago when I was notified upon starting up Thunderbird that there was an update available for the Provider for Google Calendar add-on. After I installed that, my Google calendar no longer appeared in TB.

It turns out that there is a new version of Lightning out (0.7), and the latest Provider for Google Calendar add-on requires it. So I uninstalled Lightning 0.5 via Synaptic and then downloaded the latest Lightning add-on from the Mozilla site. No matter what I do, I can't get it to work at all.

Basically, Lightning 0.7 is completely broken for me. I can't see any calendar data or any calendars in my list, and if I try to create a new calendar, task, or event it just does nothing. The display is a mess (even with the default theme) and instead of a calendar all I see are a stack of horizontal lines.

I've tried redownloading the add-on and using the latest build, but that doesn't help.

Could this have something to do with Gutsy's AppArmor? If so, I'm a little bit worried that this might happen with any number of applications. Is there a way to find out, and if it is this is there a way to circumvent it?

The repositories only have Lightning 0.5, so that means I'm stuck without a working calendar until they're updated.

Anyone else have this problem, and even better has anyone resolved it?

---

### Post by tbcurley on 2007-10-30
I am having the exact same problem, after updating to Gutsy yesterday. I tried deleting the .mozilla-thunderbird directory in the hope that it would regenerate new settings that would allow Lightning to work smoothly, but it didn't work.

---

### Post by bladefallcon on 2007-10-30
I am having the same problem myself. I have no clue what to do...

---

### Post by adaml0l on 2007-10-30
hi, im new and ive got a problem with 1 of my computer games...

i recently bought age of mythology gold and i tryed to install it on windows xp and it says"cannot load PidGen.DLL" and im getting annoyed that i cant play my game can some1 help me???

---

### Post by bladefallcon on 2007-10-30
You need to post this somewhere else. This thread has nothing to do with your problem.

---

### Post by adaml0l on 2007-10-30
like were???

---

### Post by bladefallcon on 2007-10-30
here's a thought...somewhere that has to do with the game...or maybe even the operating system you are using? Youy said you tried to install it on windows...this entire forum is for linux...not windows...you are soooooo in the wrong place..

---

### Post by magiver on 2007-11-04
i have the same problem. does anyone have thunderbird/lightning_0.7 working jet?

---

### Post by michaelzap on 2007-11-04
> **magiver said:**
> i have the same problem. does anyone have thunderbird/lightning_0.7 working jet?

It's still not working for me, and my jet's broken also.

---

### Post by dpward on 2007-11-04
Same problem for me, right after a fresh install of Gutsy and Thunderbird...

---

### Post by magiver on 2007-11-04
> **michaelzap said:**
> It's still not working for me, and my jet's broken also.
oops :oops: i´m from south america, so my english is not perfect...

anyway, i manage to solve this. the problem is that the thunderbird version that is in the repositories is not the official mozilla build or something like that. in order to get the official mozilla release you can use the [ubuntuzilla script]("http://ubuntuzilla.wiki.sourceforge.net/"). 
it worked for me. my thunderbird_2.0.0.6/lightning_0.7 is working perfectly

---

### Post by michaelzap on 2007-11-04
> **magiver said:**
> oops :oops: i´m from south america, so my english is not perfect...

anyway, i manage to solve this. the problem is that the thunderbird version that is in the repositories is not the official mozilla build or something like that. in order to get the official mozilla release you can use the [ubuntuzilla script]("http://ubuntuzilla.wiki.sourceforge.net/"). 
it worked for me. my thunderbird_2.0.0.6/lightning_0.7 is working perfectly

¡Hombre! ¡Vos me salvastes el pellejo! Tu método funciona perfectamente.

Bueno te estoy intentando hablar como Argentino, pero como vivo en Mexico a lo mejor se nota mi acento...

This is a very easy fix, and the new Lightning is nicer and Provider for Google Calendar works with it perfectly.

---

### Post by jeffla376 on 2007-11-05
I am also having the same problem. Hoping for a clue or a fix soon.

Jeff

---

### Post by michaelzap on 2007-11-05
> **jeffla376 said:**
> I am also having the same problem. Hoping for a clue or a fix soon.
Check out magiver's post above. The Ubuntzilla script does fix this 100%. I am happily using Lightning and my Google calendar today.

---

### Post by tbcurley on 2007-11-05
The ubuntuzilla script mentioned above did the trick for me, too.

---

### Post by ianmidd on 2007-11-06
Someone has already compiled a 64-bit version.  Just tried it on Gusty - Works Great!  

[http://blog.devzero.net/2007/10/lightning-07-for-x8664.html]("http://blog.devzero.net/2007/10/lightning-07-for-x8664.html")

---

