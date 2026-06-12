---
title: "Disable NetworkManager"
date: 2007-08-16
forum: General Help
---

### Post by jedcred on 2007-08-16
I'd like to disable NetworkManager permenently, as it seems to cause problems for me when I run /etc/init.d/networking restart on the DHCP'd ethernet connection (the connection doesn't come up).  However, if I kill nm-applet, everything is hunky-dory.  I'm trying to run a two-interface firewall and I think this has been my main problem, as, if I do it from the command line (using the command above) eth1 doesn't come up at all.  However, if I force it up with ifconfig, then click on the network manager, then it finally comes up.  This is unacceptable, as I won't have Gnome access when I'm trying to refresh my DHCP.  This shouldn't be happening anyway, yet it does.  TIA.

---

### Post by Damanther on 2007-08-16
sudo update-rc.d NetworkManager remove

That will take it out of the system startup. If you truly want to remove it you can 
sudo apt-get remove NetworkManager

---

### Post by ugm6hr on 2007-08-16
I think it is *network-manager* and *network-manager-gnome* that you need to uninstall:

```
sudo aptitude remove network-manager
```

---

### Post by Damanther on 2007-08-16
Oops,

I think ugm6hr is right. I got my Ubuntu and Fedora mixed up.

---

### Post by walkerk on 2007-08-16
> **ugm6hr said:**
> I think it is *network-manager* and *network-manager-gnome* that you need to uninstall:

```
sudo aptitude remove network-manager
```

yep. this should do the trick.

best to remove both network-manager and network-manager-gnome
```
sudo aptitude remove network-manager network-manager-gnome
```

---

### Post by Tex-Twil on 2007-09-19
Hello,
I would alos like to disable the NetworkManager. I dont want it to load on boot but I dont want to uninstall it neither. 
I did this
```

sudo update-rc.d NetworkManager remove

```

But there are still some NetworkManager processes after the boot:
```

/usr/sbin/NetworkManager --pid-file /var/run/NetworkManager/NetworkManager.pid
/usr/sbin/NetworkManagerDispatcher --pid-file /var/run/NetworkManager/NetworkManagerDispatcher.pid

```

I'm lazy to kill those everytime ..

thanks

---

### Post by mykmelez on 2008-01-31
> **Tex-Twil said:**
> Hello,
I would alos like to disable the NetworkManager. I dont want it to load on boot but I dont want to uninstall it neither.


It looks like you can disable NetworkManager without uninstalling it via the procedure described on the [Ubuntu wiki on WifiDocs/NetworkManager]("https://help.ubuntu.com/community/WifiDocs/NetworkManager#head-1de145d05f957ff659f5fdb58974ec3e5864def5"):

[https://help.ubuntu.com/community/WifiDocs/NetworkManager#head-1de145d05f957ff659f5fdb58974ec3e5864def5](https://help.ubuntu.com/community/WifiDocs/NetworkManager#head-1de145d05f957ff659f5fdb58974ec3e5864def5)

---

### Post by jjalocha on 2008-02-15
For the record: On Xubuntu Gutsy, I had to do the following for removing the network manager:

```

$ sudo aptitude purge network-manager network-manager-gnome

```


Then edit '/etc/network/interfaces', and add the following lines. Strangely, they were not present in my installation, and without these, Linux is unable to set-up the (wired) network.

```

auto eth0
iface eth0 inet dhcp

```

Then, restart the network:

```

$ sudo /etc/init.d/networking restart

```

---

