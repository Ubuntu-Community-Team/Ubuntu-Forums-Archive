---
title: "Pulseaudio intermittent issues and pavucontrol not connecting"
date: 2019-09-28
forum: General Help
---

### Post by holybladder on 2019-09-28
I'm running 18.04, all packages up to date. Recently pavucontrol started reporting that it couldn't connect to pulseaudio (screenshot attached) and other sound-generating apps only intermittently produce audio.

ps shows pa running as a child of gdm, but while open pavucontrol then causes a series of attempts to spawn a new pa process as a child of my user session - these stop as soon as pavucontrol is closed.

Based on my limited understanding, it seems like gdm/X windows isn't correctly reporting the (Address? Socket? Little unclear on that part of the system) of pulseaudio to other processes?

I've purge-and-reinstalled ("sudo apt-get --purge --reinstall install x") both pulseaudio and pavucontrol, and I've renamed both ~/.config/pulse and /etc/pulse and then killed pulseaudio (~/.config/pulse is recreated, /etc/pulse isn't and pa fails to load) but neither has resolved the issue.

Any suggestions?

---

### Post by holybladder on 2019-09-28
I meant to add: The pa processes that spawn when I open pavucontrol fail to load because I have a pa plugin (snapcast) which creates a temp file while running - those processes find it, can't delete it then abort pa loading. If I delete the temp file a second instance of pa successfully spawns off my user session and pavucontrol then connects to that, but I can't get audio through it presumably because it's conflicting with the gdm-spawned one.

---

### Post by holybladder on 2019-09-29
Updated my system to Ubuntu 19.04 and it seems to have resolved the issue.

---

