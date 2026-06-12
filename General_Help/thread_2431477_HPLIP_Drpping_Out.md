---
title: "HPLIP Drpping Out"
date: 2019-11-17
forum: General Help
---

### Post by Quarkrad on 2019-11-17
For the past few years/versions I have found the wifi setup in hplip eventually drops outs/fails to connect.  I have tried all manner of initial connections using hp-setup, cups, static ip addresses and no matter what method I use eventually the printer disappears and I have to re-establish the connection.  (Eventually means 'months').  This causes me some grief as it on family/friends machines that I have converted to Ubuntu and hp printers.  Back in the 10.04 and 12.04 days hplip seemed to be rock solid but since then I have to constantly re-establish the connection.  Any advise above the normal connection methods would be most appreciated - I'm off this afternoon as a neighbours printer has again disappeared (they are running 18.04 and hplip 3.19.8).

---

### Post by #&amp;thj^% on 2019-11-17
I'm not sure if this will help you, but when that was happening on Xenial, I just edited: "/etc/NetworkManager/conf.d/default-wifi-powersave-on.conf"
```
sudo nano /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf

```
And changed the:
```
[connection]
wifi.powersave = 3

```
To:
```
[connection]
wifi.powersave = 2
```
I have kept this setting since.
If you still have the same issue, use:
```
journalctl --follow
```
Then when the connection drops again look at the messages

---

### Post by #&amp;thj^% on 2019-11-18
Thought I would also leave you with this:
1.Remove hplip completely After the normal un-install (Terminal/or Package manger):
```

sudo rm -rf /usr/share/hplip
sudo rm -rf /etc/hp
sudo rm -rf ~/.hplip
sudo rm -rf /var/lib/hp
```

2. Downloaded an older version, namely hplip-3.18.6.run from:
[https://sourceforge.net/projects/hplip/files/hplip/](https://sourceforge.net/projects/hplip/files/hplip/)

3. Then Installed it:

Switch to the directory with the downloaded file:
```

cd Downloads
```

Make the file executable:
```

chmod +x hplip-3.18.6.run
```

Execute:
```

./hplip-3.18.6.run
```

 Follow the steps.

4. Install the hp-plugin if it is not installed after the above steps:
Then run:
```

hp-plugin
```

 Follow the steps. && Good Luck

---

