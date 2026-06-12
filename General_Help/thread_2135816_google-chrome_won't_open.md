---
title: "google-chrome won't open"
date: 2013-04-15
forum: General Help
---

### Post by moonpoppy on 2013-04-15
i'm using ubuntu 12.04. 

removing kubuntu-desktop and dependencies caused google-chrome to be removed. i reinstalled it: through google.com/ ubuntu-software-center and ubuntu-tweak methods. either way, i can no longer open google-chrome.

i get these errors:
```


/usr/bin/google-chrome: line 8: /bin/readlink: Permission denied
/usr/bin/google-chrome: line 10: /usr/bin/dirname: Permission denied
/usr/bin/google-chrome: line 42: /chrome: No such file or directory



```

the file it's referring to says:

```

#!/bin/bash
#
# Copyright (c) 2011 The Chromium Authors. All rights reserved.
# Use of this source code is governed by a BSD-style license that can be
# found in the LICENSE file.


# Let the wrapped binary know that it has been run through the wrapper.
line 8 ==> export CHROME_WRAPPER="`readlink -f "$0"`"


line 10 ==> HERE="`dirname "$CHROME_WRAPPER"`"


# We include some xdg utilities next to the binary, and we want to prefer them
# over the system versions when we know the system versions are very old. We
# detect whether the system xdg utilities are sufficiently new to be likely to
# work for us by looking for xdg-settings. If we find it, we leave $PATH alone,
# so that the system xdg utilities (including any distro patches) will be used.
if ! which xdg-settings &> /dev/null; then
  # Old xdg utilities. Prepend $HERE to $PATH to use ours instead.
  export PATH="$HERE:$PATH"
else
  # Use system xdg utilities. But first create mimeapps.list if it doesn't
  # exist; some systems have bugs in xdg-mime that make it fail without it.
  xdg_app_dir="${XDG_DATA_HOME:-$HOME/.local/share/applications}"
  mkdir -p "$xdg_app_dir"
  [ -f "$xdg_app_dir/mimeapps.list" ] || touch "$xdg_app_dir/mimeapps.list"
fi


# Always use our versions of ffmpeg libs.
# This also makes RPMs find the compatibly-named library symlinks.
if [[ -n "$LD_LIBRARY_PATH" ]]; then
  LD_LIBRARY_PATH="$HERE:$HERE/lib:$LD_LIBRARY_PATH"
else
  LD_LIBRARY_PATH="$HERE:$HERE/lib"
fi
export LD_LIBRARY_PATH


export CHROME_VERSION_EXTRA="stable"


# We don't want bug-buddy intercepting our crashes. http://crbug.com/24120
export GNOME_DISABLE_CRASH_DIALOG=SET_BY_GOOGLE_CHROME


line 42 ==> exec -a "$0" "$HERE/chrome"  "$@"


```

i tried to clear the cache at .cache/google-chrome/Default/Cache
i'm at a loss on how to fix this. any help would be greatly appreciated. thanks in advance.

---

### Post by moonpoppy on 2013-04-15
i've done more investigating and i disabled apparmor and that made it possible to open google-chrome. the question now is how do i have apparmor active and use google-chrome simultaneously? i have no idea how to use apparmor. and how could i have triggered apparmor to block google chrome?

---

