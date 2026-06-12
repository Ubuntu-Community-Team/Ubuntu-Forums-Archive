---
title: "Terminal Focus action"
date: 2013-07-01
forum: General Help
---

### Post by kjarli on 2013-07-01
I'm having a very annoying issue. I'm working with 2 screens, left my terminal in a small window and on the right my IDE. I have to copy paste stuff into my terminal to run composer updates (php composer.phar). Because for some silly reason, the terminal doesn't allows ctrl+v (dunno who came up with that idea :confused:) thus I use the middle mouse button.

The problem with the middle mouse button is: Once I've selected something on the right screen in my IDE and I want to focus something in the terminal so I can click and have it on my commandline, it sometimes selects characters/lines in my terminal due to my mouse moving while I click (high dpi). This cancels my selection from the IDE and puts the selected text on the commandline causing me to either execute the wrong command or a new line. I also have to reselect the text etc. This is _really_ annoying.

Is there a way I can prevent the terminal from selecting texts when I focus the window until the moment I press the LMB again?

---

### Post by Impavidus on 2013-07-01
Ctrl-v doesn't paste in a terminal because it has a different meaning (and has probably had since before the clipboard was invented). Use shift-ctrl-v instead.

You can focus on the terminal without selecting any text by clicking on the title bar (if you have any) or by selecting "focus follows mouse" or something similar. How to set these options depends in your DE and should be somewhere in the settings for your window manager.

---

### Post by kjarli on 2013-07-01
Yes, I know of that setting. I dislike that setting, already tried it but couldn't get used to it. Title bar is rather small for a fast DPI mouse, I'll give it a try but I think the shift-ctrl-v will do wonders for me, thanks!

---

