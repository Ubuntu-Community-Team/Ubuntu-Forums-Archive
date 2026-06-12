---
title: "Software sources for chrome failure"
date: 2016-03-05
forum: General Help
---

### Post by pfeiffep on 2016-03-05
Software updater just failed on my installation due to ```
[dl.google.com/linux/chrome/deb/stable]("http://dl.google.com/linux/chrome/deb/stable") main
``` After removing it software updater worked perfectly. I would like to keep Chrome (version 49 / 64bit) around in the off chance I need it. FWIW I also have Chromium browser installed (version 48 / 64bit) and there's no other software entry in the sources listing for chromium

I tried changing the source to ```
[dl.google.com/google-chrome-stable_current_amd64.deb]("http://dl.google.com/google-chrome-stable_current_amd64.deb")
```
 which also failed.

This is not critical to me since I use FireFox almost exclusively.

How do I determine the correct software source for Chrome?

TIA


[COLOR=#303942][FONT=Ubuntu]
[/FONT][/COLOR]

---

### Post by Bashing-om on 2016-03-05
pfeiffep; Uh Huh ...

Goggle has dropped support for 32 bits . That requires us to tell google's server we want only 64 bit code.

I had to edit 2 files to make that happen:
1) /etc/apt/sources.list.d/google-chrome.list :
to be:
```

deb [arch=amd64] http://dl.google.com/linux/chrome/deb/

```
adding the field " [arch=amd64] "

2) and make the same changes in the file " /opt/google/chrome/cron/google-chrome " ( search on http: )
as this script also generates the .list file .

[INDENT][INDENT]just what I did
[/INDENT][/INDENT]

---

### Post by pfeiffep on 2016-03-05
Thanks for your response.

I think I misunderstood EXACTLY what to do

The first file you mentioned doesn't appear to be directly changed ... ```
cat  /etc/apt/sources.list.d/google-chrome.list
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/chrome/deb stable main
```

the section of the 2nd file now ```
# sources.list setting for google-chrome updates.
REPOCONFIG="deb [arch=amd64] http://dl.google.com/linux/chrome/deb/"
SSLREPOCONFIG="deb https://dl.google.com/linux/chrome/deb/ stable main"
```

Problem remains unchanged.```
W:Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/Release  Unable to find expected entry 'main/binary-i386/Packages' in Release file (Wrong sources.list entry or malformed file)
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```

When is the first file automatically configured?
What step(s) did I screw up?

---

### Post by Bashing-om on 2016-03-05
pfeiffep; Hey ... 

It took me a while to blunder through this also .

If you make the edit to /etc/apt/sources.list.d/google-chrome.list and reboot, you will find that scripts within the file " /opt/google/chrome/cron/google-chrome " will regenerate the source file to the old default.

So in addition to the edit to /etc/apt/sources.list.d/google-chrome.list,
one makes the same edit to /opt/google/chrome/cron/google-chrome.
In my install this is lines 24 and 25, to be:
```

 REPOCONFIG="deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main"
SSLREPOCONFIG="deb [arch=amd64] https://dl.google.com/linux/chrome/deb/ stable main"

```

it is always best practice to make a backup of any file one is to edit . Never can tell what might perchance, loss of power can hurt real bad. A slip of the fingers or a miss thought ... ouch .

once the edits are made .. reboot the system and run:
```

sudo apt update
sudo apt upgrade

```
and welcome to version 49 of google-chrome .

[INDENT][INDENT]hope this further helps
[/INDENT][/INDENT]

---

### Post by pfeiffep on 2016-03-05
Thanks!
The salient point for me was to reboot to initiate the sources to be re-generated...

---

### Post by Bashing-om on 2016-03-05
pfeiffep; Hey ...

You do good work .

[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]together we can
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

