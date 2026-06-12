---
title: "ubuntu doesn't remove unneeded programs..."
date: 2005-09-15
forum: General Help
---

### Post by kcy29581 on 2005-09-15
Hi all,

I installed gnome-bluetooth today to try it out. It's dependencies were:
libbluetooth1
libbtctl1
libgnomebt0
libopenobex-1.0-0
python2.4-libbtctl

I later decided to remove gnome-bluetooth, but Synaptic only removed gnome-bluetooth, so now I have 5 packages which are unneeded (I didn't need them before installing gnome-bluetooth, thats why they are unneeded).

Is there a way for Synaptic to clean Ubuntu from such packages? If someone installs/uninstalls all the time, they might end up with many packages for nothing!

ANd I bet there's an easy solution to this which I'm missing...

---

### Post by Caboto on 2005-09-16
Synaptic don't remember the dependencies and can't remove them. There's a fairly simple solution.

Check [this How-To](http://ubuntuforums.org/showthread.php?t=53176) for deborphan in synaptic. With that, you can find orphaned (not needed anymore) packages. You could even "sudo apt-get install deborphan" und use the deborphan command in the console to get a list which package aren't needed anymore, but the how-to isn't that difficult and you'll get it integrated in Synaptic.

If you would like the packet manager to remove all dependencies a package installed with it and which aren't needed anymore, try out aptitude. It's a console script, but it's really simple. [Here's](http://ubuntuforums.org/showthread.php?t=37736) a nice how-to for it.

---

### Post by sneax on 2005-09-16
Thanks I was also looking for that  :)

---

### Post by kcy29581 on 2005-09-16
Thanks Caboto, I'll get reading! :grin:

Any chance of knowing whether Synaptic will eventually have this feature integrated "officially"?

---

