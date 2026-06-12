---
title: "Google Maps hangs Chromium (but not Firefox)"
date: 2014-07-08
forum: General Help
---

### Post by Paddy Landau on 2014-07-08
Google Maps used to work perfectly with Chromium.

Recently, this has changed. (Until yesterday, I hadn't used Maps for a fortnight, so I'm not sure quite how recently this changed.)

Now, Google Maps works at first, but as soon as I try to scroll the map, Chromium hangs and I have to force-kill it. This includes any type of scrolling, e.g. when asking for directions to a location.

I've tried disabling all of my Chromium extensions in case one of them was causing the problem, but that made no difference.

While Chromium is hanging, the System Monitor reports a full 1.1 Gb free RAM; no swap in use; all CPU's quiet (under 7%); and no Internet activity.

However, Firefox works perfectly with Google Maps, even while Chromium is hanging.

I am using Ubuntu 14.04 64-bit, fully updated.

Do you have any ideas on how to resolve this problem, please?

---

### Post by patsev-anton on 2014-07-12
Using --disable-accelerated-compositing

---

### Post by Paddy Landau on 2014-07-12
> **patsev-anton said:**
> Using --disable-accelerated-compositing
Do you mean the following?
```
chromium-browser --disable-accelerated-compositing
```
I have tried that, and it doesn't work. The manual for [FONT=lucida console]chromium-browser[/FONT] doesn't show that option, so I'm not sure that it is valid anyway.

However, your suggestion has allowed me to find something that does work! After some new Googling about composting, I did the following.
[LIST]
[*]Go to [chrome://flags/](chrome://flags/)
[*]Change *GPU compositing on all pages* to *Disabled*.
[*]Restart Chromium.
[/LIST]
It's early days yet, but so far it's working. I'll post back should it start to give problems again. Thank you for your suggestion.

---

### Post by pabloab7772 on 2014-12-18
[SIZE=2][FONT=arial]I solved with a workaround: Go to chrome://flags/#enable-gpu-rasterization and disable it. [/FONT][/SIZE][INDENT]
[COLOR=#000000][FONT=Ubuntu]**Disable WebGL**[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu] [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu]Mac, Windows, Linux, Chrome OS, Android[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu][/FONT][/COLOR][/INDENT]
[COLOR=#000000][FONT=Ubuntu][INDENT]Enabling this option prevents web applications from accessing the WebGL API. [#disable-webgl]("chrome://flags/#disable-webgl")[/FONT][/COLOR][/INDENT]
[COLOR=#000000][FONT=Ubuntu]
[SIZE=2][FONT=arial]Then restart Chromium.[/FONT][/SIZE][/FONT][/COLOR]

---

### Post by Paddy Landau on 2014-12-19
> **pabloab7772 said:**
> [SIZE=2][FONT=arial]I solved with a workaround: Go to chrome://flags/#enable-gpu-rasterization and disable it.[/FONT][/SIZE]
Thanks, but…
```
Sorry, this experiment is not available on your platform.
```
The solution is to use Lite Mode. Google Maps is supposed to work that out automatically, and it does (now) — except when clicking a link from a website (e.g. Gmail). I cannot find an answer to the last one.

---

### Post by vasa1 on 2014-12-19
> **Paddy Landau said:**
> Do you mean the following?
```
chromium-browser --disable-accelerated-compositing
```
I have tried that, and it doesn't work. The manual for [FONT=lucida console]chromium-browser[/FONT] doesn't show that option, so I'm not sure that it is valid anyway.
...
[http://peter.sh/experiments/chromium-command-line-switches/](http://peter.sh/experiments/chromium-command-line-switches/) has a list of current switches (CLI options). I remember reading somewhere that switches come and go. So if a switch worked before but doesn't work now, it's possible it's no longer in use.

---

