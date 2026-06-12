---
title: "can't log in into my account"
date: 2013-10-11
forum: General Help
---

### Post by YcfG7kr on 2013-10-11
Hi everyone,
Three days ago I wanted to run some windows software under ubuntu so I installed wine. After executing some command to install a library with winetricks, the system crashed 2-3 seconds later. I had 1 or 2 windows open when suddenly the title-bar as well as the software menu-bar disappeared (I am not sure, but perhaps even the gnome-shell panel). I restarted the computer but since then I weren't able to log me in again (via GUI). I had previously about 900MB free disk but after crashing I ran out of space, just some MB were free so I deleted some files via termial. If I try to log in, a black screen with some status output flashes for fraction of a second (I were able to shot a photo with my smartphone but it doesn't display any errors) and I get back to the login prompt (tried to log in via gnome, gnome classic and unity). So I created a new user (logged in via terminal (Ctrl+Shift+F1)) and everything works fine there as well as in the guest account.
After that I installed and tried to log in via xfce which seemed to be successful, but all I can see is a desktop wallpaper and the program "launchy" (which I had installed a long time ago, but can't execute a program with it right now) but there aren't any toolbars etc. One time I saw a short information that dropbox has synchronized but nothing else.

In the "broken" user directory the .Xautority-File is empty and the .xsession-errors-File contains the following lines:

```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
Failed to connect to the VirtualBox kernel service
Failed to connect to the VirtualBox kernel service
Failed to connect to the VirtualBox kernel service
Failed to connect to the VirtualBox kernel service
gnome-session[1963]: WARNING: Could not parse desktop file /home/michael/.config/autostart/xfce4-settings-helper-autostart.desktop: Key file does not have key 'Name'
gnome-session[1963]: WARNING: could not read /home/michael/.config/autostart/xfce4-settings-helper-autostart.desktop
GNOME_KEYRING_CONTROL=/tmp/keyring-VPcr5z
GNOME_KEYRING_CONTROL=/tmp/keyring-VPcr5z
GPG_AGENT_INFO=/tmp/keyring-VPcr5z/gpg:0:1
GNOME_KEYRING_CONTROL=/tmp/keyring-VPcr5z
GPG_AGENT_INFO=/tmp/keyring-VPcr5z/gpg:0:1
SSH_AUTH_SOCK=/tmp/keyring-VPcr5z/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-VPcr5z
GPG_AGENT_INFO=/tmp/keyring-VPcr5z/gpg:0:1
SSH_AUTH_SOCK=/tmp/keyring-VPcr5z/ssh
GConf warning: failure listing pairs in `/desktop/gnome/keybindings': Configuration server couldn't be contacted: D-BUS error: Connection is closedGConf Error: Configuration server couldn't be contacted: D-BUS error: Connection is closed
GConf Error: Configuration server couldn't be contacted: D-BUS error: Connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/desktop/background/': The connection is closed

** (gnome-settings-daemon:2043): WARNING **: Could not listen to session manager: The connection is closed
xcb_connection_has_error() returned true

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/system/smb/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/empathy/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/empathy/ui/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/empathy/contacts/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/empathy/sounds/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/empathy/notifications/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/empathy/conversation/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/empathy/hints/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/empathy/location/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/desktop/gnome/crypto/pgp/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/evince/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/file-roller/listing/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/file-roller/ui/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/file-roller/general/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/file-roller/dialogs/extract/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/file-roller/dialogs/add/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/file-roller/dialogs/batch-add/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/file-roller/dialogs/last-output/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/deja-dup/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/deja-dup/s3/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/deja-dup/file/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/deja-dup/ssh/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/apps/onboard/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/apps/onboard/icon-palette/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/gnome-system-log/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/Totem/opensubtitles/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/desktop/gnome/remote-access/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/apps/seahorse/listing/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/nautilus/preferences/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/nautilus/icon-view/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/nautilus/compact-view/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/nautilus/list-view/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/nautilus/sidebar-panels/tree/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/nautilus/desktop/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/nautilus/window-state/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/Totem/jamendo/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/system/dns-sd/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/gnome-session/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/vinagre/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/com/ubuntu/update-notifier/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gwibber/preferences/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/apps/indicator-session/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/desktop/gnome/crypto/cache/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/brasero/config/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/brasero/filter/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/brasero/display/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/libgnomekbd/desktop/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/libgnomekbd/preview/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/libgnomekbd/indicator/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/libgnomekbd/keyboard/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/apps/notify-osd/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/desktop/gnome/crypto/pgp/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/com/canonical/unity-2d/launcher/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/settings-daemon/peripherals/smartcard/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/settings-daemon/peripherals/touchpad/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/settings-daemon/plugins/a11y-keyboard/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/settings-daemon/plugins/background/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/settings-daemon/plugins/clipboard/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/settings-daemon/plugins/font/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/settings-daemon/plugins/housekeeping/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/settings-daemon/plugins/keybindings/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/settings-daemon/plugins/keyboard/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/settings-daemon/plugins/media-keys/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/settings-daemon/plugins/mouse/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/settings-daemon/peripherals/mouse/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/settings-daemon/plugins/smartcard/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/settings-daemon/plugins/sound/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/settings-daemon/plugins/xrandr/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/settings-daemon/plugins/xsettings/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/apps/update-manager/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/eog/fullscreen/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/eog/plugins/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/eog/ui/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/eog/view/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/Bluetooth/sendto/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/Totem/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/gnome-screenshot/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/desktop/background/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/desktop/media-handling/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/desktop/applications/office/calendar/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/desktop/applications/office/tasks/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/desktop/applications/terminal/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/desktop/interface/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/desktop/lockdown/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/system/proxy/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/system/proxy/http/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/system/proxy/https/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/system/proxy/ftp/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/system/proxy/socks/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/desktop/thumbnail-cache/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/desktop/sound/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/desktop/a11y/keyboard/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/desktop/a11y/applications/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/desktop/a11y/mouse/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/desktop/thumbnailers/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/NautilusSendto/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/desktop/a11y/mouse/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/apps/seahorse/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/Totem/jamendo/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/gedit/preferences/editor/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/gedit/preferences/ui/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/gedit/preferences/print/': The connection is closed

(process:2064): GLib-GIO-CRITICAL **: g_dbus_connection_signal_subscribe: assertion `G_IS_DBUS_CONNECTION (connection)' failed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/gedit/preferences/encodings/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/gedit/plugins/': The connection is closed

** (process:2064): WARNING **: Error connecting: Connection refused

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/apps/shotwell/preferences/ui/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/apps/shotwell/preferences/slideshow/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/apps/shotwell/preferences/window/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/apps/shotwell/preferences/files/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/apps/shotwell/preferences/editing/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/apps/shotwell/video/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/apps/shotwell/printing/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/apps/shotwell/sharing/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/apps/shotwell/plugins/enable-state/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/apps/shotwell/sharing/facebook/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/apps/shotwell/sharing/flickr/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/apps/shotwell/sharing/picasa/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/apps/shotwell/sharing/org-yorba-shotwell-publishing-piwigo/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/apps/shotwell/sharing/org-yorba-shotwell-publishing-yandex-fotki/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/apps/shotwell/sharing/youtube/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/settings-daemon/plugins/housekeeping/': The connection is closed

** (gnome-settings-daemon:2043): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/desktop/thumbnail-cache/': The connection is closed
g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0).
```

Has anybody some suggestions what I can do to repair my system?
Thanks in advance.

---

