---
title: "[SOLVED] I accidentally uninstalled something important ^_^"
date: 2007-08-19
forum: General Help
---

### Post by darkzim on 2007-08-19
Ok I'm a really big linux newb....

I've had Edgy running on my laptop for several months now, but today i got annoyed with the low battery life, so i decided after reading some tutorial to install laptop-mode and laptop-mode-tools packages.  Then I got frustrated b/c I couldn't figure out how to use it, so i decided to remove the packages.

To my horror upon removing laptop-mode-tools, it started removing all these gnome packages... I stopped the removal, and reinstalled it, so i thought everything was ok, but apparently not.

I restarted my laptop later and found that it brings up the login, but when i log in, it just sorts of sits there, it doesn't bring up that small window where the icons show its loading, etc... 

What do i need to do 2 figure out what to install again? 

Lol, sorry if this is insanely newbish.  

Thanks,
darkzim

---

### Post by aysiu on 2007-08-19
Reinstall the *ubuntu-desktop* package.

---

### Post by darkzim on 2007-08-19
Thanks for the quick reply!

hmm... it didn't seem to help. The loading bar still doesn't come up when i log in, it just sits there with a cursor and an orange screen.

the output was "ubuntu-desktop is already the newest version"

---

### Post by g2g591 on 2007-08-19
try using apt-get install -f that should reinstall any vital thing

---

### Post by davidonabus on 2007-08-19
I just had this EXACT same problem.

See the thread..

[http://ubuntuforums.org/showthread.php?p=3219351#post3219351](http://ubuntuforums.org/showthread.php?p=3219351#post3219351)

apt-get install -f

didn't work for me.

However..

apt-get install gnome

Did fix the problem.

Hope that helps.

david

---

### Post by darkzim on 2007-08-20
Thank you for the help!

sudo apt-get install -f didn't work,tho.
I'm going to go try the "install gnome" option now.

---

### Post by darkzim on 2007-08-20
Well, that didn't seem to work either.  I still have the same problem.

"apt-get install gnome" installed a plethora of related packages. Rebooted, same problem.

"apt-get remove gnome" removed the "gnome" package. Installed gnome again, rebooted, same problem. LOL, I hope I don't have to reformat, that would be bad seeing as how I don't have a cd drive in my laptop.

EDIT: OK, I managed to fix it on my own ^_-.  I loaded up gnome in failsafe mode (mentioned in davidonabus' thread), and it came up with an error "Failed to load settings daemon"... So I googled that and came up with people saying they had fixed that error by editing their /etc/networking/interfaces and /etc/hosts files.... So I looked in /etc/ hosts and viola!  I don't know what it actually does, but there are hose lines 
127.0.0.1  networknamething
127.0.0.1  <----------------------------- But this was "127.0.1.1"... So I changed the one to a zero, rebooted and loaded up normal gnome and everything worked out.

Thanks

---

