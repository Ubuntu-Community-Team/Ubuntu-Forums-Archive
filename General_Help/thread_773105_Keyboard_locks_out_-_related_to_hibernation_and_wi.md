---
title: "Keyboard locks out - related to hibernation and wireless networking?"
date: 2008-04-28
forum: General Help
---

### Post by fergalm on 2008-04-28
I have a strange bug, and one I don't know has a solution, but I'm posting to let others know about one possible work around. And maybe someone out there knows how to fix it, here's hoping.

The System
I'm running Kubuntu 7.1 with KDE 3.8 on a Dell Latitude D610 laptop

The Problem
After resuming from hibernation, sometimes the keyboard locks out. The mouse works fine, but no key or key combination produces any effect. The system then fails to reboot when requested, halting on the line "Shutting down Network Card" (or some such), and a hard reboot is required. When you restart the computer, I can login (typing my user name and password), and type for about 10 seconds (less time than necessary for all my applets to load) on the keyboard until it locks out again, and another hard reboot is required.

Reproduction:
This has happened to me three times, and each time it happened I noticed the following pattern.
o I resumed from hibernation in a different building than where I shut down. When I hibernated, I was connected to a wireless network.
o Using KNetworkManager, I select a new wireless network connection, because I'm out of range of the old one.
o I connect momentarily, and then lose connection
o I notice the keyboard isn't working.

Of course, I've never try starting up any other way, but my suspicion still lies with the network card manager. 

Workaround.
Reboot your computer. When you get to the login page hit [Ctrl]+[Alt]+[F1] and log in at a text terminal.
Make a copy of your .kde directory
  cp .kde oldkde
Remove your .kde directory
  rm -r .kde
Switch back to a graphical login using [Ctrl]+[Alt]+[F7] and login as usual.

You will have lost all your settings, but at least your keyboard still works. You can play with restoring your settings by copying directories from oldkde/ to .kde/ and seeing if your computer reboots without complaint.

This is a far from ideal workaround, but it's better than having no keyboard. If anyone has any better solutions, please post.


Fergal

---

