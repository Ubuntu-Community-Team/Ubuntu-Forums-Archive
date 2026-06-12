---
title: "Mysterious lockup"
date: 2007-12-27
forum: General Help
---

### Post by charliehubuntu on 2007-12-27
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/178915](https://bugs.launchpad.net/ubuntu/+bug/178915) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				This problem started when I went from Feisty to Gusty on an Sony Vaio VGN-AR170p with Intel 3945 wireless, using nm-applet.

System runs fine for some number of hours. Then a dialog pops up asking me for my WEP key. That's unusual because the keyring usually takes care of the WEP key. After that happens, things start crumbling. I can't make any wireless connections. I can't launch some applications: e.g. can't start a new gnome-terminal (opened gnome-terminals keep working), can't start some other apps, can start others. nm-applet menus respond to commands (e.g., I can select different radio buttons for wireless network, but the applet icon doesn't change, and when I re-open nm-applet menu, the original radio button is still selected).  

Then after a while the whole system stops responding to commands. The mouse cursor can be moved, but no mouse clicks do anything, and no keystrokes do anything. I cannot ctrl-alt-F? to get a terminal window. Power button does not respond. All I can do is force power off.

Then I bought a Dell Vostro 1700 with Intel 3945 card and installed Gusty. The same bug appears on the Dell, exact same sequence of failure.

I configured the wireless interface via network-admin, so that it's not handled by nm-applet. The lockup isn't as frequent, and I don't get the WEP key dialog, but the system still slowly crumbles, starting with network failure and ending with no response to keyboard/mouse.

There's a big thread [http://ubuntuforums.org/showthread.php?t=585983]("http://ubuntuforums.org/showthread.php?t=585983") which I believe is mostly about this bug. Mine seems not to be about hardware or dust because it's on two different machines, one brand new.

---

