---
title: "Change default systemd service installation behavior for a package"
date: 2019-10-07
forum: General Help
---

### Post by riek on 2019-10-07
Hi there, 
I'm using teamviewer every once in a while to connect to Windows machines, so I have their repository added to my package sources.
By default the teamviewer package installs a unit file, that enables the teamviewer service. But I don't need this service to be running at all times, so I disable it.
Now every time a system update installs a new version of the package, the service gets re-enabled.

So I was wondering how I should go about changing the default behavior of this package installation?
I have a couple of ideas, but I'm not sure if they would work and if there is perhaps an easier way:
1. Try to make it a .socket file, that will start the teamviewer service if I run a command, and at the same time somehow blocks (?) the enabling of the service file.
2. Check with inotify for the service file and automatically run `systemctl disable...`

How would you go about this?
Thanks

---

### Post by Xian on 2019-10-07
Try using systemd&#8217;s mask feature. 
This will symlink /etc/systemd/system/<name>.service to /dev/null.

To mask the service:

```
sudo systemctl mask <name>
```

Keep in mind that if you want to restart the service it will first need to be un-masked.

```
sudo systemctl unmask <name>
sudo systemctl enable <name>
sudo systemctl start <name>
```

---

