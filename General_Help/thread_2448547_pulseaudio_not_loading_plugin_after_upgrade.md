---
title: "pulseaudio not loading plugin after upgrade"
date: 2020-08-09
forum: General Help
---

### Post by bobby-fischer on 2020-08-09
Upgraded Ubuntu 19.10 -> 20.10
pulseaudio dynamic range compression plugin/sink stopped working after boot up (other than that pulseaudio is working)
But if (after boot up) I kill the daemon manually from a terminal it auto restarts and the plugin/sink is loaded and working!


I have a ~/.config/pulse/default.pa (the relevant lines are):
```
  ## load ladspa module
  set-default-sink alsa_output.pci-0000_00_1f.3.analog-stereo


  .ifexists module-ladspa-sink.so
  .nofail
  load-module module-ladspa-sink sink_name=compressor-stereo plugin=sc4_1882 label=sc4 control=1,1.5,401,-30,20,5,12
  .fail
  .endif


  # set our custom compressor audio as default
  set-default-sink compressor-stereo

```

In the journal log this is the only error:
```
  pulseaudio[1842]: Sink alsa_output.pci-0000_00_1f.3.analog-stereo does not exist.

```

After a fresh boot the sinks look like this:
```
  pacmd list-sinks | awk '/index/ || /name:/ || /alsa.card_name/ || /device.description/'
  * index: 2
        name: <alsa_output.pci-0000_00_1f.3.analog-stereo>
                alsa.card_name = "HDA Intel PCH"
                device.description = "Built-in Audio Analogue Stereo"

```

Then after a manual restart of pulse audio:
```
  systemctl --user stop pulseaudio.service #(auto restarts)
  pacmd list-sinks | awk '/index/ || /name:/ || /alsa.card_name/ || /device.description/'
      index: 0
          name: <alsa_output.pci-0000_00_1f.3.analog-stereo>
                  alsa.card_name = "HDA Intel PCH"
                  device.description = "Built-in Audio Analogue Stereo"
    * index: 1
          name: <compressor-stereo>
                  device.description = "LADSPA Plugin SC4 on Built-in Audio Analogue Stereo"

```


I've tried putting a script in ~/.config/autostart  to restart pulseaudio there... but that doesn't work. It only works from my terminal.
Could it be some path or library variable?
When I run env command I don't see anything special related to this. Also if that's the case why doesn't pulseaudio show an error related to it?

Thanks

---

### Post by bobby-fischer on 2020-08-11
I found the cause of the problem (but not the solution).
pulseaudio is trying to load the plugin before setting up the sound cards sink.
The plugin obviously cannot find the sink for the sound card and fails. (It finds the auto_null sink and causes feedback loop error/issues).
How do I force pulseaudio to load the hardware sound card sink before the plugin sink?!
Here is my updated settings:

```

# This doesn't seem to do anything or force it to be loaded first
set-default-sink alsa_output.pci-0000_00_1f.3.analog-stereo

## load ladspa module
# The sink_master parameter doesn't seem to be forcing pulseaudio to load the soundcard sink first
load-module module-ladspa-sink sink_name=compressor-stereo sink_master=alsa_output.pci-0000_00_1f.3.analog-stereo plugin=sc4_1882 label=sc4 control=1,1.5,401,-30,20,5,12

# set our custom compressor audio as default
set-default-sink compressor-stereo

```

Once I'm booted, if I kill pulseaudio, it restarts, and then it all works correctly!
Very strange!
Is Gnome doing something with pulse audio sinks at boot?

---

