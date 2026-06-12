---
title: "Firefox, Thunderbird slow to launch file dialogue"
date: 2021-03-11
forum: General Help
---

### Post by SeijiSensei on 2021-03-11
The most recent updates to Firefox and Thunderbird suddenly take forever to bring up the file selection dialogue on my Kubuntu machine. The dialogue would pop right up on earlier versions, but now takes up to a minute to appear.  Has anyone else seen this behavior?  If not, are you using Kubuntu 20+?

---

### Post by TheFu on 2021-03-11
In short, sorta - me too.  I don't have a good solution.

I have an issue with Thunderbird where any menu, anywhere in the program takes 10+ seconds to be displayed.  I'm running thunderbird over an ssh -X tunnel on a different machine. It is only menus.  Changing the message in the reading pane is fast, just like running local.

The remote 20.04 system is in a different LAN segment than where I work normally. Only ssh is allowed between them. I'm not using any DE at the time of these issues.  All DEs make things slower than I like, though not really slow on the local machine.  The 20.04 VM has Mate as the DE installed, but that was too slow/painful to be used - like 90 seconds to display windows even when running full screen with QXL and Spice. Using other methods was much worse.  I do run thunderbird inside a firejail too.

As for firefox, it was slow too and nearly impossible to use over the ssh -X connection. That method had been working for years. Oddly, using non-Snap chromium browser with firejail over the ssh -X works fine.  It is definitely something about the Mozilla cross-platform libraries, that is certain.
If I run firefox like this: **firejail --ignore=seccomp --ignore=protocol firefox -no-remote** it is fast, but I have to modify the LAN firewall, which isn't really desirable.

On a laptop, running everything local, inside firejails, FF and thunderbird are fast. But this is an 18.04 machine.

---

### Post by VMC on 2021-03-11
I don't use Thunderbird, but Firefox comes up as fast as it ever did, on my 21.04 testing Kubuntu.
```
[FONT=monospace][COLOR=#000000]Mozilla Firefox 86.0 20210222142601 20210222142601
```[/COLOR]
[/FONT]

---

### Post by SeijiSensei on 2021-03-11
> **VMC said:**
> I don't use Thunderbird, but Firefox comes up as fast as it ever did, on my 21.04 testing Kubuntu.
Yes, they are not slow to launch, but for me they are slow when saving a web page or an email attachment. Anything that brings up the file save dialog.

---

### Post by VMC on 2021-03-12
I just saved this page from FF browser. It brought up Library and then saved page instantly  Not sure about file/save dialog. That didn't appear. Just Library save.

---

