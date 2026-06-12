---
title: "Hang at splash on new install (6.10) &quot;Cannont access tty&quot;"
date: 2006-12-28
forum: General Help
---

### Post by phatlip on 2006-12-28
Scenario:

  - Used alternate install i386 CD and ran through installer with no problems. 
  - Restarted machine and waited for boot. 
  - Reached Ubuntu splash screen, loading bar went about 1mm in - then hangs.
  - Screen changes to flashing underscore in the top left hand corner.
  - About 2 minutes later i am given the error message: error: "Cannont access tty; stopping job control"
  - I'm then presented with a console where i can basically do nothing.
  - alt+ctrl+f1 returns the error: /dev/hda1 does not exists! (however, ubuntu should know perfectly well that its installed onto /dev/sda1)

System:

  - AMD64 939 3000+
  - 2GB of DDR (OCZ) Ram
  - Gigabyte K8NS-pro nForce4 chipset.
  - PCI-X nvidia 7600GT gfx card.
  - 80GB SATA HDD
  - Phillips 190S 19" LCD
  - Antec 550W PSU


This is my first try at using ubuntu, before this i have been using openSUSE, so i'm probably doing something wrong. The hard-drive is good because i had an OS running fine that i formatted to install ubuntu.

Any help is appreciated - i have a handle on the cli and editing various config files. i can get into the recovery console too, just have no idea what to do to fix it.

---

### Post by dcstar on 2006-12-28
> **phatlip said:**
> 
......
Any help is appreciated - i have a handle on the cli and editing various config files. i can get into the recovery console too, just have no idea what to do to fix it.

Might be better to use this forum (could be a better chance of useful info for you situation):

[http://ubuntuforums.org/forumdisplay.php?f=140](http://ubuntuforums.org/forumdisplay.php?f=140)

---

### Post by phatlip on 2006-12-28
ok, wasn't sure if it was an install problem, since i had the same result when i installed from the live CD, and alternate CD. Each time i formatted and installed - i got the same problem.

downloaded from different mirrors each time.

---

### Post by phatlip on 2006-12-28
reading some bug reports with the same error, although it was assumed there was a connection between ATI and the bug - i'm getting it with a nvidia card. 

either way - i took their advice and commented out dri and glx in xorg.conf with the recovery console. still no change.

perhaps there is a way to watch the progress in text mode rather than a frozen splash screen?

any logs i could be checking out?

thanks.

---

### Post by phatlip on 2006-12-28
bump?

please just give me a clue to follow... do i need to provide more infomation? ask in a different place? pay someone?

---

