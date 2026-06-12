---
title: "Multiple issues with Ubuntu 20.04.1"
date: 2020-08-08
forum: General Help
---

### Post by peterroux on 2020-08-08
My system.  Gigabyte Aorus extreme motherboard with AMD 3900 CPU, 64g Mem, MSI 5700 Gaming X GPU, 2 TB SSD boot disk, 2x16TB Seagate Exos drives.  Cabled network.

Long term Linux user from 1993.

Upgraded from fully working 18.04.  During the install, I selected for all config files to go back to maintainers defaults.  Have also ensure all up to date with latest patches.

Following issues being noticed:

1. On login page after fresh boot, and using default "Ubuntu" session, the system does log in, but within a few seconds freezes.  No keyboard or mouse activity.  Cannot open terminal for example.  Mouse cursor is shown to bottom right of screen but does not move.  I can see changes in task bar of internet up/down speeds though, but as mentioned I cannot do anything.  HARD boot required.  Checking logs afterwards shows give no indication of a problem.

2. On login page If I select "Gnome Classic" same issue as mentioned in point 1.  It just freezes with same results.  HARD boot required.  

3. On login page, if I select "Ubuntu Wayland", finally I am able to login okay.  However further issues to note as follows:

4. I am unable to get into settings.  Settings menu used to be under the top right icons of Ubuntu, but there is no such option shown there.  There is no settings option within the apps.  If I right-click on the actual desktop, it does show an option for settings, and also for Display Settings, but when either is clicked nothing happens.

5.  Cannot play mkv video files using the default video player.  Get message "There is no application installed for Matroska video files.  Sames goes for other video formats such as mp4.   Same issue applies to music files such as mp3.  It seems that all mime settings are not being seen.  I tried using vlc to open the file, but this crashes straight away with SIGSEGV fault in XCloseDisplay().

6.  GPU benchmark test.  I tried to use Unique Heaven 4.0 to do a benchmark test to see if any significant difference using 20.04, but when doing so this actually never finishes - only does about 20 seconds of the test - and causes the entire PC to crash and reboot.  I manually installed latest drives from AMD site and slightly better stability but still the benchmark crashes.  Tried other benchmarks too, with similar issues. 

7. Steam.  Trying to play a game.  Often causes complete reboot of the PC.  I've tried with a number of games, such as Witcher, and Tomb Raider with same issues.

So all in all, not a pleasant experience so far.  I'm very surprised that so many things are broken even with this point release.  Any suggestions?

---

### Post by SeijiSensei on 2020-08-08
> **peterroux said:**
> 5.  Cannot play mkv video files using the default video player.  Get message "There is no application installed for Matroska video files.  Sames goes for other video formats such as mp4.   Same issue applies to music files such as mp3.  It seems that all mime settings are not being seen.  I tried using vlc to open the file, but this crashes straight away with SIGSEGV fault in XCloseDisplay().
Install mpv and its excellent GUI front-end smplayer.

Honestly, if you're having this many problems, I'd just do a clean install of 20.04.1.

---

