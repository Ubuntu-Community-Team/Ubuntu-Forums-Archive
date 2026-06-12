---
title: "Getting failed to add i915 component master (-19) error after installation of Nvidia"
date: 2016-03-31
forum: General Help
---

### Post by mr_dude2 on 2016-03-31
After installing the Nvidia drivers via running

[COLOR=#000000]sudo add-apt-repository ppa:graphics-drivers

sudo apt-get update

sudo apt-get install nvidia-361

[/COLOR]
[COLOR=#000000]Upon shutting down I get the error:

... wait for state stop/killed, process 15677 
[/COLOR]
[COLOR=#000000]stopping rsync daemon rsync 
[/COLOR]
[COLOR=#000000]speech dispatcher disabled: edit /etc/default/speech-dis...
[/COLOR]
[COLOR=#000000]asking all remaining processes to terminate...
[/COLOR]
[COLOR=#000000]all process ended within 1 second...
[/COLOR]
[COLOR=#000000]modemmanager [801]: <info> caught signal, shutting down
[/COLOR]
[COLOR=#000000]modemmanager [801]: <info> modemmanager is shut down

[/COLOR]
[COLOR=#000000]whereas when the system boots up I get:
[/COLOR]

snd_hda_intel 0000:00:1f.3: failed to add i915 component master (-19)

Without the drivers installed the system boots up and shuts down without errors, once I re-install them here come the errors again. Anyone knows how to fix them?

[COLOR=#000000]

[/COLOR]

---

