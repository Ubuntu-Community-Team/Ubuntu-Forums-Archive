---
title: "Immediate Shutdown on Startup"
date: 2014-03-27
forum: General Help
---

### Post by 0dyss3us on 2014-03-27
Hey folks,

I just installed 13.10 over an older XP machine to turn it into a make-shift thin client that would connect to our terminal server. Everything was going fine. I wrote a shell script to run at startup that would initiate an rdesktop connection with the proper configuration in full screen so the end user wouldn't even know they're on a linux machine. I also added a line that would shutdown the computer upon exiting the rdesktop connection. I tested it numerous times and all was working fine. I was about to move the machine out of my office to the office where it will stay, but before I did, I opened it up to remove a wireless networking card because it was just going to run off ethernet now. I popped it out, and then had second thoughts because I didn't have a pci slot cover to replace it. So I popped it back in and moved the tower. After I hooked it all up, I turned it on once more to test and I was shown a different set of start screens. I didn't even make it to the desktop and it powered off. I tried it a few more times but same result. I took it back to my office to test it, and it did the same thing once. two or three more tests went normally. I thought it might be a power issue with the outlet I was using, so I went to a third office, but had the shutdown problem. I came back to my office and now it's shutting down every time.

The original start screens went: 1) BIOS, 2) Prompt saying "kvm disabled in BIOS" (don't know what it means, but never caused problems...), 3) Ubuntu loading screen, and 4) Desktop.
The new screens are: 2) BIOS, 3) white flash, 4) Prompt saying "kvm disabled in BIOS", 5) blank pink screen (not the gradient loading screen background, or wallpaper), 6) flash to black, 7) Ubuntu loading screen, 8) Prompt saying 
```
broadcast message from root@my_computer
        (unknown) at 11:46 ...
the system is going down for power off NOW!
_
```"
9) Ubuntu loading screen, and 10) blank.

I could boot into recovery mode once, but I didn't know what to do with it. I'm at a loss. Any ideas?

---

### Post by 0dyss3us on 2014-03-28
Nevermind...

I figured out that my auto-running script was working too well. Since the computer didn't have enough up time to establish its new wired connection, the rdesktop connection was cancelled and the script jumped straight to the shutdown command.

I'm a moron...

---

