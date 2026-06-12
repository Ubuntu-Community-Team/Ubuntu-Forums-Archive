---
title: "No unity after fresh install. Ubuntu 12.10, Nvidia Geforce 295 GTX."
date: 2013-02-19
forum: General Help
---

### Post by Aerivan on 2013-02-19
So I just installed Ubuntu, updated and installed nvidia-current on my computer but it won't show me a propper desktop on booting.

**Visible symptoms:**
[LIST]
[*] Missing unity dash
[*] Missing window frames
[*] Limited resolution options
[*] Starting nvidia-settings it tells me I'm not using the xorg-config.
[*] Nvidia-settings only shows me a very limited set of options.
[*] Running nvidia-xconf replaces the xorg-config but it seems to be ignored by the system as nothing changes on reboot.
[/LIST]

I've tried updating to the latest nvidia-drivers found in the xorg-edgers ppa with no effect.

I'd very much appreciate it if someone could shine some light on what the issue might be and whether or not it's likely to be fixable.

---

### Post by dino99 on 2013-02-19
a few comments:
- now the kernel directly deal with X, so using a xorg.conf is disturbing, and should be erased.
- from synaptic: purge the graphic driver(s) (and *-video-all if installed), then reinstall nvidia-313
- reboot
- watch xorg.0.log & .xsession-errors to let you know about possible issue
- if unity does not work as it might, then either reconfigure it:
```
   sudo dpkg-reconfigure unity
```

or run : unity --reset

---

### Post by Aerivan on 2013-02-19
> **dino99 said:**
> a few comments:
- now the kernel directly deal with X, so using a xorg.conf is disturbing, and should be erased.
- from synaptic: purge the graphic driver(s) (and *-video-all if installed), then reinstall nvidia-313
- reboot
- watch xorg.0.log & .xsession-errors to let you know about possible issue
- if unity does not work as it might, then either reconfigure it:
```
   sudo dpkg-reconfigure unity
```

or run : unity --reset

Thank you! Installing the nvidia-313 drivers got the graphics going!

Question: Since we're not supposed to use the xorg.conf anymore I'm assuming that I shouldn't fiddle around with the nvidia-settings concerning monitor placement and such but use the normal display-manager, right?

Also, my keyboard is still using an american key-map even though only a swedish layout is listed under the layout settings, could that problem be related to this or should I perhaps make a new post about that? The lines at the bottom of my .xsession-errors posted below look like they might concern this topic.

I tried resetting and reconfiguring unity but the commands gave me "ERROR: the reset option is now deprecated" and nothing respectively.

