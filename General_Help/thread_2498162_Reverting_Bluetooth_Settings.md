---
title: "Reverting Bluetooth Settings"
date: 2024-06-02
forum: General Help
---

### Post by scribner on 2024-06-02
I was trying to set up a pair of Sony headphones to use with Ubuntu and need helping reverting the settings on my computer (if necessary).

Here is a link to the instructions I partially tried: <https://gist.github.com/peters/26315cd7a8a31e3d192ed05ef9a79ba7>.

I only followed steps 1 through 3:

> 
[LIST=1]
[*] Open a terminal and launch bluetoothctl:
 bluetoothctl 
[*] Initialize the agent and set it as the default:
 agent on
default-agent 
[*] Scan for Bluetooth devices:
 scan on 
[/LIST]


I am mostly interested in step 2. Is there anything I should do to revert my computer's settings back to the original?

---

### Post by currentshaft on 2024-06-03
It doesn't appear you have actually changed any system settings that would require reverting.

The agent and default-agent commands are used to configure Bluetooth settings for pairing devices, but they don't affect your system's overall settings.

This will restart the Bluetooth service, which might be what you want to do:

sudo service bluetooth stop
sudo service bluetooth start

---

### Post by #&amp;thj^% on 2024-06-03
> **currentshaft said:**
> It doesn't appear you have actually changed any system settings that would require reverting.


+1 I agree 
> **scribner said:**
> 
I only followed steps 1 through 3:


But did you also follow the whole page on suggestions?
```
sudo apt install pipewire-media-session- wireplumber
systemctl --user --now enable wireplumber.service
```
This works on 22.04 and 24.04 LTS.
For Bluetooth:
```
sudo apt install libldacbt-{abr,enc}2 libspa-0.2-bluetooth pulseaudio-module-bluetooth-
```
It may take a reboot to load all this needed "libs"

---

