---
title: "any way to fix freezing browser with online shard collaborative documents?"
date: 2020-05-12
forum: General Help
---

### Post by anotherChris on 2020-05-12
My work started using Microsoft Office 365 to share and collaboratively modify documents (mostly Excel spreadsheets).  I am using Lubuntu 20.04 and Firefox.  Everything is completely updated.  However, I can only make about 3 or 4 modifications in these documents before everything starts slowing down.  After maybe 7-8 modifications, my computer (cursor, mouse, etc) freezes, and I have to hard re-start.

(This freezing problem only occurs for me in this Office 365 website and sometimes on YouTube if I have more than 2 browser tabs open of YouTube.  Other websites not a problem.  I am assuming that O365 has too many scripts running in the background, but since it starts off okay and gets progressively slower, I wonder if there is a way to improve things...)

Is there a way I can fix/improve performance with this MS Office website?

---

### Post by dragonfly41 on 2020-05-13
Have you considered using Google Sheets instead?

---

### Post by anotherChris on 2020-05-13
> **dragonfly41 said:**
> Have you considered using Google Sheets instead?

HAHAHAHAHAHAHAHHAHAHAHA!!!!!!!!   When I said "My work", I meant the company I work for, not my company.  It's a large corporation, and I have no say in what we use.

---

### Post by TheFu on 2020-05-13
I can hear the MSFT web-app devs laughing about how only "Edge", or whatever the MSFT browser is, will work correctly with their Office web-apps.  

Might try Chromium browser instead of firefox. You can run it inside a firejail sandbox to limit access to the local system.
I have two firejail aliases:
```
alias firechrome='firejail chromium-browser --js-flags=--noexpose_wasm '
alias firepchrome='firejail --private chromium-browser --js-flags=--noexpose_wasm '
```
The "private" option doesn't allow anything to be saved on the local storage. A temporary file system overlay gets created before launching chromium.  No settings or addons are retained between program runs.

The other alias allows access to selected parts of $HOME, so settings, addons, etc. are retained between each run, but it is still a constrained environment.  No idea if chromium inside a snap will work inside a firejail. Sorry.

---

### Post by dragonfly41 on 2020-05-13
[Brave browser?]("https://www.petri.com/brave-browser-office365")

---

### Post by anotherChris on 2020-05-14
Thanks for all the advices.

---

### Post by anotherChris on 2020-05-18
> **TheFu said:**
> I can hear the MSFT web-app devs laughing about how only "Edge", or whatever the MSFT browser is, will work correctly with their Office web-apps.

I think you mean cackling, not laughing.

> **TheFu said:**
> Might try Chromium browser instead of firefox. You can run it inside a firejail sandbox to limit access to the local system.
I have two firejail aliases:
```
alias firechrome='firejail chromium-browser --js-flags=--noexpose_wasm '
alias firepchrome='firejail --private chromium-browser --js-flags=--noexpose_wasm '
```
The "private" option doesn't allow anything to be saved on the local storage. A temporary file system overlay gets created before launching chromium.  No settings or addons are retained between program runs.

The other alias allows access to selected parts of $HOME, so settings, addons, etc. are retained between each run, but it is still a constrained environment.  No idea if chromium inside a snap will work inside a firejail. Sorry.

> **dragonfly41 said:**
> [Brave browser?]("https://www.petri.com/brave-browser-office365")

Thank you, TheFu and dragonfly41.  You might be interested to continue following this topic in this other thread...  
[https://ubuntuforums.org/showthread.php?t=2443565&p=13958297&viewfull=1#post13958297](https://ubuntuforums.org/showthread.php?t=2443565&p=13958297&viewfull=1#post13958297)

---

