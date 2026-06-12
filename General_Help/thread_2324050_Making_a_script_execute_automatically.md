---
title: "Making a script execute automatically?"
date: 2016-05-10
forum: General Help
---

### Post by psfal on 2016-05-10
Ubuntu 14.04
DE Gnome 2.0 via [https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks) which has worked perfectly since 12.04 with some minor tweaking for 14.04

So I've written this script into an "adduser.local" file to move my window controls to the right in new accounts, but I have to type in "adduser.local" from terminal in the new account for it to work.

[COLOR=#000000]#!/bin/bash[/COLOR]
[COLOR=#000000]#min max close[/COLOR]
[COLOR=#000000]gsettings set org.gnome.desktop.wm.preferences button-layout ':minimize,maximize,close'

I did [/COLOR][COLOR=#000000]"sudo chmod 755 /usr/local/sbin/adduser.local"

How do I make this execute automatically when I create a new account from my admin account in settings? Do I have to point it out in an existing config file? My understanding of the Adduser man page is that if adduser.local exists it will be run on new accounts on the first login.

How do I make this work without having to log into the new account and manually run it?[/COLOR]

---

