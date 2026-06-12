---
title: "Alsa dmix high psu usage"
date: 2019-04-07
forum: General Help
---

### Post by mrfomt on 2019-04-07
Have an Odroid Xu4 running Ubuntu 16.04 with retropie.
I had some problems with the pulseaudio, random distortions in the sound, tried to change configs and google a lot, but nothing helps. So I decided to skip pulseaudio and only use Alsa with Dmix, and the sound works great! No problem at all with the sound. Added &#8221;autospawn = no&#8221;  to /etc/pulse/client.conf, but I notice some higher cpu usage. I have set sample rate with Alsa to 44100.
mpg123 uses 30%, and mplayer 70%. 
With pulseaudio mpg123 it is 1-2% and mplayer 20-30%. Checked with command top.
I&#8217;m no expert at this, I have googled and tried to set it up correct, sound is working, but dont know why it uses more cpu.
I added softvol to asound.conf also, because in emulationstation I got an error:

**[SIZE=2]VolumeControl::init() - Failed to find mixer elements![/SIZE]**

But that dissapeard when adding softvol to asound.conf

```

$ cat /proc/asound/card0/pcm0p/sub0/hw_paramsaccess
MMAP_INTERLEAVED
format: S16_LE
subformat: STD
channels: 2
rate: 44100 (44100/1)
period_size: 1024
buffer_size: 4096
```

Here are the configs I have changed:

asound.conf
```

$ cat /etc/asound.conf
pcm.!default {
    type plug
    slave.pcm "softvol"
}
pcm.softvol {
       type softvol
       slave.pcm "dmixer"
       control {
           name "Master"
           card 0
       }
}
pcm.dmixer {
       type dmix
       ipc_key 1024


       slave {
         pcm "hw:0,0"
         period_time 0
         period_size 1024
         buffer_size 4096
         buffer_time 0
         channels 2
         rate 44100
}
       bindings {
           0 0
           1 1
       }
}




ctl.!default {
    type hw
    card 0
}
ctl.softvol {
    type hw
    card 0
}
ctl.dmixer {
    type hw
    card 0
}

```

/etc/pulse/default.pa
```

cat /etc/pulse/default.pa
#!/usr/bin/pulseaudio -nF
#
# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify it
# under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, see <http://www.gnu.org/licenses/>.


# This startup script is used only if PulseAudio is started per-user
# (i.e. not in system mode)


.nofail


### Load something into the sample cache
#load-sample-lazy x11-bell /usr/share/sounds/freedesktop/stereo/bell.oga
#load-sample-lazy pulse-hotplug /usr/share/sounds/freedesktop/stereo/device-added.oga
#load-sample-lazy pulse-coldplug /usr/share/sounds/freedesktop/stereo/device-added.oga
#load-sample-lazy pulse-access /usr/share/sounds/freedesktop/stereo/message.oga


.fail


### Automatically restore the volume of streams and devices
load-module module-device-restore
load-module module-stream-restore
load-module module-card-restore


### Automatically augment property information from .desktop files
### stored in /usr/share/application
load-module module-augment-properties


### Should be after module-*-restore but before module-*-detect
load-module module-switch-on-port-available


### Load audio drivers statically
### (it's probably better to not load these drivers manually, but instead
### use module-udev-detect -- see below -- for doing this automatically)
load-module module-alsa-sink device=dmix
load-module module-alsa-source device=hw:0,0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink


### Automatically load driver modules depending on the hardware available
.ifexists module-udev-detect.so
#load-module module-udev-detect tsched=0
.else
### Use the static hardware detection module (for systems that lack udev support)
#load-module module-detect 
.endif


### Automatically connect sink and source if JACK server is present
.ifexists module-jackdbus-detect.so
.nofail
load-module module-jackdbus-detect channels=2
.fail
.endif


### Automatically load driver modules for Bluetooth hardware
.ifexists module-bluetooth-policy.so
load-module module-bluetooth-policy
.endif


.ifexists module-bluetooth-discover.so
load-module module-bluetooth-discover
.endif


### Load several protocols
.ifexists module-esound-protocol-unix.so
load-module module-esound-protocol-unix
.endif
load-module module-native-protocol-unix


### Network access (may be configured with paprefs, so leave this commented
### here if you plan to use paprefs)
#load-module module-esound-protocol-tcp
#load-module module-native-protocol-tcp
#load-module module-zeroconf-publish


### Load the RTP receiver module (also configured via paprefs, see above)
#load-module module-rtp-recv


### Load the RTP sender module (also configured via paprefs, see above)
#load-module module-null-sink sink_name=rtp format=s16be channels=2 rate=44100 sink_properties="device.description='RTP Multicast Sink'"
#load-module module-rtp-send source=rtp.monitor


### Load additional modules from GConf settings. This can be configured with the paprefs tool.
### Please keep in mind that the modules configured by paprefs might conflict with manually
### loaded modules.
.ifexists module-gconf.so
.nofail
load-module module-gconf
.fail
.endif


### Automatically restore the default sink/source when changed by the user
### during runtime
### NOTE: This should be loaded as early as possible so that subsequent modules
### that look up the default sink/source get the right value
load-module module-default-device-restore


### Automatically move streams to the default sink if the sink they are
### connected to dies, similar for sources
load-module module-rescue-streams


### Make sure we always have a sink around, even if it is a null sink.
load-module module-always-sink


### Honour intended role device property
load-module module-intended-roles


### Automatically suspend sinks/sources that become idle for too long
load-module module-suspend-on-idle


### If autoexit on idle is enabled we want to make sure we only quit
### when no local session needs us anymore.
.ifexists module-console-kit.so
load-module module-console-kit
.endif
.ifexists module-systemd-login.so
load-module module-systemd-login
.endif


### Enable positioned event sounds
load-module module-position-event-sounds


### Cork music/video streams when a phone stream is active
#load-module module-role-cork


### Modules to allow autoloading of filters (such as echo cancellation)
### on demand. module-filter-heuristics tries to determine what filters
### make sense, and module-filter-apply does the heavy-lifting of
### loading modules and rerouting streams.
load-module module-filter-heuristics
load-module module-filter-apply


# X11 modules should not be started from default.pa so that one daemon
# can be shared by multiple sessions.


### Load X11 bell module
#load-module module-x11-bell sample=x11-bell


### Register ourselves in the X11 session manager
#load-module module-x11-xsmp


### Publish connection data in the X11 root window
#.ifexists module-x11-publish.so
#.nofail
#load-module module-x11-publish
#.fail
#.endif


### Make some devices default
#set-default-sink output
#set-default-source input

```

---

