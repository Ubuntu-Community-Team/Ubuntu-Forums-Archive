---
title: "Constantly Freezing Up?"
date: 2008-07-03
forum: General Help
---

### Post by FLCL on 2008-07-03
So recently, the last couple days or so this began happening, and it's getting worse and worse. Ill be using firefox, and then ill go to a site, and then the window darkens and freezes up for a minute or so. This is happening every page now; very annoying. Even after the page has loaded, itll darken and freeze up again. Also this is happening on IM, if im typing, itll just stop typing, go dark and freeze up. This is extremely annoying, does anyone know why this is happening. It's most likely cpu spikes, but it makes no sense why it keeps spiking for no reason. Any clue?:confused:

---

### Post by powerpleb on 2008-07-03
You can open System Monitor (Applications >> Administration) and watch graphs in the resources tab to see what's happening regarding CPU and RAM.
If something is using all the CPU power or RAM up you can find out what it is in the Processes tab.

---

### Post by FLCL on 2008-07-03
Yeah, I have conky, ff3 beta 5 is whoring up my cpu at times haha. Java sometimes too, but that might be a result of it being constantly run for an app for over a day straight x.x; 

But mainly it's ff3 beta 5 thats killing me. Any suggestions?

---

### Post by nikgare on 2008-07-03
Don't use FF3 beta 5.

---

### Post by nikgare on 2008-07-03
> Don't use FF3 beta 5.

I'll try to be a bit more helpfuly ;-)

Things to try:

Upgrade to Firefox3, by either downloading directkly from Mozilla, or using the Ubuntu repos.

Remove all of the extentions that you have - some can cause problems, especially in pre-release software.

Remove all the plugins, and check that they have really been removed by going to "about:plugins" in firefox.

Run firefox from a terminal, noting any output gives when it crashes.

It wopuld probably help if before trying out a new version, you first remove the old version, and all your choices by deleting or moving the directory  ~/.mozilla/firefox

---

