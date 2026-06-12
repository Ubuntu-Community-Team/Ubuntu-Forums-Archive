---
title: "Why does Eclipse works so unstable anb buggy on the Ubuntu?"
date: 2007-05-28
forum: General Help
---

### Post by Joe_Bishop on 2007-05-28
Eclipse works very unstable and buggy with the comparison of my Windows XP. It often suddenly crashes or freezes, and it often lost settings of its plugins, whereas I have no crashes in Windows XP and there are no lost of settings. It is criticality important, because it is possible to lost much code in this way, like me yesterday. :x

---

### Post by luisromangz on 2007-05-28
I use Eclipse everyday in Ubuntu as a mean of earning a living ;), and have no stability problems. I'm using the version from the Eclipse web page, because I dislike the gcj version which is avalaible in the repositories just because is slower, but it hadn't other problems with it.

I hope you manage to solve this, losing your code is infuriating.

---

### Post by ssadhale on 2008-03-22
My experience is pretty much the same. I have eclipse europa version for the J2EE developers on ubuntu gutsy. And its buggy as hell. It crashes time and again. Something as simple as creating a servlet using New -> Other -> Web -> Servlet doesnt work. I click on next and nothing happens. If i click multiple times, the main eclipse window vanishes because it crashes and leaves this create new servlet dialogue for me to kill. Thats crap. Never had these problems on windows! Its not a fault of ubuntu. I think the eclipse linux version is poorly maintained. Perhaps its not their main focus. But what ends up happening is that those who are trying eclipse for the first time ... if they try it on ubuntu for the first time, they will end up picking up totally wrong impression about eclipse :( and they may not come back to eclipse. No wonder there are so many people vouching for NetBeans and call eclipse buggy. Probably those are the people who burned their hands with eclipse linux combination. NetBeans is far more stable on ubuntu compared to eclipse!!

---

### Post by ssadhale on 2008-04-27
Aah! Now I have managed to solve the problem for myself. This is what I did. I went one version back on eclipse. Instead of Europa crap, go back to Calisto. I went to the WTP (Web Tools Project) page and downloaded the all in one zip. It contains the eclipse 3.2 SDK and WTP with all dependencies bundled with it. It works like a charm now. No problems whatsoever. One word of caution though. Install the Microsoft True Type fonts and set the editor fonts to look like windows. The default Java editor fonts dont look that nice otherwise.

---

### Post by ulgor on 2008-07-10
just a note:

My problems with Eclipse (32bit hardy, Eclipse Europe from the standard repository) stopped when I started running it with the sun jvm 5 instead of 6.
Now I am running both Sun's JDK 6 and jvm5, the latter for running eclipse only.

---

