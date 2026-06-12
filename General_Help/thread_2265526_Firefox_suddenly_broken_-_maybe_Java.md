---
title: "Firefox suddenly broken - maybe Java?"
date: 2015-02-15
forum: General Help
---

### Post by Doug_Van on 2015-02-15
Thanks for everyone's time in advance.

I suddenly started having issues the other day with firefox (chrome still works fine). It appears to be an issue with java basically not functioning at all but I don't know enough about java to be sure. I've attached an image of the ubuntu community forum page as it currently loads in firefox.

I am not sure what to do. I have tried installing a both openjdk-7-jre and oracle-java8-installer and enabling/disabling the plugin through the firefox GUI.

Also, my java version right now reads:
java version "1.8.0_31"
Java(TM) SE Runtime Environment (build 1.8.0_31-b13)
Java HotSpot(TM) 64-Bit Server VM (build 25.31-b07, mixed mode)

Any ideas on what might be wrong?

---

### Post by Holger_Gehrke on 2015-02-16
No, the page in the screenshot doesn't use Java at all. Quite a bit of JavaScript, but no Java (completely different Language that's called in a completely different way; the similarity in names is a marketing issue, not a technical one). And the completely broken display looks more like a problem with CSS than one with JavaScript.

Do you have NoScript installed ? Or some kind of userspecific CSS override ?

---

### Post by Doug_Van on 2015-02-16
It was adblock edge. Thank you for the help. It was really easy with your bit of prompting!

---

