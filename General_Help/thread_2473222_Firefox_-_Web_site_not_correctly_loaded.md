---
title: "Firefox - Web site not correctly loaded"
date: 2022-03-28
forum: General Help
---

### Post by foosterh on 2022-03-28
Hello

using Ubuntu 20.04 TLS and packaged Firefox browser I notice that the following web site is not correctly loaded (the only web site for the moment that gives me this issue):

www(dot)telegraaf(dot)nl

The page is accessed for a second or so after which the pages blanks.
The blank page is loaded from:

https://www(dot)telegraaf(dot)nl/error?ref=/&refSource={location}&message=&method=&file=&stack=Pc%40https%3A%2F%2Fwww.telegraaf.nl%2Fcdn%2Fstatics%2Fapp.2.3.200.281088.js%3A105%3A167467%0Askip%40https%3A%2F%2Fwww.telegraaf.nl%2Fcdn%2Fstatics%2Fapp.2.3.200.281088.js%3A105%3A168922%0AN%2F%3C%2F%3C%2Fs%3C%2Fu.prototype.render%40https%3A%2F%2Fwww.telegraaf.nl%2Fcdn%2Fstatics%2Fapp.2.3.200.281088.js%3A21%3A30479%0AFa%40https%3A%2F%2Fwww.telegraaf.nl%2Fcdn%2Fstatics%2Fapp.2.3.200.281088.js%3A77%3A69876%0AMa%40https%3A%2F%2Fwww.telegraaf.nl%2Fcdn%2Fstatics%2Fapp.2.3.200.281088.js%3A77%3A69671%0Avs%40https%3A%2F%2Fwww.telegraaf.nl%2Fcdn%2Fstatics%2Fapp.2.3.200.281088.js%3A77%3A105470%0Acu%40https%3A%2F%2Fwww.telegraaf.nl%2Fcdn%2Fstatics%2Fapp.2.3.200.281088.js%3A77%3A96719%0Asu%40https%3A%2F%2Fwww.telegraaf.nl%2Fcdn%2Fstatics%2Fapp.2.3.200.281088.js%3A77%3A96642%0AZs%40https%3A%2F%2Fwww.telegraaf.nl%2Fcdn%2Fstatics%2Fapp.2.3.200.281088.js%3A77%3A93672%0AGo%2F%3C%40https%3A%2F%2Fwww.telegraaf.nl%2Fcdn%2Fstatics%2Fapp.2.3.200.281088.js%3A77%3A45314%0At.unstable_runWithPriority%40https%3A%2F%2Fwww.telegraaf.nl%2Fcdn%2Fstatics%2Fapp.2.3.200.281088.js%3A85%3A3844%0Aqo%40https%3A%2F%2Fwww.telegraaf.nl%2Fcdn%2Fstatics%2Fapp.2.3.200.281088.js%3A77%3A45023%0AGo%40https%3A%2F%2Fwww.telegraaf.nl%2Fcdn%2Fstatics%2Fapp.2.3.200.281088.js%3A77%3A45261%0A%24o%40https%3A%2F%2Fwww.telegraaf.nl%2Fcdn%2Fstatics%2Fapp.2.3.200.281088.js%3A77%3A45194%0AQs%40https%3A%2F%2Fwww.telegraaf.nl%2Fcdn%2Fstatics%2Fapp.2.3.200.281088.js%3A77%3A90457%0AenqueueForceUpdate%40https%3A%2F%2Fwww.telegraaf.nl%2Fcdn%2Fstatics%2Fapp.2.3.200.281088.js%3A77%3A49296%0Aw.prototype.forceUpdate%40https%3A%2F%2Fwww.telegraaf.nl%2Fcdn%2Fstatics%2Fapp.2.3.200.281088.js%3A69%3A1384%0At%2Fr.updateCurrentData%40https%3A%2F%2Fwww.telegraaf.nl%2Fcdn%2Fstatics%2Fapp.2.3.200.281088.js%3A21%3A17054%0Anext%40https%3A%2F%2Fwww.telegraaf.nl%2Fcdn%2Fstatics%2Fapp.2.3.200.281088.js%3A21%3A16695%0Ag%40https%3A%2F%2Fwww.telegraaf.nl%2Fcdn%2Fstatics%2Fapp.2.3.200.

Specific output needed to analyse? Just ask me.

Thanks
Fred

---

### Post by #&amp;thj^% on 2022-03-28
Loads fine here.
any proxy's or vpn's?

---

### Post by CharlesA on 2022-03-28
You might have better luck by launching the browser dev tools (F12, or similar) and going to the Network tab to see what is going on or if there are any errors displayed.

---

### Post by foosterh on 2022-03-29
Hi Charles

F12 produces too many info which is beyond my knowledge. However F12 / Console might give a clue as it contains lines like the following:
Request to access cookie or storage on &#8220;[https://sb.scorecardresearch.com/cs/12344628/beacon.js&#8221;](https://sb.scorecardresearch.com/cs/12344628/beacon.js&#8221;) was blocked because it came from a tracker and content blocking is enabled.

In web sites that do load such lines are absent.

Let me look better into this including the area of trackers so see if I can make it working.

Regards
Fred

---

### Post by CharlesA on 2022-03-29
> **foosterh said:**
> Hi Charles

