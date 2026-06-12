---
title: "flatpak apps refuse to start with a: unable to connect to X error or Display:99"
date: 2019-11-02
forum: General Help
---

### Post by rasmus91 on 2019-11-02
Hi there.

I'm having some problems running flatpaks on my system. They seem to all have issues connecting to the X-server. I've been googling until my fingers are numb, but I can't seem to find any posts or suggestions as to how to solve the exact issues I'm having. 

(I've tried to switch the system language to english, but it seems to don't care that much, and still print part of error messages in Danish. sorry)

The system is elementary OS Juno, e.g. Bionic Beaver

trying to run gnome builder:

```
$ flatpak run org.gnome.Builder 
Gtk-Message: 22:26:12.926: Failed to load module "pantheon-filechooser-module"
Invalid MIT-MAGIC-COOKIE-1 keyUnable to init server: Kunne ikke forbinde: Opkobling nægtet

(gnome-builder:2): Gtk-WARNING **: 22:26:12.928: cannot open display: :99.0
```

the invalid MIT-MAGIC-COOKIE-1 line says at the end: "could not connect: connection refused"

trying to run midori:

```
$ flatpak run org.midori_browser.Midori 
Gtk-Message: 22:30:49.856: Failed to load module "pantheon-filechooser-module"
Invalid MIT-MAGIC-COOKIE-1 keyUnable to init server: Kunne ikke forbinde: Opkobling nægtet

(midori:2): Gtk-WARNING **: 22:30:49.860: cannot open display: :99.0
```

And lastly trying to run steam:
```

$ flatpak run com.valvesoftware.Steam
https://github.com/flathub/com.valvesoftware.Steam/wiki/Frequently-asked-questions
Overriding TZ to Europe/Copenhagen
Running Steam on org.freedesktop.platform 19.08.3 64-bit
STEAM_RUNTIME is enabled automatically
Pins up-to-date!
Installing breakpad exception handler for appid(steam)/version(0)
Invalid MIT-MAGIC-COOKIE-1 key[2019-11-02 22:26:17] Startup - updater built Apr  9 2019 22:48:20
ILocalize::AddFile() failed to load file "public/steambootstrapper_english.txt".
../steamexe/updateui_xwin.cpp (339) : Assertion Failed: Could not open connection to X
Installing breakpad exception handler for appid(steam)/version(1.0)
sh: /home/rasmus/.local/share/Steam/steam_msg.sh: Ingen sådan fil eller filkatalog
crash_20191102222617_3.dmp[135]: Uploading dump (out-of-process)
/tmp/dumps/crash_20191102222617_3.dmp
../steamexe/updateui_xwin.cpp (339) : Assertion Failed: Could not open connection to X
../steamexe/main.cpp (754) : Assertion Failed: failed to initialize update status ui, or create initial window
../steamexe/main.cpp (754) : Assertion Failed: failed to initialize update status ui, or create initial window
crash_20191102222617_3.dmp[135]: Finished uploading minidump (out-of-process): success = yes
crash_20191102222617_3.dmp[135]: response: CrashID=bp-34644aa0-f631-477d-8432-bf4282191102
crash_20191102222617_3.dmp[135]: file ''/tmp/dumps/crash_20191102222617_3.dmp'', upload yes: ''CrashID=bp-34644aa0-f631-477d-8432-bf4282191102''
```

Again, I really have no idea what to do. I've tried switching the driver version. Running it on the Dedicated nvidia card, on the intel card. Under the nvidia driver and under the nouveau driver with no change to it. If anyone can help me figure this out I'll be very happy. Thank you for reading through this.

---

