---
title: "Server Back To Basics Help"
date: 2007-08-06
forum: General Help
---

### Post by TheSpecs on 2007-08-06
Hello! Sorry if this has been asked before, i tried searching the forum but didn't come up with anything so here it goes....

I have a server in my cupboard with just the normal network cable coming out of it into the router and a power cord. 
I currently use it as a web server and a general mess around toy with Ubuntu command line, learning as i go. Because of this and me messing around with the settings all the time i mess up stuff occasionally and its normally a real pain to fix, and since i use putty over the network, if i mess up the net config on the server it means dragging it out of my cupboard, attaching a screen and keyboard and normally totally re-installing everything, which is really annoying to say the least.

Soooo, my question is... Is it possible to use a command to uninstall and get rid of all the non-essential apps and configuration files leaving just my server intact, clean and ready for me to mess it up and play around again? I don't mind if it gets rid of my apache, mysql, php, python stuff etc, however it would be nice if openSSH was left on there so i could easily get it back.

So masterminds, any ideas? :wink:
Thanks!

---

### Post by BoneKracker on 2007-08-06
Backup and restore.

Or, reinstall from cd (with a keyboard plugged in, you can blindly "/etc/init.d/sshd start").

---

### Post by TheSpecs on 2007-08-06
Ok, ill give it a go, thanks mate! :)

---

