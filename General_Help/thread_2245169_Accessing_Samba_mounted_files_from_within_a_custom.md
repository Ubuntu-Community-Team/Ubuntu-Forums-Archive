---
title: "Accessing Samba mounted files from within a custom program"
date: 2014-09-21
forum: General Help
---

### Post by aMomentaryBlip on 2014-09-21
Hello all,

I've recently started replacing some old xp machines with Ubuntu 14.04 installs at work. I've got all of the functionality of the previous machines minus one, miniscule problem. 

I've written several Java based standalone programs that perform various office tasks. From within the program, I open a file browser using the systems native explorer. In windows, I had access to the full network from within this explorer. On Ubuntu, however, when the file browser opens, I am unable to navigate outside of the local computer.

When I run Ubuntu's File Browser program, I can easily access the network and computers by clicking to them, create bookmarks and everything like that. Everything would be fine and dandy if I could make a symbolic link of a couple of network locations in the /mnt directory. Accessing these files from within the program I've written would be tremendously helpful.

I don't even need the solution, if you can point me in the right direction of what information this will entail, I am pretty handy at picking things up myself. I appreciate all the help.

---

### Post by aMomentaryBlip on 2014-10-04
I found a solution, so I thought I'd follow up on my post in case someone in the future has the same issue. It really boiled down to something simple. I was using the standard JFileChooser to use as a file browser within Java. Instead, I replaced it with FileDialog, which has less flexibility, but uses the OS file view, which gives you access to samba bookmarks.

---

