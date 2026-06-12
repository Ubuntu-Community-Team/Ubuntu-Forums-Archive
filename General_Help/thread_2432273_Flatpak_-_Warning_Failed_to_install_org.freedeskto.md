---
title: "Flatpak - Warning: Failed to install org.freedesktop.Platform.openh264/x86_64/19.08"
date: 2019-11-29
forum: General Help
---

### Post by ardouronerous on 2019-11-29
```
flatpak update
Looking for updates...
Installing in system:
org.freedesktop.Platform.openh264/x86_64/19.08 flathub 8801c9a82f9c
Is this ok [y/n]: y
Installing: org.freedesktop.Platform.openh264/x86_64/19.08 from flathub
[####################] Downloading files: 1/1 593.6 kB (49.5 kB/s)            
Warning: Failed to install org.freedesktop.Platform.openh264/x86_64/19.08: Error deploying: While trying to apply extra data: runtime/org.freedesktop.Platform/x86_64/19.08 not installed
```

Getting this error whenever I run the flatpak update command.

---

### Post by deadflowr on 2019-11-29
Here: [https://ubuntuforums.org/showthread.php?t=2429840&p=13911400#post13911400]("https://ubuntuforums.org/showthread.php?t=2429840&p=13911400#post13911400")

---

### Post by ardouronerous on 2019-11-30
> **deadflowr said:**
> Here: [https://ubuntuforums.org/showthread.php?t=2429840&p=13911400#post13911400](https://ubuntuforums.org/showthread.php?t=2429840&p=13911400#post13911400)

```
flatpak install org.freedesktop.Platform/x86_64/19.08
flatpak uninstall --unused
flatpak update
```

Running the first command gives me this error:

```
flatpak install org.freedesktop.Platform/x86_64/19.08
Usage:
  flatpak install [OPTION&#8230;] LOCATION/REMOTE [REF...] - Install applications or runtimes

Help Options:
  -h, --help              Show help options

Application Options:
  --user                  Work on user installations
  --system                Work on system-wide installations (default)
  --installation=NAME     Work on specific system-wide installation(s)
  --arch=ARCH             Arch to install for
  --no-pull               Don't pull, only install from local cache
  --no-deploy             Don't deploy, only download to local cache
  --no-related            Don't install related refs
  --no-deps               Don't verify/install runtime dependencies
  --no-static-deltas      Don't use static deltas
  --runtime               Look for runtime with the specified name
  --app                   Look for app with the specified name
  --bundle                Assume LOCATION is a .flatpak single-file bundle
  --from                  Assume LOCATION is a .flatpakref application description
  --gpg-file=FILE         Check bundle signatures with GPG key from FILE (- for stdin)
  --subpath=PATH          Only install this subpath
  -y, --assumeyes         Automatically answer yes for all questions
  --reinstall             Uninstall first if already installed
  -v, --verbose           Print debug information during command processing, -vv for more detail
  --ostree-verbose        Print OSTree debug information during command processing

error: REMOTE and REF must be specified
```

---

### Post by deadflowr on 2019-11-30
Yeah, I just noticed the command is missing the repo.
flatpak installs usually want to where it comes from,
try
```
flatpak install flathub org.freedesktop.Platform/x86_64/19.08
```

---

### Post by ardouronerous on 2019-11-30
```
flatpak install flathub org.freedesktop.Platform/x86_64/19.08
flatpak uninstall --unused
flatpak update
```

That worked, thank you. :)

---

