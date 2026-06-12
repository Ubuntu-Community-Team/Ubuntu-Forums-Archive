---
title: "ubuntu WINE and Lotus Notes"
date: 2005-04-21
forum: General Help
---

### Post by rpm on 2005-04-21
Hi all,

I m a Lotus Notes/Domino DBA and I would like to make the switch to ubuntu linux or at least make room for a new patition dedicated to it.

A dual boot pc could be a solution for my needs but unfortunately there is no Lotus Notes Client natively available for linux. 

I know this could be installable using CrossXover Office but I was wondering if this could be accomplished too with WINE (upon of which is built crossxover office).

Can someone help me with this problem?

Can really wine be an alternative free solution or I have to pay for CrossXOver Office ?

Have you ever tried to run Lotus Notes on linux ?

thx

rpm

---

### Post by bnutting on 2005-04-21
We us WINE to run Lotus Notes in our 700+ store chain. Be very careful which version of WINE you install, because Lotus Notes only plays nice with particular ones. Notes is *VERY* usable under WINE but some things are a little flaky you would have to test it to make sure things work as expected.

Bryan

---

### Post by philcolbourn on 2005-04-21
I and a few others used wine and notes for several years. I stopped when i had no success installing r6, but that was a year ago. I think IBM switched to using the new fancy installer which wine did not support at the time.

I had a few wine version problems from memory. I generally used debian unstable.
 I found it to work very well and it was very stable. Probably because notes used so few windows dlls and it would still run ok on w95 so I suspect the API calls were old ones and fairly well documented and debugged.

---

### Post by rpm on 2005-04-21
Have you tried it too on ubuntu yet ?

And which version of wine is best suited for this job ? (for R6)

I have absoutely no experience with WINE can you help me or guide me a little ?

thx

rpm

---

### Post by shakin on 2005-04-21
[QUOTE=rpm]Have you tried it too on ubuntu yet ?

And which version of wine is best suited for this job ? (for R6)

I have absoutely no experience with WINE can you help me or guide me a little ?

thx

rpm[/QUOTE]

I assume that the latest version of Wine would be fine because Wine features don't regress from old versions.

Have a look at [my how-to for installing DVD Decrypter with Wine](http://www.ubuntuforums.org/showthread.php?t=27369). Skip to section 2 where I show how to install Wine from Wine's own software repository and use winetools to get it configured properly.

---

### Post by rpm on 2005-04-21
thank you very much

rpm

---

### Post by bnutting on 2005-04-21
One thing we have learned here with Wine is not to assume that the newest version of Wine is the best, at least not when it comes to Lotus Notes. We run R5 on our stores with Wine version wine-20020710. This is on SuSE 7.3, so I'm sure things may be different with Ubuntu. You may have to play with a couple different versions of Wine to get the 'right' one.

Bryan

---

### Post by philcolbourn on 2005-05-21
I generally used unstable debian when I had notes installed. I didn't have too many failures (I can't recall any major ones).

R6 initially would not install. I haven't tried recently. If I get time, I'll try on breezy - it may not be the same on hoary.

In the past you had to tweak wine to get notes working. But more recently wine has special configs for lotus notes installed and these seemed to work fine.

Notes uses very few windows dlls and so it is easily supported on wine.

Also, I wrote this howto (see below - someone even translated it into russian!) a long time ago (circa r5.0 in 2001?). It explains how to get r5 working on wine, but I think it is almost foolproof now. The only catch would be whether wine can run the new windows installer. If it can not, it will get messy but it is probably not impossible. I would install a shared client somewhere, and copy the files to your linux box (in the .wine/ directory) and copy a working notes data directory, and fixup a notes.ini file and it will probably work ok (but windows registry things will not work).

[http://www.keysolutions.com/NotesFAQ/canclient.html](http://www.keysolutions.com/NotesFAQ/canclient.html)

---

### Post by elsewhere on 2005-05-21
I had installed R6 under Wine in FC3, although I think the principle should be the same for Ubuntu.  At the time, I found a link in IBM's site that guided me, I just looked for it but can't find it anymore, I think it was part of an engineer's blog or something to that effect.

The trick was to do an install in Windows and copy the notes directory intact over (I don't think mounting a shared one was recommended, but I could be wrong) and run it with wine, as mentioned above the installer will not work under wine.  As also mentioned above, a couple of mods to the notes.ini file were required but that was pretty much it.  Everything worked properly except the sametime client (I never really tried to, and I think there's a Java client available anyways) and integrated web browsing which defaults to use IE.  The one catch was that I also think I had to copy one of my Windows .dll's over to wine as well, not an issue under dual boot since it resides on the same system, but could be a licensing issue if you're running only linux.

Anyways, sorry I can't be more specific, it was over a year ago and I never bothered re-installing when I converted to Kubuntu.  I find it easier to just use Domino Web Access, which works very well with Firefox.

But FWIW, I can attest that R6 runs under Wine and since I was able to do it myself, it can't be too difficult...   ;-) Google will probably be your best friend for this, that's how I found the info on IBM's site originally.

Hope this helps somewhat ?

Cheers,
KV

---

### Post by philcolbourn on 2005-05-21
[QUOTE=elsewhere]I had installed R6 under Wine in FC3, although I think the principle should be the same for Ubuntu.  At the time, I found a link in IBM's site that guided me, I just looked for it but can't find it anymore, I think it was part of an engineer's blog or something to that effect.

The trick was to do an install in Windows and copy the notes directory intact over (I don't think mounting a shared one was recommended, but I could be wrong) and run it with wine, as mentioned above the installer will not work under wine.  As also mentioned above, a couple of mods to the notes.ini file were required but that was pretty much it.  Everything worked properly except the sametime client (I never really tried to, and I think there's a Java client available anyways) and integrated web browsing which defaults to use IE.  The one catch was that I also think I had to copy one of my Windows .dll's over to wine as well, not an issue under dual boot since it resides on the same system, but could be a licensing issue if you're running only linux.

Anyways, sorry I can't be more specific, it was over a year ago and I never bothered re-installing when I converted to Kubuntu.  I find it easier to just use Domino Web Access, which works very well with Firefox.

But FWIW, I can attest that R6 runs under Wine and since I was able to do it myself, it can't be too difficult...   ;-) Google will probably be your best friend for this, that's how I found the info on IBM's site originally.

Hope this helps somewhat ?

Cheers,
KV[/QUOTE]
 That sounds about right. As I wrote above, the registry will  not be right but that will only affect other apps running under wine from launching notes mail etc. It will also mean that shell commands will not know what a nsf file is, but these shouldn't matter.

I think notes installs a notes.ini and a lotus.ini file in c:\windows so these should be moved as well.

You can fix the registry by manually editing a file in the notes directory (something.reg) to change %notesdir% to the actual notes directory and adding it to the wine registry. remember to use double backslashes for each backslash. eg. c:\\lotes\\notes\\etc.

---

