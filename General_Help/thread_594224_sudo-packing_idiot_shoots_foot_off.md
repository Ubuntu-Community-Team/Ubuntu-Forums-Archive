---
title: "sudo-packing idiot shoots foot off"
date: 2007-10-27
forum: General Help
---

### Post by raydar on 2007-10-27
I can't believe I'm about to admit this, but . . .

I botched an install of VMware server, & the uninstall didn't get everything, so I went to try to erase remaining traces so the reinstall would proceed, and I sudo rm'd everything inside my /usr/bin instead of inside the vmware folder *within* my /usr/bin.  

I'm able to boot the drive and write this post because I still had an "old" Ubuntu drive to copy /usr/bin/* over from (recently upgraded to Gutsy, but video wouldn't work right),  It didn't copy an X11 folder, but I can remedy that.  Various things aren't working right, though, e.g. Thunderbird won't start, and I can't imagine I didn't break gobs of packages & system stuff.  I'm too much the Linux newb to know how fatal & how recoverable that is; all I can say is I did it from the terminal, so the recycle bin is not my savior. :(  

Anybody happen to know a way to cause an automatic rebuild by the system and by (e.g.) Synaptic, to write anew all the files that should be in /usr/bin?  Or is it R.I.P.?

---

### Post by hikaricore on 2007-10-27
If you can get Synaptic up, I'd imagine you could mark every single installed package for reinstall.

Not sure if that will fix everything, but it should help.

---

### Post by sloggerkhan on 2007-10-27
Hey, if you have a separate /home, just reinstall over the rest of it. If you don't back up your /home and reinstal, then copy /home back.

---

### Post by raydar on 2007-10-28
Thanks, guys.  I did download Kubuntu 7.10, just to give KDE a whirl for fun, but when I boot the CD, the installation hangs on a fresh black screen right after it says it's loading cups.  

So I went back & tried selecting all installed packages for reinstallation.  It takes several minutes for Synaptic to do the marking & figure out what all it has to do, and a box comes up listing a few non-supported apps that "may let a malicious person damage or take control of my computer."  Then when I hit Apply, I get an error box containing the following:

E: I wasn't able to locate file for the realplay package. This might mean you need to manually fix this package.
E: Unable to lock the download directory

That's a quote from the second time I tried it; on the first try, that first "E:" line specified not Realplayer but the 2.6.20 low-latency kernel.  Before I tried it the second time, I deselected the two or three items in Synaptic that specifically mentioned that kernel.  But as you see, on the second try, Realplayer just jumped in to fill the first "E:" line slot where the kernel had been listed before.

Is that "Unable to lock the download directory" a permissions thing?  I'm operating in "Failsafe Gnome" mode, 'cause my regular session won't start (it just keeps looping back to Nvidia splash screen & Gnome login), but the failsafe mode took my normal username & password just fine.  I was prompted for my password when I started Synaptic, and it was accepted, and I tried reinstalling just a single package, Thunderbird, and that did work just fine.  Maybe I just haven't found the right package(s) not to include in the mass-reinstallation.

Any ideas, before I go back & try the other option, reinstalling the OS, again (maybe with a Gnome distro, since the Kubuntu disc doesn't want to boot)?

UPDATE: Had to omit some alsa-tools, Realplayer, 2.6.20 kernel, ubuntu-session-splashes, and wired files, and that way did a mass reinstall. Did those omitted packages individually afterward except the old kernel files and, because they apparently no longer exist, the splashes. Got a funny "E.couldn't configure pre-depend sysvutils for upstart, probably a dependency cycle" error, and another the same but for coreutils and dpkg; but did those individually successfully.  I still can't boot into a normal Gnome session, though; I have to either get rid of my xorg.conf or choose failsafe Gnome mode at login. 

Also still trying to get Kubuntu install to boot . . . grrr, I screwed myself good! :(

---

