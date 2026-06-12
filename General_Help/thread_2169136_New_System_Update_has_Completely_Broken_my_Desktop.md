---
title: "New System Update has Completely Broken my Desktop [With Images]"
date: 2013-08-20
forum: General Help
---

### Post by r-grun on 2013-08-20
Hi everyone, Linux scrub here. I recently switched to Ubuntu 13.04 from Windows, and everything has been going great up to this point; I've received a lot of great help and advice from this community, and haven't had any real, big problems until now.

But today an update I installed through the normal system update tool has completely broken my desktop after the login screen (which displays fine). Normally my desktop looks similar to this: 

[IMG]http://i40.tinypic.com/2h6rfas.png[/IMG]

But after today's update, it looks like this, without the left side bar or the clock bar along the top:

[IMG]http://i39.tinypic.com/3aa8g.png[/IMG]

I can still get into the terminal through keyboard shortcuts and access all my files by going into the folders, but the navigation bars have completely vanished. Additionally, if I open a window there's no bar along the top (where the close and min-max buttons normally are), and trying to drag it around makes my system chug like something else. Is there any way to roll back the update or install and activate another desktop environment through the terminal? or perhaps do an install repair from the Ubuntu install boot disk?

Thanks in advance for all your advice. I really enjoy the OS, and I hope I can get this fixed without too much trouble.

---

### Post by papibe on 2013-08-20
Hi r-grun.

Try opening a terminal by pressing Ctrl+Alt+t, install the unity reset tool:
```
sudo add-apt-repository ppa:amith/ubuntutools
sudo apt-get update
sudo apt-get install unity-reset
```
Then run it:
```
unity-reset
```
Hope it helps. Let us know how it went.
Regards.

---

### Post by r-grun on 2013-08-20
Hi Papibe, thanks for the quick response.

The first two commands seemed to work fine, but "sudo apt-get install unity-reset" came back with an error saying it was "E: unable to locate package unity-reset". Is there another source from where I can get the unity-reset tool?

---

### Post by papibe on 2013-08-20
Sorry to hear that, let's try another approach:

Let's try to reset Unity the hard way:
[LIST]
[*]Clean your compiz pre-recorded settings:
```
rm  -rf  ~/compiz  ~/.config/compiz-1
```
[*]install ccm
```
sudo apt-get install compizconfig-settings-manager
```
[*]Then run it like this:
```
ccsm
```
[*]Search for Unity plugin, and make sure it is enabled.
[*]Close ccm.
Run this
```
unity --reset & disown
```
Let it run for a couple of minutes.
[*]If you don't get your desktop back, reboot:
```
sudo reboot
```
[/LIST]
Let us know how it goes.
Regards.

---

### Post by r-grun on 2013-08-20
Hello again,

I did everything you said, and got a window that looked like this, in which I rechecked everything that was unchecked (unity plugin was unchecked):

[IMG]http://i40.tinypic.com/10nb7fr.png[/IMG]

But when I get to the command "unity --reset & disown" the console fires back "ERROR: the reset option is now deprecated" and nothing seems to happen. After a reboot, nothing has changed, though when I go back into the ccsm thingy everything is still checked as I left it. Is there a different command for reset & disown?

---

### Post by papibe on 2013-08-20
Try this:
```
dconf reset -f /org/compiz/ 

unity --reset-icons &disown

sudo reboot
```
Regards.

---

### Post by r-grun on 2013-08-20
Ugh, I'm sorry for being such a bother to help, but I'm still getting strange errors I barely understand. If it would make things easier, is there just a way to completely reinstall Unity and Gnome?

But anyway, when I do the "donf" command I get this:

"error: Error spawning command line `dbus-launch --autolaunch=aa17fe14... (hexadecimal jumbles) --binary-syntax --close-stderr`: child precess exited with code 1"

And when I try the second command I get a terrifying, full-screen readout with a lot of "Fatal"s and which ends in "compiz (opengl) - Fatal: glxQueryExtensionsString is NULL for screen 0"

When I press enter it brings me back to the command line and nothing has changed.

---

### Post by papibe on 2013-08-20
Did you reboot?

If you still don't have your desktop back, you may try this:
```
sudo apt-get install --reinstall ubuntu-desktop
```
Then restart.

Let us know how it went.
Regards.

---

### Post by r-grun on 2013-08-20
Yes, I've been rebooting every single time you've asked me to.

I reinstalled the ubuntu desktop and again nothing happened, I have no idea why the normal system update would break my desktop like this. If I were to reinstall the OS from my boot disc I originally used to install it, do you think it would fix anything? what if I used a different version than 13.04?

---

### Post by VMC on 2013-08-20
You could try creating a new user and see if that boots up normal.

---

### Post by r-grun on 2013-08-20
> **VMC said:**
> You could try creating a new user and see if that boots up normal.

I did that; same result as on my other account: desktop icons but no Ubuntu desktop at all.

---

### Post by r_avital on 2013-08-20
r-grun,

When you log in, there's a dark-ish rectangle on the left side, with your user-name, and box below it to enter your password.  In that rectangle, top-right corner, is there a circle, or a logo of any kind?

If there is, that's a button.  Could you click it, and tell us what you get?  Unfortunately, I don't know if there is even a way to do a screenshot of that, so a detailed description would be helpful.  IF there is such a circle/logo to begin with.

---

