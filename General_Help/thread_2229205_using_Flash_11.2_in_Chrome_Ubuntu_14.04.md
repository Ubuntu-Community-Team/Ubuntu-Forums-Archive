---
title: "using Flash 11.2 in Chrome Ubuntu 14.04"
date: 2014-06-11
forum: General Help
---

### Post by eival on 2014-06-11
i used nautilus to drag the .so file to opt/google/chrome/ and put a copy everywhere including creating an actual Plugins folder

none of which showed up when i restarted

this is for the ACTUAL chrome installed, not the chrominium in the packages

i did this before back in Ubuntu 10 but cant find the thread or any others talking about it

---

### Post by monkeybrain20122 on 2014-06-11
Chrome has dropped support for NPAPI plugins, that include mozilla-flashplugin. Since Chrome comes with up to date flash why do you want to do that?

---

### Post by eival on 2014-06-11
thats not what im asking, i know theres a backdoor way to put the .so file into one of the system folders and have it show up in the chrome://plugins, doesnt matter that adobe isnt still using it.

if its a matter of a specific chrome version not working with that backdoor anymore, than which version did so i can install that one

---

### Post by monkeybrain20122 on 2014-06-11
If you install adobe-flashplugin the normal way through the Software Center it would show up in chrome://plugins for Chrome <= 34. There was no need for any 'backdoor". But Chrome 35 no longer supporta NPAPI plugins so there is nothing you can do.

Like I said, Chrome already comes bundled with up to date (pepper) flash so I am not sure what you are trying to achieve (The "backdoor" you are speaking of is probably for installing pepper flash in Chromium)

---

### Post by eival on 2014-06-12
> **monkeybrain20122 said:**
> If you install adobe-flashplugin the normal way through the Software Center it would show up in chrome://plugins for Chrome <= 34. There was no need for any 'backdoor". But Chrome 35 no longer supporta NPAPI plugins so there is nothing you can do.

Like I said, Chrome already comes bundled with up to date (pepper) flash so I am not sure what you are trying to achieve (The "backdoor" you are speaking of is probably for installing pepper flash in Chromium)


[http://ubuntuforums.org/showthread.php?t=2144347&p=12811464](http://ubuntuforums.org/showthread.php?t=2144347&p=12811464)

---

### Post by monkeybrain20122 on 2014-06-13
The link does not contradict what I told you. You can't install flash 11.2 on Chrome/Chromium any more because google has pulled the plug (and before version 35 you didn't need to install with any 'back door' way, chrome://plugins would show two versions of flash, you only needed to disable pepper flash to use hal)

Now unfortunately there is no way to access drmed flash streams from Chrome/Chromium. In Firefox you can either install hal or use pipelight flash. [http://pipelight.net/cms/installation.html](http://pipelight.net/cms/installation.html)

---

### Post by eival on 2014-06-14
> **monkeybrain20122 said:**
> The link does not contradict what I told you. You can't install flash 11.2 on Chrome/Chromium any more because google has pulled the plug (and before version 35 you didn't need to install with any 'back door' way, chrome://plugins would show two versions of flash, you only needed to disable pepper flash to use hal)

Now unfortunately there is no way to access drmed flash streams from Chrome/Chromium. In Firefox you can either install hal or use pipelight flash. [http://pipelight.net/cms/installation.html](http://pipelight.net/cms/installation.html)

awesome, pipelight works perfectly

will it keep updating the windows version of flash with my normal system updates?

---

### Post by monkeybrain20122 on 2014-06-14
> **eival said:**
> awesome, pipelight works perfectly

will it keep updating the windows version of flash with my normal system updates?

Yes.

---

