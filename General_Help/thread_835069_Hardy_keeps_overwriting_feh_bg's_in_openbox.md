---
title: "Hardy keeps overwriting feh bg's in openbox"
date: 2008-06-20
forum: General Help
---

### Post by HangukMiguk on 2008-06-20
every time I have to log out of openbox, whenever I log back in, I lose my background.  It's not that I don't have it set up in Autostart to run feh, it's that Hardy keeps overwriting my background to the default Hardy wallpaper, meaning I have to open up aterm to reset my wallpaper everytime.

Here's the contents of /home/xxxxx/.config/openbox/autostart.sh:

```
# This shell script is run before Openbox launches.
# Environment variables set here are passed to the Openbox session.

# Set a background color
BG=""
if which hsetroot >/dev/null; then
    BG=hsetroot
else
    if which esetroot >/dev/null; then
	BG=esetroot
    else
	if which xsetroot >/dev/null; then
	    BG=xsetroot
	fi
    fi
fi
test -z $BG || $BG -solid "#303030"

# D-bus
if which dbus-launch >/dev/null && test -z "$DBUS_SESSION_BUS_ADDRESS"; then
       eval `dbus-launch --sh-syntax --exit-with-session`
fi

# Make GTK apps look and behave how they were set up in the gnome config tools
if which gnome-settings-daemon >/dev/null; then
  gnome-settings-daemon &
fi

# Preload stuff for KDE apps
if which start_kdeinit >/dev/null; then
  LD_BIND_NOW=true start_kdeinit --new-startup +kcminit_startup &
fi

pypanel &
conky &
gdesklets &
pidgin &
screenlets &
eval `cat $HOME/.fehbg` &
```

---

### Post by HangukMiguk on 2008-06-24
Bump, I'm really needing a fix for this, it's getting incredibly annoying.

---

