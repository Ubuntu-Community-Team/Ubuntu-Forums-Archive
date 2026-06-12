---
title: "ssh -X errors"
date: 2012-11-25
forum: General Help
---

### Post by seattle vic on 2012-11-25
I've used ssh -X for years on my servers to open a remote application on my local laptop.  After the upgrade to 12.10, I started getting a dbus error.  I looked in the .dbus directory and in the session-bus subdirectory there were several files that had root for the owner and group.  I changed those to myself and now it works.

However, even though it's working I still get errors about the accessibility bus (whatever that is...) when I run the remote app:

WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-NxXM3Sd6al: Connection refused.

As I said, it works, but this annoyning message persists.  Any idea what it is and how to eliminate it?

---

### Post by personalpc on 2012-11-25
sudo rm -R /tmp/*

then 

sudo dpkg-reconfigure -a

restart openssh or reboot remote server.

also clear temp on client running ssh-X and added compression never hurts (ssh -c -X user@host)

---

### Post by seattle vic on 2012-11-25
> **personalpc said:**
> sudo rm -R /tmp/*

then 

sudo dpkg-reconfigure -a

restart openssh or reboot remote server.

also clear temp on client running ssh-X and added compression never hurts (ssh -c -X user@host)

Thanks for the suggestion, but I did all that with no effect; still get the same message...

---

### Post by rnerwein on 2012-11-26
> **seattle vic said:**
> I've used ssh -X for years on my servers to open a remote application on my local laptop.  After the upgrade to 12.10, I started getting a dbus error.  I looked in the .dbus directory and in the session-bus subdirectory there were several files that had root for the owner and group.  I changed those to myself and now it works.

However, even though it's working I still get errors about the accessibility bus (whatever that is...) when I run the remote app:

WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-NxXM3Sd6al: Connection refused.

As I said, it works, but this annoyning message persists.  Any idea what it is and how to eliminate it?
ssh[COLOR=Blue] WichOS[/COLOR] -X blablu  (other than ubuntu ?)
i try: ssh to_lucid(10.04) --> works ok
i try: ssh to_precise(12.04.1) --> works ok

---