```

compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
compiz (core) - Info: Loading plugin: ccp
compiz (core) - Info: Starting plugin: ccp

(gnome-settings-daemon:1576): common-plugin-WARNING **: Error reading property "Wacom Rotation" for "Wacom Bamboo 16FG 6x8 Finger pad"
compiz (core) - Info: Loading plugin: composite
compiz (core) - Info: Starting plugin: composite
compiz (core) - Info: Loading plugin: opengl
compiz (core) - Info: Unity is fully supported by your hardware.
compiz (core) - Info: Unity is fully supported by your hardware.
compiz (core) - Info: Starting plugin: opengl
compiz (core) - Info: Loading plugin: compiztoolbox
compiz (core) - Info: Starting plugin: compiztoolbox
compiz (core) - Info: Loading plugin: decor
compiz (core) - Info: Starting plugin: decor
compiz (core) - Info: Loading plugin: vpswitch
compiz (core) - Info: Starting plugin: vpswitch
compiz (core) - Info: Loading plugin: snap
compiz (core) - Info: Starting plugin: snap
compiz (core) - Info: Loading plugin: mousepoll
compiz (core) - Info: Starting plugin: mousepoll
compiz (core) - Info: Loading plugin: resize
compiz (core) - Info: Starting plugin: resize
compiz (core) - Info: Loading plugin: place
compiz (core) - Info: Starting plugin: place
compiz (core) - Info: Loading plugin: move
compiz (core) - Info: Starting plugin: move
compiz (core) - Info: Loading plugin: wall
compiz (core) - Info: Starting plugin: wall
** Message: applet now removed from the notification area
compiz (core) - Info: Loading plugin: grid
compiz (core) - Info: Starting plugin: grid
compiz (core) - Info: Loading plugin: regex
compiz (core) - Info: Starting plugin: regex
compiz (core) - Info: Loading plugin: imgpng
compiz (core) - Info: Starting plugin: imgpng
compiz (core) - Info: Loading plugin: session
compiz (core) - Info: Starting plugin: session
I/O warning : failed to load external entity "/home/vind/.compiz/session/103f03d8f5d024571f136128149938068100000015090032"
compiz (core) - Info: Loading plugin: gnomecompat
compiz (core) - Info: Starting plugin: gnomecompat
compiz (core) - Info: Loading plugin: animation
compiz (core) - Info: Starting plugin: animation
compiz (core) - Info: Loading plugin: fade
compiz (core) - Info: Starting plugin: fade
compiz (core) - Info: Loading plugin: unitymtgrabhandles
compiz (core) - Info: Starting plugin: unitymtgrabhandles
compiz (core) - Info: Loading plugin: workarounds
compiz (core) - Info: Starting plugin: workarounds
compiz (core) - Info: Loading plugin: scale
compiz (core) - Info: Starting plugin: scale
compiz (core) - Info: Loading plugin: expo
compiz (core) - Info: Starting plugin: expo
compiz (expo) - Warn: failed to bind image to texture
compiz (core) - Info: Loading plugin: ezoom
compiz (core) - Info: Starting plugin: ezoom
compiz (core) - Info: Loading plugin: unityshell
compiz (core) - Info: Starting plugin: unityshell
** Message: using fallback from indicator to GtkStatusIcon
** Message: moving back from GtkStatusIcon to indicator
[2115:2115:0219/144542:ERROR:content_settings_pref_provider.cc(475)] Invalid pattern strings: ,*
[2115:2115:0219/144542:ERROR:content_settings_pref_provider.cc(329)] Invalid pattern strings: ,*
[2115:2199:0219/144542:ERROR:object_proxy.cc(608)] Failed to get name owner. Got org.freedesktop.DBus.Error.NameHasNoOwner: Could not get owner of name 'org.chromium.Mtpd': no such name
[2115:2199:0219/144542:ERROR:object_proxy.cc(608)] Failed to get name owner. Got org.freedesktop.DBus.Error.NameHasNoOwner: Could not get owner of name 'org.chromium.Mtpd': no such name
[2115:2115:0219/144542:ERROR:object_proxy.cc(513)] Failed to call method: org.chromium.Mtpd.EnumerateStorage: object_path= /org/chromium/Mtpd: org.freedesktop.DBus.Error.ServiceUnknown: The name org.chromium.Mtpd was not provided by any .service files
[2115:2197:0219/144549:ERROR:native_backend_gnome_x.cc(448)] Keyring save failed: 
[2115:2115:0219/145501:ERROR:extension_prefs.cc(1576)] Bad or missing pref 'version' for extension 'gighmmpiobklfepjocnamgkkbiglidom'
[2115:2115:0219/145503:ERROR:extension_prefs.cc(1576)] Bad or missing pref 'version' for extension 'nonjdcjchghhkdoolnlbekcfllmednbl'
[2115:2115:0219/145505:ERROR:extension_prefs.cc(1576)] Bad or missing pref 'version' for extension 'fgbjpbdfegnodokpoejnbhnblcojccal'
[2115:2115:0219/145506:ERROR:extension_prefs.cc(1576)] Bad or missing pref 'version' for extension 'kneloppijbcidgidihgdjnooihjcdbij'
[2115:2115:0219/145506:ERROR:extension_prefs.cc(1576)] Bad or missing pref 'version' for extension 'lkllajgbhondgjjnhmmgbjndmogapinp'
[2115:2115:0219/145506:ERROR:extension_prefs.cc(1576)] Bad or missing pref 'version' for extension 'kdmmkfaghgcicheaimnpffeeekheafkb'
[2115:2115:0219/145506:ERROR:extension_prefs.cc(1576)] Bad or missing pref 'version' for extension 'aafjiaooblldgcephecfcafbmckcfeep'
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
[2115:2115:0219/145507:ERROR:extension_prefs.cc(1576)] Bad or missing pref 'version' for extension 'ehcibdjmpjlekgjhepbfmenfppliikcj'
[2115:2115:0219/145507:ERROR:extension_prefs.cc(1576)] Bad or missing pref 'version' for extension 'ejidjjhkpiempkbhmpbfngldlkglhimk'
[2115:2115:0219/145507:ERROR:extension_prefs.cc(1576)] Bad or missing pref 'version' for extension 'cldcgifnkcmflfjfbhedkdfecbaakmcd'
[2115:2115:0219/145507:ERROR:extension_prefs.cc(1576)] Bad or missing pref 'version' for extension 'namljbfbglehfnlonjmebceimaalofei'
[2115:2115:0219/145508:ERROR:extension_prefs.cc(1576)] Bad or missing pref 'version' for extension 'lcgmndephhjcabhhjfcmncnhbmgbkpij'
[2115:2115:0219/145508:ERROR:extension_prefs.cc(1576)] Bad or missing pref 'version' for extension 'nbdmccoknlfggadpfkmcpnamfnbkmkcp'
[2115:2115:0219/145508:ERROR:extension_prefs.cc(1576)] Bad or missing pref 'version' for extension 'bkgoccjhfjgjedhkiefaclppgbmoobnk'
[2115:2115:0219/145508:ERROR:extension_prefs.cc(1576)] Bad or missing pref 'version' for extension 'lbfehkoinhhcknnbdgnnmjhiladcgbol'
[2115:2115:0219/145508:ERROR:extension_prefs.cc(1576)] Bad or missing pref 'version' for extension 'omlmnomieeknagejjojcpdomnbnbchdl'
[2115:2115:0219/145509:ERROR:extension_prefs.cc(1576)] Bad or missing pref 'version' for extension 'aknpkdffaafgjchaibgeefbgmgeghloj'
[2115:2115:0219/145509:ERROR:extension_prefs.cc(1576)] Bad or missing pref 'version' for extension 'pjjhlfkghdhmijklfnahfkpgmhcmfgcm'
[2115:2115:0219/145509:ERROR:extension_prefs.cc(1576)] Bad or missing pref 'version' for extension 'hbdpomandigafcibbmofojjchbcdagbl'
[2115:2115:0219/145509:ERROR:extension_prefs.cc(1576)] Bad or missing pref 'version' for extension 'dcjeclnkejmbepoibfnamioojinoopln'
[2115:2115:0219/145510:ERROR:extension_prefs.cc(1576)] Bad or missing pref 'version' for extension 'aciahcmjmecflokailenpkdchphgkefd'
[2115:2115:0219/145510:ERROR:extension_prefs.cc(1576)] Bad or missing pref 'version' for extension 'lajkckfbiimjdfdfbjgfbdfecnbipdcm'
[2115:2115:0219/145510:ERROR:extension_prefs.cc(1576)] Bad or missing pref 'version' for extension 'offpaifnchmpbnjhjbhpdffahlofdkfb'
[2115:2115:0219/145510:ERROR:extension_prefs.cc(1576)] Bad or missing pref 'version' for extension 'mijlebbfndhelmdpmllgcfadlkankhok'
[2115:2115:0219/145511:ERROR:extension_prefs.cc(1576)] Bad or missing pref 'version' for extension 'ejjicmeblgpmajnghnpcppodonldlgfn'
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

```

---

