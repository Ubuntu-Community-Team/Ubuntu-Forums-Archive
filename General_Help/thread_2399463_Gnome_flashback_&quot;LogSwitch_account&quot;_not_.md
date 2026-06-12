---
title: "Gnome flashback &quot;Log/Switch account&quot; not working on 18.04.1"
date: 2018-08-25
forum: General Help
---

### Post by MgFrobozz on 2018-08-25
I installed 18.04.1 LTS and (as I've done for 14.04 and 16.04) added gnome flashback, by using "sudo apt-get install gnome-panel gnome-tweak-tool", logging out, and then selecting gnome-flashback as my session manager.

This worked almost as well as with 14.04 and 16.04, but if I select "Log/Switch account", it takes me to the login screen for my account (a dialog for the password only). Clicking on the "Switch User" button produces a long pause, followed by a black screen. If I click on the black screen, I'm batch to the password-only dialog.

If I log out, then I get the switch-user screen (allowing login by any user), but of course my session disappears.

I found this question on the same subject ...
[https://askubuntu.com/questions/1044779/unable-to-switch-users-at-lock-screen-unity-ubuntu-18-04](https://askubuntu.com/questions/1044779/unable-to-switch-users-at-lock-screen-unity-ubuntu-18-04)
... but the suggested cure (remove and reinstall lightdm) doesn't work because lightdm isn't installed.

Thanks in advance for any hints.

---

### Post by MgFrobozz on 2018-08-25
It turns out that [https://askubuntu.com/questions/1044779/unable-to-switch-users-at-lock-screen-unity-ubuntu-18-04](https://askubuntu.com/questions/1044779/unable-to-switch-users-at-lock-screen-unity-ubuntu-18-04) works if I skip the "apt-remove lightdm" step (18.04.1 uses gdm3 instead of lightdm), and instead use "apt-get install lightdm" and change the default manager to lightdm, then reboot.

gdm3 doesn't seem to support gnome flashback in the same way.

---

### Post by MgFrobozz on 2018-09-22
This is still not working quite right. Anytime someone selects "Log/Switch Account", it goes to the unlock (screen saver) interface ok, but then in order for a different user to return to their session, then need to (1) select "Switch User", then (2) select their own account and enter their password, and then (3) after their screen saver appears, and then the screen goes dark, wiggle the mouse to wake it up again and then (4) enter their password again.

In order to figure out what's going on, I need to figure out what software is running the lock screen (with the "Log/Switch Account button) and the login screen (with an entry for each user). Anyone know what packages do this, and what the executables are called?

---

### Post by MgFrobozz on 2018-10-03
I found I needed to remove gnome screensaver for this to work ...
[FONT=Arial]sudo apt-get remove gnome-screensaver
... and it's very important to shut down from within the session, rather than using "Lock/Switch Account" after you do this, because it pops up a screen with no controls, which requires a cold boot to recover.

It's still not quite right, because "Lock/Switch Account" does nothing after rebooting, and in order to suspend a session, you must switch to another users's name in the power menu. I'm assuming there's no way to suspend if there's only one user registered.




[/FONT]

---

### Post by Claus7 on 2018-10-04
Hello,

just a couple of questions first: 
i) do you try this from indicator-session of gnome panel? 
ii) if yes, then the option offered is: "Lock/Switch Account" along with a keyboard shortcut?
iii) do you have cairo-dock installed as well?
iv) do you have any other sessions installed as well? There might be some conflicts among sessions.
v) have you tried re-installing the indicator-session from synaptic?
vi) using the command: less /etc/X11/default-display-manager
which is the display manager used? 
vii) also, if indicator-session is the one you are using, have you enabled from dconf to display the list of users as well?

EDIT: My shortcut is Super+L: if pressed it works and I can switch user, yet if I click on it it does nothing.
In order to switch user, it brings me back to the login screen where I can choose the user I want.

Regards!

---

