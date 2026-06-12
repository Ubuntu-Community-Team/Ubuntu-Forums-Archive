---
title: "Ubuntu 12.04 GUI won't load"
date: 2013-09-18
forum: General Help
---

### Post by AdeJczr on 2013-09-18
How do I get it working again? When I select Ubuntu from the grub menu, I get the purple splash screen with the white loading dots like normal. After a while I get a black screen with what looks like diagnostic text on it. It reads 
"* Starting tor daemon...          [OK]
  (something about a service called saned disabled)
 * Checking battery state...      [OK]"

A picture of the screen is attached. I've done the sudo startx /usr/bin/unity thing to get access to my desktop, if that helps anything.

---

### Post by AdeJczr on 2013-09-18
I have an nvidia graphics card if that helps. I'm not sure what other info I should supply

---

### Post by Yellow Pasque on 2013-09-18
So what did you do the last time you ran the computer to cause this? Did you do anything with video drivers?

> "* Starting tor daemon... [OK]
(something about a service called saned disabled)
* Checking battery state... [OK]"

Those are all standard messages that you usually don't see becauseX/lightdm has fired up by that time.

---

### Post by Dennis N on 2013-09-18
This has happened to others. For suggestions, see:

[http://askubuntu.com/questions/205695/12-04-hangs-at-checking-battery-state](http://askubuntu.com/questions/205695/12-04-hangs-at-checking-battery-state)

and Google "Ubuntu 12.04 boot stuck on checking battery state" for more.

---

### Post by AdeJczr on 2013-09-20
Thanks for the responses. After chasing through the thread above^, I am still having issues. After freeing up some HD space (I now have 650+ MB free), updating/upgrading my apt-get, fixing the dependencies, verifying that default-display-manager points to lightdm, reconfiguring lightdm, and verifying that ubuntu-desktop is installed and up to date, I now get a login screen! YAY! However, when I press enter to login, the screen goes black, I get a quick flash of the "Checking Battery State"-style screen, and am then taken back to the login screen. It's progress in my book, but its still not fixed. Any suggestions? Also, I have not made any changes to my video drivers.

---

### Post by Yellow Pasque on 2013-09-20
So after you try to log in and get thrown back to the login screen, press Ctrl+alt+F1 to get to a terminal.
Some things to try:
- Get the /var/log/Xorg.0.log and find a way to pastebin it (save to USB stick if must)
- Create a new user, run 'sudo lightdm restart' and try to log in as new user.

---

