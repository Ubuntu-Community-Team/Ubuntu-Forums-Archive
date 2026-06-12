---
title: "k3b &quot;could not unlock cd drive&quot;"
date: 2005-07-26
forum: General Help
---

### Post by royg1234 on 2005-07-26
k3b "could not unlock cd drive" -- anyone know how to fix this?  Thanks.

---

### Post by Emerzen on 2005-08-20
Hey, I'm having the same problem.  One workaround is to open a terminal and use the following command;  $gksudo k3b

Make sure to use the gksudo and not sudo command...sudo alone will mess up your ICEauthority config files.  If this works you can add an applet w/ this command at the top.  Hope that helps.

---

### Post by felixj on 2005-12-19
for further reference...

I had the same problem when trying to burn an audio-cd from mp3-files (which worked nicely before). K3b starts writing but got stuck at 59%. Message "could not unlock..."

I tried the $gksudo k3b-thingie: Also got stuck at 59%. Message: "There was an error decoding audio-files" (or similar)

Then I tried to burn another audio-cd from mp3 (without gksudo): worked nicely as before.

So I conclude: This is not a problem with k3b but a problem with errors in one of the mp3-files. Poor encoding... I might be wrong, but this is what happened here.

Messed up a couple of discs, so I post this to save others the hassle.

---

