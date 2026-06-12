---
title: "rdesktop and krdc show corrupted image when scroll up"
date: 2007-01-17
forum: General Help
---

### Post by geoff123 on 2007-01-17
I wanted to share a solution to a problem with rdesktop and krdc I had been having (connected to windows server at work). The windows were not refreshing properly when scrolling UP and moving windows around.  For example, in Outlook I could scroll down just fine and read the email, but when i scrolled back up the page it looked corrupted until I scrolled down again or refreshed the screen by minimizing and then maximizing the window again. Very tiresome.

This solution came from the website: [http://www.nvnews.net/vbulletin/showthread.php?t=50434&page=2](http://www.nvnews.net/vbulletin/showthread.php?t=50434&page=2)

1)backup /etc/X11/xorg.conf
2)close running programs on the desktop
3)ADD the  4 lines below to your /etc/X11/xorg.conf file (mine is right after the mouse input device section, but I don't think it matters where it goes). Also, guessing this might cause problems if using compiz that might need this or such??
4)Restart X (ctl-alt-backspace) 

# ADDED TO FIX RDESKTOP REFRESH PROBLEM
Section "Extensions"
    Option        "Composite" "Disable"
EndSection

Good Luck, Geoff

---

### Post by dcstar on 2007-01-17
> **geoff123 said:**
> I wanted to share a solution to a problem with rdesktop and krdc I had been having (connected to windows server at work). The windows were not refreshing properly when scrolling UP and moving windows around.  For example, in Outlook I could scroll down just fine and read the email, but when i scrolled back up the page it looked corrupted until I scrolled down again or refreshed the screen by minimizing and then maximizing the window again. Very tiresome.

This solution came from the website: [http://www.nvnews.net/vbulletin/showthread.php?t=50434&page=2](http://www.nvnews.net/vbulletin/showthread.php?t=50434&page=2)

1)backup /etc/X11/xorg.conf
2)close running programs on the desktop
3)ADD the  4 lines below to your /etc/X11/xorg.conf file (mine is right after the mouse input device section, but I don't think it matters where it goes). Also, guessing this might cause problems if using compiz that might need this or such??
4)Restart X (ctl-alt-backspace) 

# ADDED TO FIX RDESKTOP REFRESH PROBLEM
Section "Extensions"
    Option        "Composite" "Disable"
EndSection

Good Luck, Geoff

Since this seems to be a nvidia driver issue, perhaps next time you could be a little more specific and state this in your post?

---

### Post by chooseopen on 2007-03-05
You are da man!  I do alot of work via RDP and have been fighting this for months! 

Thanks SO much!

Jason

---

### Post by afljafa on 2007-03-19
Cheers for that - fixed my problems here.

---

