---
title: "MUSESCORE: how to get the repository updated? And, more"
date: 2023-08-30
forum: General Help
---

### Post by Old Jimma on 2023-08-30
Hello Ubuntuers:

Musescore is a music notation program for Windows, macOS, and Linux ([HTML] https://en.wikipedia.org/wiki/MuseScore[/HTML]).

Currently, the version of musescore available in the Ubuntu repository is 3.2 and became available in 2021.

Since then, there have been many improvements and fixes that have resulted in two important releases:
[LIST]
[*]Musescore 3.6, and
[*]Musescore 4.
[*]
[/LIST]

Musescore users who seek advice on the Musescore forum ([HTML]https://musescore.org/en/forum[/HTML]) are recommended to upgrade to either of those two more recent releases... depending on their needs.

Many important improvements have been made to Musescore.

Neither of these versions are not available in the Ubuntu repositories.

My first question is:
**What's the process for making the new Musescore releases available in the repository?**

Using the new releases is important for Raspberry Pi users, also, who use Ubuntu as their operating system.

So, my second question is:
**What is the process to getting Musescore 3.6 and Musescore 4 available for in the Ubuntu repository.... that work on a pi with that arm processor?**

Thank you!
Old Jimma from the Old Country

---

### Post by maglin2 on 2023-08-30
3.6.2 is available as a snap.

---

### Post by Old Jimma on 2023-08-30
Thanks.

Is it true that snaps do not get updated??

---

### Post by ajgreeny on 2023-08-30
No, that is very untrue, in fact snaps generally upgrade without you having much control over when they do it.

The details of exactly how snaps work is something that I can't help you with as I do not use any and have totally removed the snap infrastructure from all my machines.
 
However as well as a snap you can also download Musescore as an Appimage which is what I have. Currently on my machine is version **MuseScore-4.1.1.232071203-x86_64.AppImage** which you can download from [https://musescore.org/en/download/musescore-x86_64.AppImage](https://musescore.org/en/download/musescore-x86_64.AppImage).  Make the Appimage file executable and double click it to start the application.  You can create a launcher for it if you wish, which you can add to your menu system.

---

### Post by ian-weisser on 2023-08-30
Musescore upstream migrated away from debs, dallied with snaps, and is now distributing using AppImage.
There are no longer updated Debian packages nor updated snaps coming from Musescore upstream.
For all the gossip and details, see [https://github.com/musescore/MuseScore/issues/15994](https://github.com/musescore/MuseScore/issues/15994)

Both debs and snaps can be packaged by volunteers (not Musescore upstream), but there currently seem no volunteers willing to do that work.
No Debian volunteer has touched it in a few years. If anyone is interested, that's the place to begin.

---

### Post by #&amp;thj^% on 2023-08-30
Also for another option:
```
flatpak search musescore
Name   Description                    Application ID      Version Branch Remotes
MuseS&#8230; Create, play and print beauti&#8230; &#8230;usescore.MuseScore 4.1.1   stable flathub

```

---

