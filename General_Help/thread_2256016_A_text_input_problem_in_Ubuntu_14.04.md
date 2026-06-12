---
title: "A text input problem in Ubuntu 14.04"
date: 2014-12-09
forum: General Help
---

### Post by afuori on 2014-12-09
Okay, I've done some poking around and after not finding anything even remotely close to the sort, here or elsewhere online, I thought that I would blow your mind.
Ubuntu 14.04 on an i7 processor, perfect in almost every way (Hibernate works, can't recall running into any problem that took more than an hour or two to fix and while Conky, Unitiy and compiz have all crashed at one time or another, restarting them through the terminal has always completely remedied the problem and resulted in a stable system for hours to follow)...

Except when certain text fields decide to ignore me almost entirely in varring flavors of weird ranging from inconvient to full blown WTF. 
It starts with one and then spreads like a cold the longer the uptime since the first occurance. 
Restart the computer and the problems are gone.

Ex: A search bar similar to the one in the top right of this page. Click it and you get your familiar flashing cursor. Type and each keystroke deletes all of the input before it. 
Yeah, I get it bugs happen but take that as the baseline bug and add in the following flavors of weird.

-It's usually Firefox that is the first to go but it can effect stock system programs too like when trying to edit a folder name via file manager GUI.
-There have been times where 'p' is the only charecter that won't delete all the others.
-There have been times where a vowel following a consenant doesn't delete either (any 3rd keystroke will delete the 2 regardless).
-There are times where holding down shift for the duration of the input permits it without deleting it. Will not always be an acceptable work around though.
-There are times where Ctrl+v works, other times when it doesn't.
-There are times where Right click --> Paste works, other times it doesn't. 
-Other input fields on the same page in the same window are generally completely functional while the other one refuses input.
-The on-screen keyboard has not, to date, ever been a viable workaround.
-In Twitter, any attempts to type at the cursor would appear at the start of the input field and deletes and backspaces were nothing short of unpredictable.

-To make things a little more interesting, let's throw in the fact that reloading Unity, compiz or both through the terminal have not once solved the problem (at least that I can remember).

Now I've given this one my best shot on many occassions, the only substantial evidence I've seen in the code was when debugging a malfunctioning webpage search bar, a line of code flashed on every keypress except 'p' and would highlight upon pressing shift then after a longer period than a regular keypress flash (while still pressing shift) the highlight would fade and all the keypresses that followed would be accepted (as I said previously). 
The flashing string in the debugger was this: <div id="header-search-container" class="form-control ui-front open">

Unfortunately, I really don't have any formal coding experience whatsoever; just a really good intuition from having 2 programming parents and poking around in Windows systems since I was 3 or 4. I honestly wouldn't be able to say whether that piece has anything wrong with it but I got a feeling that it doesn't: it seems innocent enough, ran fine when I saved it and the child strings as their own file then opened it in the same instance of Firefox not to mention this wouldn't explain the problem appearing in native windows. 

At this point, a  '--replace' type solution would be a perfectly acceptable workaround. With a force-restart at my disposal, I would have nothing against taking my sweet time actually coming up with a permanent fix. Again though, I have no idea where to start on this one. I cannot resolve this massive post into a bug report either until i've cleared my 10 post cap.caused the problem. Anyone with even the most vauge *scent* of an idea, please feel free to discuss.

---

