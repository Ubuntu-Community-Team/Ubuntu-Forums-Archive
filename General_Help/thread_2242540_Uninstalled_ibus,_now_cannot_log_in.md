---
title: "Uninstalled ibus, now cannot log in"
date: 2014-09-02
forum: General Help
---

### Post by klundermann on 2014-09-02
With synaptic I unstalled all of the ibus-related packages I could find.  I won't try to explain why, for doing so would probably only make me look even stupider.

Anyway, I can no longer log in.  When I attempt to do so, I get the message "Failed to start session" after I type my password.

First I thougt I might try to re-install from the command line the packages I had removed.  I restarted the machine and selected the advanced options in grub and booted to a command line.  I then tried
```
apt-get install ibus
```
but the result was
[COLOR=#ff0000]
W: Not using locking for read-only lock file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt
E: The package lists or status file could not be parsed or opened.
[/COLOR]
Next, I thought I might be able to decrypt and copy my data to a new location and then re-install 14.04.  I plugged in a USB stick with 14.04 on it and booted from that.  Then I found my home directory on the hard disk and ran```
sudo ecryptfs-recover-private <my username>
``` After entering my 32-character passphrase, I got a message saying the the operation had succeeded and that the directory was now mounted at  /tmp/encryptfs.<several characters>.  Great!  I use sudo to open up a Nautilus window and go to the directory and then click Access-Your-Private-Data.desktop.  A Nautilus window flashes and then immediately closes.  So how do I actually access the files I've so painstakingly recovered?

Would anybody have any ideas how I could fix the system so I can log in as before or, failing that, recover my data?

---

