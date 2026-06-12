---
title: "Firefox and Chromium don't work, Chrome keeps crashing"
date: 2013-11-05
forum: General Help
---

### Post by d-wall08 on 2013-11-05
google chrome keeps crashing, every now and then. foxfire and chromium wont work, got chrome, works yet it crashes every now and then. Whats to do?

---

### Post by Toz on 2013-11-05
*Renamed thread to be more descriptive of the problem and moved to **General Help***.

---

### Post by sanderj on 2013-11-05
> **d-wall08 said:**
> google chrome keeps crashing, every now and then. foxfire and chromium wont work, got chrome, works yet it crashes every now and then. Whats to do?

Open a terminal and type "firefox" and ENTER. Post the output here.

---

### Post by steven.raiss1 on 2013-12-29
[CENTER][B][SIZE=3]_Fix Chrome Crashes " Linux "_[/SIZE]
[/B][/CENTER]
[COLOR=#000000][I]

In the Chrome address bar , type the following command:[/I][/COLOR]

[COLOR=#000000]*1- about*[/COLOR][B]: plugins

[/B]2- Here you are presented with a list of plugins that are installed in your [Chrome]("http://www.net4tech.net/2013/12/google-chrome-keeps-crashing-this-is.html") browser. Consider the existence of not one but two flash plugins :


[IMG]http://cloudhighclub.com/wp-content/uploads/2011/06/Chrome-OS-Crash.jpg[/IMG]
[COLOR=#000000][I]

3- What really happened here is that there is a clash of plugins, as Chrome does not know which plugin to use for Flash applications. We need to disable one of them.[/I][/COLOR]

[COLOR=#000000]*4- Judging by the list, which is installed in the / web directory opt / google / chrome / PepperFlash / libpepflashplayer.so looks like the built in Chrome browser, which interferes with the built in OS Flash plugin. We need to disable one of them , and we should disable that is integrated into the Chrome browser.*[/COLOR]

[COLOR=#000000]*5- Click Disable the plugin that is installed in the / opt / google / chrome / PepperFlash / libpepflashplayer.so directory*[/COLOR]
[COLOR=#000000]*6- Restart your Chrome browser, and everything would return to normal!*[/COLOR]

[COLOR=#000000][I]In summary , the cause of this problem is the new library file that comes with Chrome PepperFlash 20. Google search results sent me in 7720 faced similar problems with users of this plugin.


[/I][/COLOR]

---

