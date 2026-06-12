---
title: "Key beeps instead of making letter appear in console"
date: 2005-04-21
forum: General Help
---

### Post by enricod on 2005-04-21
Greetings, ubuntu community :)

Since this morning, I have had a strange problem: whenever I go to a console and i press the "D" key, i hear a beep and no "d" appears in the command line. For example, if I try to type "sudo", "suo" appears and I hear a beep. This happens not only in the gnome terminal but also in a ctrl-alt-F* terminal. This problem appears only after I logged in; I am able to type my username, which contains a D, in the login promt.

By the way, how do you disable those annoying beeps without recompiling the kernel?  I remember I found some time ago a command that was something like "# /dev/null > /dev/<something>", but I can't find it again in google. I can't unplug the pc speaker since I have a laptop.

Cheers, 

Enrico

---

### Post by Sam on 2005-04-21
Hi! Welcome on the Ubuntu forum.


You can disable the terminal beeps from your terminal profile (Edit menu, Current Profile, uncheck Terminal Bell).

Or for the ttys:
$ setterm -blength 0



For the "D" letter problem, maybe you mapped the key as a shortcut in the System, Preferences, Keyboard Shortcuts. I did that once and I had a similar problem.

---

### Post by enricod on 2005-04-21
Thanks, no more nasty looks directed at my in libraries now :D
but the "D" problem persists :( , D wasn't mapped as a shortcut in preferences>keyboard shortcuts. The issue is present only in a console. In Firefox, for example, I'm perfectly able to use Ds, as I am doing now.

---

