---
title: "gnome-settings-daemon problems after update"
date: 2007-04-11
forum: General Help
---

### Post by dryder on 2007-04-11
Hi,
I too have a gnome-settings-daemon problem that has just started (yesterday) after an update.

The warning box says:
"An error occurred while loading or saving configuration information for gnome-settings-daemon. Some of your configuration settings may not work properly."
The details are:
Bad key or directory name: "/desktop/gnome/peripherals/keyboard/host-server-ubuntu.dryder.org server-ubuntu/0/numlock_on": ` ' is an invalid character in key/directory names
Bad key or directory name: "/desktop/gnome/peripherals/keyboard/host-server-ubuntu.dryder.org server-ubuntu/0/numlock_on": ` ' is an invalid character in key/directory names

This come up every time I press Numlock (I have that so Numlock is on when Ubuntu starts),  Shift or Caps Lock which I have always had set in Keyboard-Accessibility with Enable Sticky Keys-Beep when modifier is pressed and Enable Toggle Keys.

For a while before this error above I was experiencing these features just being turned off by an unknown cause - but not because of any settings in Keyboard Accessibility to turn them off.

Can anybody help please as I do not know even where the file is to repair (the error message might have told me that! :-(  )

Many thanks,
David

---

### Post by crapapelada on 2007-06-08
I have the same problem.
Any help would be appreciated.
:D

---

### Post by jthompson on 2007-07-02
Go to:

System --> Administration --> Network.  Click on the General tab and give your computer a host name and domain name.  Just make up a domain name if you don't have one.  Then Reboot.  The problem will go away. 

That fixed it for me anyway.

---

### Post by crapapelada on 2007-07-03
I had to reinstall everything due to a HD failure, but if the problem should come out again I will try this.
Thanks a lot!

---

