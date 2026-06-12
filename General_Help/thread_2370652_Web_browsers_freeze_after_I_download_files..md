---
title: "Web browsers freeze after I download files."
date: 2017-09-05
forum: General Help
---

### Post by r9-93r on 2017-09-05
[COLOR=#333333][FONT=monospace]I'm using ubuntu 14.04 with a Lubuntu enviroment desktop. I had the same problem with the Pantheon Desktop.
Everytime I download something my browser freezes, and yes I have the stable version of chrome and firefox.
Also my machine sometimes gets slower I dunno why.[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]Also Can you help me install dolphin emulator with super smash bros melee?[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]Thanks.[/FONT][/COLOR]

---

### Post by vasa1 on 2017-09-05
If you wish, install *inxi*, then run ```
inxi -Fxzc0
```in a terminal and post the output here so we know a little about your system.

---

### Post by BenginM on 2017-09-06
Hiya, How are you downloading files, are you using the native browser downloader or with a downloader extension? Is the broswers crashing, or hanging! if you have other browser extensions disable them , then run either browser in terminal and download files using the native downloader, (Do not use a downloader extension).  look at the logs $ copy them if you can before a freeze occur , and Do you still get the same behavior ?!

Are these small or big files ?  are you able to download files without issue using wget file?

Also, while you at it .. check the CPU usages ratio using system monitor or top. Does that behavior occur under a high CPU usage while downloading in the browser ?

---

