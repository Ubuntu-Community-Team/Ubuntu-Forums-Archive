---
title: "Xbindkeys in 18.04, mouse actions not done on first button click"
date: 2018-09-26
forum: General Help
---

### Post by dwsideri on 2018-09-26
My problem is related to button mappings on my mouse, via Xbindkeys, that are not working in a consistent manner. The short version is that using a mapped button action is doing "something else" in the present application when clicked the first time, then actually does the mapped action on the second (or third) click.

Question: is there a way to ensure that Xbindkeys actions are preferred over any programmatic mappings that may exist? Perhaps this is a GNOME shell setting that I'm not familiar with?

Long Version:
1. My .xbindkeysrc includes the following mapping, among others, which uses button #8 to switch the next workspace DOWN:
#Workspace Up via Mouse
"xdotool key --clearmodifiers --delay 2 ctrl+alt+Down"
   b:8
2a. If I am in the Terminal program window, clicking that button will sometimes send "B" to the prompt. If I'm in, say, Gnumeric, it will send me to the last cell at the bottom of the open sheet (row 65536, if you're interested). If I'm in Chrome with Google Sheets open, it sends "Page Down".
2b. Sometimes (I can't spot a pattern), the "Workspace Down" mapping works perfectly on the first click.
3. If the first click didn't send "Workspace Down", a second click usually send it.
4. I get similar results to mappings to button #9 and #10.

It seems like those programs have some intrinsic mouse mappings that are taking preference over Xbindkeys. How do I make Xbindkeys run its mappings first? It's a bit annoying to have to click multiple times and/or get page downs/page ups that I didn't request.

Background: I have a Logitech Performance Mouse MX, with certain actions mapped via my .xbindkeysrc file; I've been using the same combination of mappings all the way back to Ubuntu 12.04. Only with the switch to 18.04 (and GNOME shell with it) does this problem show up.

---

