---
title: "Monitor change prompt issue in Kubuntu"
date: 2020-04-25
forum: General Help
---

### Post by meetdilip on 2020-04-25
I installed Ubuntu 20.04. Using Synaptic Package manager, I installed Kubuntu Desktop. Everything works fine, but an error. Kubuntu keeps asking about what type of display switch I need. As if I have an external monitor connected to the laptop ( there is none ). The same error was there when I use Kubuntu Live USB. Popup goes away if you click somewhere. But it comes back very soon. 

Is there any way to get rid of it completely ?

[IMG]https://i.stack.imgur.com/5qmEk.jpg[/IMG]

---

### Post by meetdilip on 2020-04-25
System settings > Startup and Shutdown > Background Services > KScreen 2

" Stop " it, but don't remove it from " Background Services ". Because I doubt whether it will show the screen at all when your system starts up the next time. Still on trial and error. I will update this thread if I have any further info.


Got this path from : [https://bbs.archlinux.org/viewtopic.php?id=187998](https://bbs.archlinux.org/viewtopic.php?id=187998)

---

### Post by meetdilip on 2020-04-25
It came back on restart and I had to " Stop " * KScreen 2* again. Now back to normal. I think there should be something in Kubuntu which prevents the popup unless it detects an external monitor.

---

### Post by meetdilip on 2020-04-26
It keeps coming back on each restart. Finally removed KScreen 2 from startup background processes. It is as simple as clicking it again and bringing back to startup if I ever need it.

[IMG]https://i.imgur.com/DNqHDDO.png[/IMG]

[COLOR=unset][/COLOR]
[COLOR=unset][/COLOR][COLOR=unset][/COLOR][COLOR=unset][/COLOR][COLOR=unset][/COLOR]
[COLOR=unset][/COLOR]

---