F12 produces too many info which is beyond my knowledge. However F12 / Console might give a clue as it contains lines like the following:
Request to access cookie or storage on “[https://sb.scorecardresearch.com/cs/12344628/beacon.js”](https://sb.scorecardresearch.com/cs/12344628/beacon.js”) was blocked because it came from a tracker and content blocking is enabled.

In web sites that do load such lines are absent.

Let me look better into this including the area of trackers so see if I can make it working.

Regards
Fred

That's definitely a tracker, but that shouldn't have caused the entire site to break.

Are you using any addons in Firefox?

---

### Post by pakchamp on 2022-03-30
if your website is correctly load these are many reason. your web server are most imporent this you should move right server and you site data is overload please remove unused data

---

### Post by mIk3_08 on 2022-03-30
> **foosterh said:**
> Hello

using Ubuntu 20.04 TLS and packaged Firefox browser I notice that the following web site is not correctly loaded (the only web site for the moment that gives me this issue):

www(dot)telegraaf(dot)nl

The page is accessed for a second or so after which the pages blanks.
The blank page is loaded from:

https://www(dot)telegraaf(dot)nl/error?ref=/&refSource={location}&message=&method=&file=&stack=Pc%40https%3A%2F%2Fwww.telegraaf.nl%2Fcdn%2Fstatics%2Fapp.2.3.200.281088.js%3A105%3A167467%0Askip%40https%3A%2F%2Fwww.telegraaf.nl%2Fcdn%2Fstatics%2Fapp.2.3.200.281088.js%3A105%3A168922%0AN%2F%3C%2F%3C%2Fs%3C%2Fu.prototype.render%40https%3A%2F%2Fwww.telegraaf.nl%2Fcdn%2Fstatics%2Fapp.2.3.200.281088.js%3A21%3A30479%0AFa%40https%3A%2F%2Fwww.telegraaf.nl%2Fcdn%2Fstatics%2Fapp.2.3.200.281088.js%3A77%3A69876%0AMa%40https%3A%2F%2Fwww.telegraaf.nl%2Fcdn%2Fstatics%2Fapp.2.3.200.281088.js%3A77%3A69671%0Avs%40https%3A%2F%2Fwww.telegraaf.nl%2Fcdn%2Fstatics%2Fapp.2.3.200.281088.js%3A77%3A105470%0Acu%40https%3A%2F%2Fwww.telegraaf.nl%2Fcdn%2Fstatics%2Fapp.2.3.200.281088.js%3A77%3A96719%0Asu%40https%3A%2F%2Fwww.telegraaf.nl%2Fcdn%2Fstatics%2Fapp.2.3.200.281088.js%3A77%3A96642%0AZs%40https%3A%2F%2Fwww.telegraaf.nl%2Fcdn%2Fstatics%2Fapp.2.3.200.281088.js%3A77%3A93672%0AGo%2F%3C%40https%3A%2F%2Fwww.telegraaf.nl%2Fcdn%2Fstatics%2Fapp.2.3.200.281088.js%3A77%3A45314%0At.unstable_runWithPriority%40https%3A%2F%2Fwww.telegraaf.nl%2Fcdn%2Fstatics%2Fapp.2.3.200.281088.js%3A85%3A3844%0Aqo%40https%3A%2F%2Fwww.telegraaf.nl%2Fcdn%2Fstatics%2Fapp.2.3.200.281088.js%3A77%3A45023%0AGo%40https%3A%2F%2Fwww.telegraaf.nl%2Fcdn%2Fstatics%2Fapp.2.3.200.281088.js%3A77%3A45261%0A%24o%40https%3A%2F%2Fwww.telegraaf.nl%2Fcdn%2Fstatics%2Fapp.2.3.200.281088.js%3A77%3A45194%0AQs%40https%3A%2F%2Fwww.telegraaf.nl%2Fcdn%2Fstatics%2Fapp.2.3.200.281088.js%3A77%3A90457%0AenqueueForceUpdate%40https%3A%2F%2Fwww.telegraaf.nl%2Fcdn%2Fstatics%2Fapp.2.3.200.281088.js%3A77%3A49296%0Aw.prototype.forceUpdate%40https%3A%2F%2Fwww.telegraaf.nl%2Fcdn%2Fstatics%2Fapp.2.3.200.281088.js%3A69%3A1384%0At%2Fr.updateCurrentData%40https%3A%2F%2Fwww.telegraaf.nl%2Fcdn%2Fstatics%2Fapp.2.3.200.281088.js%3A21%3A17054%0Anext%40https%3A%2F%2Fwww.telegraaf.nl%2Fcdn%2Fstatics%2Fapp.2.3.200.281088.js%3A21%3A16695%0Ag%40https%3A%2F%2Fwww.telegraaf.nl%2Fcdn%2Fstatics%2Fapp.2.3.200.

Specific output needed to analyse? Just ask me.

Thanks
Fred Maybe its in your internet because it also loads to me very fine or maybe your Firefox browser needs to be updated. Good Luck and cheers

---

### Post by foosterh on 2022-04-06
Hello

i followed the firefox trouble shooting page at [https://support.mozilla.org/en-US/kb/troubleshoot-and-diagnose-firefox-problems](https://support.mozilla.org/en-US/kb/troubleshoot-and-diagnose-firefox-problems)
After clearing all the options in the cookies & cache the issue disappeared.

Leaving me still not knowing why ...

Regards
Fred

---

