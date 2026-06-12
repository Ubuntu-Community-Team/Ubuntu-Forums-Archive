---
title: "firefox, so slow you'd swear it was dead"
date: 2008-04-29
forum: General Help
---

### Post by TechnoJunky on 2008-04-29
I've got no idea what's going on.  I installed Hardy Heron on my computer (kde4) and downloaded firefox to my home directory and ran it from there, and everything was fine.  I still had lots to setup.  This morning it was running fine still, then I installed firestarter (firewall), configured a static IP, got synergy working, and now everything takes 5 minutes in Firefox.  From the time I click on the Firefox icon till the time I see the window, 5 minutes.  If I click on the bookmarks pull-down window, 5 minutes, if I click on a sub-menu under bookmarks, 5 minutes.  The only thing that works as expected is clicking on links.  Everything else is running fine on the machine.  To try to resolve this, I deleted firefox and re-untar'ed it.  I tried apt-getting it, I renamed my .mozilla directory.  I even renamed my .kde4 directory.  I disabled the firewall.  Rebooted as well.  I dont' want to reinstall Hardy if I don't have to.  Any help would be appreciated.

BTW, top doesn't show anything using much CPU at all.

---

### Post by TechnoJunky on 2008-04-29
update.  It seems that it's the static IP that's causing the issue.  When I revert back to my original interfaces file, the issue goes away, but when I have my current static IP then firefox is slow.   Here's my static interfaces file.  Please show me the errors of my ways :)

auto eth0
iface eth0 inet static
address 171.188.1.63
netmask 255.255.254.0
broadcast 171.188.1.255
gateway 171.188.0.1

---

### Post by TechnoJunky on 2008-04-29
I figured it out.  when I created the new interfaces file (I never delete the originals) I left out the loop back adaptor.  I re-added auto lo, and iface lo inet loopback, and now everything is as it should be.

---

### Post by ghost_ryder35 on 2008-04-29
please mark this thread as solved.  also if you have more problems with firefox being slow look here [http://ubuntuforums.org/showthread.php?t=773851](http://ubuntuforums.org/showthread.php?t=773851)

---

