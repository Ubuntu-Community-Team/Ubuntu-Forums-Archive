---
title: "Open SSH URL with terminal"
date: 2019-09-02
forum: General Help
---

### Post by jpp. on 2019-09-02
Hello

I have an issue with trying to get my Ubuntu 18.04 to open SSH URL's (ssh://root@localhost:22) with terminal.

I have done the following steps, as provided in these 2 links:

[URL="https://askubuntu.com/questions/710413/open-ssh-in-terminal-by-clicking-on-ssh-userhost-links-in-browser"]
[/URL][https://askubuntu.com/questions/710413/open-ssh-in-terminal-by-clicking-on-ssh-userhost-links-in-browser](https://askubuntu.com/questions/710413/open-ssh-in-terminal-by-clicking-on-ssh-userhost-links-in-browser) (Done the steps provided by Robobenklein)

> gconftool-2 --set --type=bool /desktop/gnome/url-handlers/ssh/enabled true
gconftool-2 --set --type=string /desktop/gnome/url-handlers/ssh/command 'gnome-terminal -e "%s"'
gconftool-2 --set --type=bool /desktop/gnome/url-handlers/ssh/needs_terminal false[URL="https://askubuntu.com/questions/710413/open-ssh-in-terminal-by-clicking-on-ssh-userhost-links-in-browser"]

> 

Handler script:

[/URL]> #!/bin/bash
# We need root to install
if [ "$(id -u)" != "0" ]; then
  echo "This script must be run as root" 1>&2
  exit 1
fi

# In case file exists
if [ -f "/usr/local/bin/ssh-url-handler" ]
then
  echo "Found an old install, moving to ssh-url-handler.old"
  mv /usr/local/bin/ssh-url-handler /usr/local/bin/ssh-url-handler.old
fi

# Install handler file
touch /usr/local/bin/ssh-url-handler
echo '#!/bin/sh' >> /usr/local/bin/ssh-url-handler
echo 'd=${1#ssh://}' >> /usr/local/bin/ssh-url-handler
echo 'x-terminal-emulator -x bash -c "ssh $d" &' >> /usr/local/bin/ssh-url-handler
chmod a+x /usr/local/bin/ssh-url-handler

# Check that it is there
type ssh-url-handler >/dev/null 2>&1 || echo "Warning: the ssh-url-handler could not be found! Please check that /usr/local/bin is in the PATH"

# Now for the desktop piece:
if [ -f "/usr/share/applications/ssh-url-handler.desktop" ]
then
  echo "Found an old desktop handler, moving to .old"
  mv /usr/share/applications/ssh-url-handler.desktop /usr/share/applications/ssh-url-handler.desktop.old
fi

touch /usr/share/applications/ssh-url-handler.desktop
echo "[Desktop Entry]" >> /usr/share/applications/ssh-url-handler.desktop
echo "Type=Application" >> /usr/share/applications/ssh-url-handler.desktop
echo "Name=SSH URL Handler" >> /usr/share/applications/ssh-url-handler.desktop
echo "Exec=ssh-url-handler %u" >> /usr/share/applications/ssh-url-handler.desktop
echo "Icon=utilities-terminal" >> /usr/share/applications/ssh-url-handler.desktop
echo "StartupNotify=false" >> /usr/share/applications/ssh-url-handler.desktop
echo "MimeType=x-scheme-handler/ssh;" >> /usr/share/applications/ssh-url-handler.desktop
chmod a+x /usr/share/applications/ssh-url-handler.desktop[URL="https://askubuntu.com/questions/710413/open-ssh-in-terminal-by-clicking-on-ssh-userhost-links-in-browser"]
[/URL][URL="https://askubuntu.com/questions/710413/open-ssh-in-terminal-by-clicking-on-ssh-userhost-links-in-browser"]

[/URL]
[https://web.archive.org/web/20170923120108/http://nknu.net/ubuntu-14-04-how-to-open-ssh-links-in-a-terminal/ (This one is actually just for reference)]("https://web.archive.org/web/20170923120108/http://nknu.net/ubuntu-14-04-how-to-open-ssh-links-in-a-terminal/")

But, when I click a SSH URL, terminal opens but "empty". It is not connecting to ssh. What am I doing wrong?

Edit: Thank you CatKiller. Just to be clear, SSH server is installed on the server I am trying to reach, and yes it supports root login.

---

### Post by CatKiller on 2019-09-02
You haven't said *which* steps you've done, but the example you've given isn't going to work in any case: you can't SSH to a machine unless an SSH server is installed, which isn't by default, and you can't SSH as root.

---

### Post by TheFu on 2019-09-02
Does **ssh root@ip** work?

localhost will never connect to any remote system.

Most Ubuntu systems will not allow a root login.  It is expected we will use sudo to elevate privileges, when necessary. 

As for using a URL with ssh, I wouldn't have a clue. Seems like that would be the hard way when there are so many convenience techniques available from the shell using the ~/.ssh/config file settings.

---

### Post by jpp. on 2019-09-03
Hi TheFu

Yep, ssh root@ip works.

The reason I am trying to get this to work is that KeePassXC has an URL function that supports opening ssh:// links with terminal. I just cant get it to work properly, although others are saying this function should work by default in Ubuntu 18(.xx).

Looking back I probably shouldnt have given an example of ssh://root@localhost. Really not what this discussion is about. :-)

---

### Post by TheFu on 2019-09-03
I use KeePassXC, but not for ssh related things.  Are you using ssh-keys and the ssh-agent?  Then you only get prompted to unlock the keys, perhaps once every 12 hours and don't get hassled for authentication for any ssh-based connections.

And with the ~/.ssh/config file, you can configure short aliases which handle different ports, different userids, different keys for each remote system connection, as needed.  Once put into the config file, there's no need to remember or enter any funky port options, userids, or almost any other setting, for any ssh-based command. The only requirement is that the alias used be unique for different settings to be used.

My KeePassXC use always requires that I take active steps for anything to happen. I don't allow any automated credentials to be provided.  Call me paranoid, if you like.

---

### Post by dragonfly41 on 2019-09-03
Perhaps rethink your search pattern .. in google search for this ..

```
ssh url protocol handler
```

---

