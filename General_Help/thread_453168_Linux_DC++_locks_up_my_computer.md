---
title: "Linux DC++ locks up my computer"
date: 2007-05-24
forum: General Help
---

### Post by Cambrant on 2007-05-24
Hi, I have been using ldcpp for over a year without much trouble, but recently since upgrading my system from Edgy to Feisty I have been experiencing really weird lockups when using Linux DC++ (latest CVS version from 2007-05-06.)

Mostly it happens when I try to close one of the tabs in ldcpp. The computer just hangs and is completely unresponsive. I can move the mouse around, but all clicks are ignored. Switching to console mode by pressing CTRL-ALT-F* or trying to kill X by pressing CTRL-ALT-BACKSPACE doesn't work either. However, if I press the power button on my computer it shuts down as usual and I see the progress bar of usplash.

After rebooting I check my logs but find nothing. It all looks like a normal shutdown. What I'm thinking is that it might have something to do with GTK+ or whatever ldcpp is using. Since the lockups only happen when I use the widgets actively. Not closing any ldcpp tabs can make me run the program flawlessly for hours until another widget locks the computer up.

I hope someone could help me with this annoying problem. I would really appreciate it. Thanks.

---

