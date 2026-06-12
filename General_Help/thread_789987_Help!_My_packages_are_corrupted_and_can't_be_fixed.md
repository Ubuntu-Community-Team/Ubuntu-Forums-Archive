---
title: "Help! My packages are corrupted and can't be fixed"
date: 2008-05-11
forum: General Help
---

### Post by Mechaphoenix25 on 2008-05-11
I was in the middle of doing a routine upgrade on Ubuntu 8.04 tonight when suddenly my laptop (Dell Inspiron 1501, 1.8GHz AMD Sempron 3500+, 2GB ram, ATI Radeon XPress 1150 with 256MB onboard RAM) did something I've never seen it do before.  The screen went completely blank, the CPU fan kept spinning, and it was still on, but the hard-drive light stopped blinking, the hard-drive stopped making any noise, and it became completely unresponsive.  I waited 5 minutes (more than enough time for the update to complete) and nothing happened.  I tried moving the mouse, messing with the keyboard, Alt+Ctrl+Backspace, Alt+Ctrl+Del, even pushing the power button.  Nothing worked.  I was forced to do a hard-reboot, which is a bad idea in the middle of an upgrade I know, but I had no choice, nothing else would get a response.  When I rebooted, the login screen worked, and obviously enough stuff works that I'm able to type this, but my panels are all messed up, all the upgrades in progress say they were upgraded but register as the un-upgraded version, and my themes are shot down the toilet.  Oh, and Nautilus is broken, so no file-browsing outside a terminal and no background.

All this is fine and dandy, I'm a computer-science major, nothing a little package re-installing won't fix... except I can't.  Synaptic errors with every single thing I try, re-upgrading, reinstalling, even trying to remove the affected packages results in an immediate error and nothing gets done.  I tried "sudo apt-get update -f", "sudo dpkg --configure -a", even "sudo dpkg -C".  Nothing works.  The errors are all in /var/cache/apt/archives, which I found out is replaced with each update.  I figured "hey, I can delete the cached files and it'll all work!"  but upon trying this (and recreating the folder structure as it was required) I found out that even FRESHLY DOWNLOADED .DEB FILES contained errors that prevented me from fixing the problems.

Please help, the only solution I can see at this point is a total reinstall, I keep my data backed up but it took me 2 weeks to get my system configured as it is, I'd hate to have to redo all that work.  Attached is a list of the packages that were registered as being updated, if anyone has any suggestions I'd be forever grateful.

---

