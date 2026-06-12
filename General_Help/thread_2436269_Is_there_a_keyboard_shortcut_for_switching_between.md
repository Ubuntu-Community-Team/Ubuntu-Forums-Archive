---
title: "Is there a keyboard shortcut for switching between monitors?"
date: 2020-02-03
forum: General Help
---

### Post by shirs on 2020-02-03
Hi,

I currently use Ubuntu 18.04.3 with two monitors.
Switching between the monitors with the mouse takes time when done occasionally.

My question is:
Is there a keyboard shortcut for this operation?
I know that Alt+Tab is for switching between windows (located in the same monitor)
and I was wondering if there exists the same thing for switching between screens.

Thanks!

i.e. if this question is not suitable for this forum please let me know if there is any other forum which it is suitable for (maybe new to ubuntu forum?) .. thanx

---

### Post by mastablasta on 2020-02-03
in Kubuntu i think it's Win Key(Super) +P 

usefull shortcuts:
[https://help.ubuntu.com/stable/ubuntu-help/shell-keyboard-shortcuts.html.en](https://help.ubuntu.com/stable/ubuntu-help/shell-keyboard-shortcuts.html.en)

also in linux you can make your own shortcuts.
[https://help.ubuntu.com/stable/ubuntu-help/keyboard-shortcuts-set.html.en](https://help.ubuntu.com/stable/ubuntu-help/keyboard-shortcuts-set.html.en)

---

### Post by kwan-e on 2020-02-03
You might be able to do this with the xautomation package.  First, install xautomation:
sudo apt install xautomation

Next, define a key shortcut:
1. Go to Keyboard Settings
2. Scroll to the bottom and click the + key to add a new shortcut
3. Name the shortcut something like "Move to top"
4. For the command:  xte 'mousemove 1 1'
5. Set a shortcut key. For example, Ctl-Shift-T

You might need to play around with the mousemove command to place the mouse where you want it.

---

