---
title: "bluetooth headset + skype, *so* close to working... (Gutsy)"
date: 2008-03-21
forum: General Help
---

### Post by nemuri on 2008-03-21
Greetings all - long time reader, first time poster - and first and foremost immense gratitude to everyone on this forum... Very much a total n00b but amazed at having managed to make it this far with using Linux, exclusively via this forum (and perhaps a thorough effort to stick with hardware highlighted on these boards as being highly compatible with Ubuntu:)

Just dealing with one major issue for which I can't seem to find a solution at the moment. I'm on a fresh Gutsy install, and seem to be maddeningly close to getting my Plantronics 510 headset working with Skype. After wading through a large number of threads, I've got Blueman running, my .asoundrc is as it should be AFAIK and the headset pairs via the following commands that I just pulled straight out of the howto on the [Bluez wiki]("http://wiki.bluez.org/wiki/HOWTO/AudioDevices"):

```
 dbus-send --system --type=method_call --print-reply --dest=org.bluez /org/bluez org.bluez.Manager.ActivateService string:audio

dbus-send --system --type=method_call --print-reply --dest=":1.26" /org/bluez/audio org.bluez.audio.Manager.CreateHeadset string:00:03:89:82:9A:A6

dbus-send --system --type=method_call --print-reply --dest=":1.26" "/org/bluez/audio/device0" org.bluez.audio.Headset.Connect

dbus-send --system --type=method_call --print-reply --dest=":1.26" "/org/bluez/audio/device0" org.bluez.audio.Headset.Play

```

The above commands get me the correct audio responses in the headset - so thus far, so good, I think. But looking at the output in the terminal from which I ran Blueman, I get these errors, immediately after both the CreateHeadset and Headset.Connect commands above (though interestingly not for the Headset.Play command):

```
** (blueman:5733): CRITICAL **: dbus_g_proxy_connect_signal: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (blueman:5733): CRITICAL **: dbus_g_proxy_connect_signal: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (blueman:5733): CRITICAL **: dbus_g_proxy_call: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (blueman:5733): CRITICAL **: dbus_g_proxy_disconnect_signal: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (blueman:5733): CRITICAL **: dbus_g_proxy_disconnect_signal: assertion `DBUS_IS_G_PROXY (proxy)' failed

```

So I try starting up Skype anyway, and set the audio settings in Skype to the headset. Clicking the Test Sound button yields the full, clear audio glory of the Skype login sound in the headset, and then the headset is immediately disconnected thereafter, followed by the output of the same errors above... Reconnecting the headset yields the same result the instant after any audio passes from Skype to the headset.

Obviously this is some issue with dbus, and as per a bit more forum perusal I've tried installing dbus-x11 as per some suggestions, uninstalling/reinstalling both dbus and dbus-x11, but no luck. I'm just about ready to give up entirely, but was hoping for any additional suggestions anyone might have.

Cheers,
nemuri

---

