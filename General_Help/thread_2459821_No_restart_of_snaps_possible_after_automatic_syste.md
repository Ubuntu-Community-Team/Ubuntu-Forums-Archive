---
title: "No restart of snaps possible after automatic system reboot of Ubuntu-core"
date: 2021-03-26
forum: General Help
---

### Post by geojanbv on 2021-03-26
Hi there,

I'm new in the world of Ubuntu and I hire a free-time Ubuntu developer working on an IoT energy blockchain project.
The challenge is to build a robust application on Ubuntu-core that can trade solar energy using blockchain technology.
I like the Ubuntu-core platform very much but we can't find a solution for automatic restart of the application after unattended system reboot.

The blockchain snaps we use now are: bitcoin-core and energycoind

With Ubuntu-desktop we are able the automatic restart with:

```
[COLOR=#000000][FONT=Helvetica][FONT=Menlo]$ sudo nano /etc/systemd/system/ENRG.service[/FONT][/FONT][/COLOR]

```[COLOR=#000000][FONT=Helvetica]```
[COLOR=#2FB41D][FONT=Menlo]**[Unit]**[/FONT][/COLOR]
[FONT=Menlo]**Description=EnergyCoin blockchain service**[/FONT]
[FONT=Menlo]**After=network.target**[/FONT]
[FONT=Menlo]**StartLimitIntervalSec=0**[/FONT]
[COLOR=#2FB41D][FONT=Menlo]**[B][Service]**[/B][/FONT][/COLOR]
[FONT=Menlo]**[B]Type=simple**[/B][/FONT]
[FONT=Menlo]**[B]Restart=always**[/B][/FONT]
[FONT=Menlo]**[B]RestartSec=1**[/B][/FONT]
[FONT=Menlo]**[B]User=geojanbv**[/B][/FONT]
[FONT=Menlo]**[B]ExecStart=/usr/bin/env energycoind -daemon**[/B][/FONT]
[FONT=Menlo]****[/FONT]
[COLOR=#2FB41D][FONT=Menlo]**[B][B][Install]**[/B][/B][/FONT][/COLOR]
[FONT=Menlo]**[B][B]WantedBy=multi-user.target**[/B][/B][/FONT]

```

```

[FONT=Menlo]**[B][B]sudo systemctl enable ENRG**[/B][/B][/FONT]

```

But this is not working on Ubuntu-core!

I hope on positive feedback so that we can build an application for energy trading.

Have a nice day,
Jan Clement
More info about the project: [https://bitcointalk.org/index.php?topic=1028941.msg56403331#msg56403331](https://bitcointalk.org/index.php?topic=1028941.msg56403331#msg56403331)

[/FONT][/COLOR]

---

