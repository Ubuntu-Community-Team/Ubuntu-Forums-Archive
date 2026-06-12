---
title: "can't run software update"
date: 2015-09-20
forum: General Help
---

### Post by Saffo on 2015-09-20
hello!

i am having trouble running software update. when i do, it shows me, like normal, the list of software that needs to be updated. but then when i choose install, after i enter my password, it shows me this 

[ATTACH=CONFIG]264543[/ATTACH]

if i click "ok" it just stops and if i click settings it opens the settings window but it doesn't tell me what to do. i have no idea what packages or what sources it is talking about.

also i am new to ubuntu so if you wouldn't mind explaining without using too much jargon that would be wonderful.

thanks!

---

### Post by JKyleOKC on 2015-09-20
To help assure that the software you download with the updater has not been modified to include malware, each server has its own encoded signature, and the updating software verifies that encoded signature each time you download anything.

The error message you're getting indicates that for some reason, that signature verification did not succeed for one or more of the sources indicated in your settings window. It's deliberately vague, so as not to give information to a possible malware distributor attempting to subvert your system -- and it's maddening to those of us who need to find out what went wrong. The most usual cause of the message is that you simply do not have an official copy of the signature in your system, but that's not always the case.

If you have added any source to the list in your settings window, try removing the check-mark by that source and run the "check" again to see if that was the offending source.

If not, or if it made no difference, we'll need to see the content of your /etc/apt/sources.lst file to try to determine what you should do next. I'm using Xubuntu 14.04.3 so someone else will need to tell you how to post that content here from your system, unfortunately.

---

### Post by oldos2er on 2015-09-20
Please run ```
sudo apt-get update
``` in a terminal and copy/paste the output here so we can see which key is missing.

---

