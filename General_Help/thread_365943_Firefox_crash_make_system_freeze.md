---
title: "Firefox crash make system freeze"
date: 2007-02-20
forum: General Help
---

### Post by el_itur on 2007-02-20
Hi all:

Lately I've encountered an annoying issue with firefox. In the past few days it has been crashing a lot (wich is not new in edgy), but whenever it crashes makes my whole system freeze. I have to go to getty and kill firefox becouse the whole gnome is freezed.

Do you know how I can backtrace it to fill a bug report?.
Do you have the same issue?.

Thanks for your feedback.

---

### Post by energiya on 2007-02-20
You could try opening firefox from a terminal, and when it freezes, just go to a tty and kill firefox-bin. The terminal should still be openend and show any errors. Also I think the system freezes because of 100% CPU usage from firefox (in tty it will appear in top or I recommand htop, a much better version).

 It happened to my a few times and switched to Swiftfox and the problem seemed to disappear, but others appeared. I'm now using Zenwalk and no problems, so it might be Ubuntu related.

---

### Post by el_itur on 2007-02-20
Thanks for your advice. Will try that later.
Its is shourely realted to ubuntu since we took it broken from debian

---

### Post by el_itur on 2007-02-21
Ummm, tried that and the terminal coundn't retain any debug data. In fact when I lunch firefox from terminal it shows me the bash again. I can close the terminal and firefox still runs, unlike any other app.

Any other suggestion to backtrace the problem?

---

### Post by energiya on 2007-02-21
Found [this]("http://www.redhat.com/archives/fedora-devel-list/2006-June/msg00211.html") on debuging firefox. But I think it should be compiled with debug activated (?).

And try searching for this bug on [http://www.debian.org/Bugs/]("http://www.debian.org/Bugs/") .

---

