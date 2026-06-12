---
title: "emacspeak"
date: 2014-11-06
forum: General Help
---

### Post by evaristegalois on 2014-11-06
Emacspeak is a screenreader specifically for emacs, but since you can do a lot in emacs it's very helpful for blind users, especially if you do terminal-related work (orca is better for GUIs). 

Installation of emacspeak was surprisingly easy. Open a terminal, type "sudo apt-get install emacspeak", type "none" when prompted for the speech synthesizer, and everything works beautifully. 

But then, when I try to start emacspeak, I hit a big snag. Type "emacspeak" in a terminal. Emacs 24 opens beautifully, and I hear the introductory message, so all is well with the speech synthesizer. 

But then weird things happen to my keyboard. I can type letters, but special characters like "ENTER" or "Alt-x" (M-x for emacs aficionados) just give me a "Back to top level" in the message area and nothing happens. I can't execute any emacs commands or even press ENTER. I tried to run "emacspeak -q" to make sure my emacs config file didn't cause any of this, but the problem persists. If I run emacs without emacspeak everything is fine.

Please help! It should take 15 seconds to reproduce this problem on your computer.

---

