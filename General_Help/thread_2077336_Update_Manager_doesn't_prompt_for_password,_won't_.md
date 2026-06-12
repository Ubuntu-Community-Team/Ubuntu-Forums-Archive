---
title: "Update Manager doesn't prompt for password, won't install updates"
date: 2012-10-28
forum: General Help
---

### Post by steveferson on 2012-10-28
I'm having problems with Update Manager.  My set up is Lubuntu 12.04 (running on a headless HP Microserver).  It sits in another room and I log into it mostly over SSH and Remote Desktop from a Windows 7 PC.

When I login over RDP Update Manager regularly pops up telling me there are updates to install. 

[IMG]http://nerd.steveferson.com/wp-content/uploads/2012/10/muon-update-manager.png[/IMG]

When I click "Install Updates" nothing happens though.  I've done a bit of digging and if I close the update manager and restart it by running "sudo update-manager" from the command line, it works fine so I think it's because for some reason Update Manager is not asking for my admin password.

Any help on fixing this would be really appreciated!


(I orignally posted this as a reply in [http://ubuntuforums.org/showthread.php?t=2002742](http://ubuntuforums.org/showthread.php?t=2002742) but I think it's a separate issue).

---

### Post by Rex Bouwense on 2012-10-28
I would re-install the Update Manager, unless of course you had two update programs open at the same time.  You know of course only one can run at a time.

---

### Post by steveferson on 2012-10-28
I'd just restarted the machine at this point, and had only logged on through Remote Desktop the once, so I don't think there were multiple Update Managers open (nobody else uses the server but me).

---

### Post by steveferson on 2012-10-29
Right, I have confirmed that this only happens when logging on over Remote Desktop - it works fine when I'm logged in on the box itself (i.e. I get the "To install updated software, you need to authenticate." dialogue).

---

