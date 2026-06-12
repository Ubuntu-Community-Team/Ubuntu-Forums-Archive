---
title: "I thought my systemd service should only run at boot time?"
date: 2020-06-03
forum: General Help
---

### Post by desconocido on 2020-06-03
I thought my systemd service (in Ubuntu Mate 16.04; to turn off Bluetooth at boot time) should only run at boot time?

I wrote a systemd service to turn off Bluetooth at boot time. See
[https://ubuntuforums.org/showthread.php?t=2363212]("https://ubuntuforums.org/showthread.php?t=2363212")

I did it because I hardly ever use bluetooth, don't want to be tracked by bluetooth scanners but still wanted to be able to turn it on via the Bluetooth top panel applet icon if necessary.

It turns bluetooth off nicely at boot time and I thought I had tested that turning it on manually worked.

Recently I got some bluetooth speakers and I tried connecting to them.

But every time I turned bluetooth on, it turned off again (after about ten seconds) and the logs show that it was my service doing the turning off.

(What confused me more was that the first day I tried connecting, I managed to connect to the speakers long enough to play a couple of symphonies - it's only since the weekend that bluetooth always turns itself off.)

Have I misunderstood? I thought the service would just run once at boot time. Do I have to specify something else?
This is the service:

```
[Unit]
Description=Service to always turn bluetooth off at system start time
After=NetworkManager.service
Before=network-online.target

[Service]
ExecStart=/usr/local/bin/turn-bluetooth-off.sh

[Install]
WantedBy=default.target
```

---

### Post by webaake on 2020-06-03
[Service]
Type=oneshot

---

### Post by desconocido on 2020-06-03
> **webaake said:**
> [Service]
Type=oneshot

Thanks. That seems to do the trick. Now listening to Bob Marley.

---

### Post by desconocido on 2020-06-03
> **desconocido said:**
> Thanks. That seems to do the trick. Now listening to Bob Marley.

I spoke too soon. Turning Bluetooth off manually and then trying to turn it on again manually leads to the service being invoked to turn it off.

---

### Post by desconocido on 2020-06-04
I tried adding

```
Restart=no
```

to the service section but with no luck.

---

### Post by desconocido on 2020-06-17
OK, I have found a workaround. I have just realised that the Bluetooth setting (on or off) at shutdown is preserved at the next boot up. So I don't need my service at all. Smiley face.

The vanilla Bluetooth doesn't work too well, but I can live with that.

---

