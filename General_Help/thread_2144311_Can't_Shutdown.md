---
title: "Can't Shutdown"
date: 2013-05-11
forum: General Help
---

### Post by Hyper Tails on 2013-05-11
Hey guys, I have Windows 8 Pro and Ubuntu 13.04 Raring Ringtail on my computer.

When I click on the shut down button on my top right-bar, it doesn't shut down; I have to got to terminal and type **sudo poweroff** in order for me to shout down my computer. It's very annoying!

Any help will be thanked.

---

### Post by Hekabe on 2013-05-11
You could write a script like this:
```
#!/bin/bash
sudo init 0 
```
and just place it on your desktop and mark it as executable, then run it to shutdown.

---

### Post by wxnker on 2013-05-11
I had shutdown issues with 13.04, but this solved the problem. It's about shutdown problems and speech-dispatcher.

[http://askubuntu.com/questions/287792/not-been-able-to-shut-down-13-04](http://askubuntu.com/questions/287792/not-been-able-to-shut-down-13-04)
[http://askubuntu.com/questions/293244/problem-with-speech-dispatcher](http://askubuntu.com/questions/293244/problem-with-speech-dispatcher)

---

