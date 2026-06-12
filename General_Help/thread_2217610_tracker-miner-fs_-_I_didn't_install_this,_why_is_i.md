---
title: "tracker-miner-fs - I didn't install this, why is it eating up my CPU?"
date: 2014-04-18
forum: General Help
---

### Post by frogwarrior on 2014-04-18
I noticed my computer using a lot of CPU right after logging in so I ran top to see what was using all that RAM, and it was "tracker-miner-f", so I googled that and found a few threads talking about tracker-miner-fs and tracker-store eating up CPU for no apparent reason. I never installed these applications, could it be some kind of malware that installed them and added them as startup apps? I ran apt-get purge tracker-miner-fs and it removed some files but didn't remove tracker-store, which now runs on startup. I can't uninstall it with the package manager since the package manager can't find a package by that name. It doesn't appear in the output of ps -e, but heres what top says about it:
[IMG]http://i.gyazo.com/e7cb5687082db7a82236918cc25dc10f.png[/IMG]
I've been killing the process manually whenever I start the computer, is there a blacklist that I can add the process to so that I don't have to manually kill it every time? Also, how do I remove it from the list of startup processes? Theres no tracker-store.desktop file in the ~/.config/autostart folder. tracker-store doesn't use anywhere near as much memory as tracker-miner-fs was using on startup, now the biggest problem I have is with firefox which frequently crashes the system with its excessive RAM usage. I'm running it in safe mode now with no problems, but when I had to forcefully reboot the computer twice when starting this thread because something was eating up so much memory that the machine froze. This happened after I killed tracker-store, thats its something else thats eating up the CPU. I usually reinstall Ubuntu when this kinda thing happens, but I want to find out more about the issue first. If you suspect your system has been infected with malware and/or hacked, how do you go about confirming that, and "disinfecting" your machine?

I upped my routers firewall level and enabled ufw, but if my comp has been infected with malware, it might render all that useless so I ran chkrootkit and rkhunter to see if they tell me anything. chkrootkit found a lot of "suspcious files" and told me that /etc/init is infected with Suckit rootkit. chkrootkit commonly gives a false positive on Suckit rootkit in init so I'm ignoring that one for now. As for the suspicious files, there are a lot of them, heres a few:
```
/usr/lib/python2.7/dist-packages/PyQt4/uic/widget-plugins/.noinit /usr/lib/pymodules/python2.7/.path /usr/lib/jvm/java-8-oracle/lib/visualvm/visualvm/.lastModified /usr/lib/jvm/java-8-oracle/lib/visualvm/profiler/.lastModified /usr/lib/jvm/java-8-oracle/lib/visualvm/platform/.lastModified /usr/lib/jvm/java-8-oracle/lib/missioncontrol/plugins/org.eclipse.core.runtime.compatibility.registry_3.5.100.v20120521-2346/.api_description
```
theres nothing suspicious looking to me there. 

rkhunter on the other hand spotted something weird. Hold on, I'll rerun it and paste the output.

EDIT: For some reason rkhunter didn't detect the weird activity this time, but I still have the log file from the last scan, heres what looks weird to me:
```

[21:17:29] Info: Starting test name 'group_changes'
[21:17:29]   Checking for group file changes                 [ Warning ]
[21:17:29] Warning: Group 'jetty' has been added to the group file.
[21:17:29] Warning: Group 'guest-inCTAf' has been added to the group file.
[21:17:29] Warning: Group 'guest-0nFC5A' has been added to the group file.
[21:17:29] Warning: Group 'guest-kz6hB8' has been added to the group file.
[21:17:29] Warning: Group 'guest-XhmtJU' has been added to the group file.
[21:17:29] Warning: Group 'guest-UNkGu7' has been added to the group file.
[21:17:29] Warning: Group 'guest-lcVsBA' has been added to the group file.
...
[21:17:31] Warning: Group 'guest-aOt1uR' has been added to the group file.
[21:17:31] Warning: Group 'guest-AQvDl6' has been added to the group file.
[21:17:31] Warning: Group 'guest-PnABZW' has been added to the group file.
[21:17:32] Warning: Group 'guest-48PYmw' has been added to the group file.
[21:17:32] Warning: Group 'guest-VLNvOT' has been added to the group file.
[21:17:32] Warning: Group 'guest-qN0XR2' has been added to the group file.
[21:17:32]   Checking root account shell history files       [ OK ]

```
theres over 50 lines of that. Who/what the hell added all those groups (50 groups, all with that guest-xxxxxx format), why so many of them and why didn't rkhunter detect this the second time I ran it? I ran rkhunter -c both times.

---

### Post by HermanAB on 2014-04-18
Welcome to Ubuntu.

These useless desktop indexing programs are always the first thing I disable on new installed machine.  I have no idea why certain distros insist on it and never found it useful.  You have the same cruft on KDE, but at least, there it is easy to disable.

See this: [http://askubuntu.com/questions/346211/tracker-store-and-tracker-miner-fs-eating-up-my-cpu-on-every-startup](http://askubuntu.com/questions/346211/tracker-store-and-tracker-miner-fs-eating-up-my-cpu-on-every-startup)

---

### Post by frogwarrior on 2014-04-18
I found this useful thread on removing the useless and potentially dangerous (Zeitgeist and Geoclue, providing applications with info like that is a gaping security hole if I ever saw one) crap that comes with Ubuntu:
[http://ubuntuforums.org/showthread.php?t=2000108](http://ubuntuforums.org/showthread.php?t=2000108)

Thanks for the link, I skimmed over that thread before but missed the solution. So thats where global startup apps are stored (/etc/xdg/autostart). The Ubuntu guide tells you to edit the .desktop files and leave only Hidden=true in there, I'd personally delete the .desktop files, I don't see any reason to leave them in there. On top of tracker-store, I spotted another one that I'll be deleting (zeitgeist-datahub.desktop).

EDIT: Another one to delete: vino-server.desktop, what the hell is that doing in there, I never enabled any VNC server nor would I have any reason to. Don't tell me thats installed and enabled on Ubuntu by default too.

---

### Post by Double.J on 2014-04-18
Vino has been the default vnc server since atleast karmic as far as I can remember. Obviously enabling remote desktop is a security risk compared to not enabling it, but it is a user choice to do so. For users that do wish to access their ubuntu machines remotely, vino is a far simpler method than cli configuration. Vnc rdf and ssh are relativly standard components of most modern OS. As with so many things, it's how you use it!

---

### Post by frogwarrior on 2014-04-18
VNC is very useful for remote administration, but I wouldn't have a VNC server run on startup by default. People who do use it can just enable it when they need it.

---

### Post by mc4man on 2014-04-18
tracker-store is part of the tracker packer.
If you are running ubuntu-gnome then tracker is installed by default along with some related packages.
(or some gnome3 ppa packages may have a dep or recommend of tracker, ect.

---

### Post by den_ on 2014-04-18
So because you don't need it, it is useless. How cool of you.

Regarding your observation about KDE, and easy to disable, on Ubuntu is even more easier because the package is not part of default installation at all. Typing 'aptitude remove tracker' or whatever is also not that hard.

---

