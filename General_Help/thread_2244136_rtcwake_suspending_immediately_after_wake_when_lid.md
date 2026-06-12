---
title: "rtcwake suspending immediately after wake when lid is closed"
date: 2014-09-13
forum: General Help
---

### Post by quadrplax on 2014-09-13
I have a server which I do not want running overnight. For this I use rtcwake in crontab. I believe it used to work, but now it just stays suspended. It turns off perfectly fine though. I did a test via PuTTY: "sudo rtcwake -m mem -s 15". After the 15 seconds it woke up, stayed on for about 5 seconds, then suspended again. If I turn it on during the time it's asleep, it doesn't turn auto re-suspend. The server is a laptop on a docking station, and this only happens if the lid is closed. If I close the lid while it is on, it doesn't suspend. If I turn it on while the lid is closed (via docking station button or WOL), it doesn't suspend. This is only an issue with rtcwake. I've changed some settings in various places to make it work the way it does now (ignoring lid close). Any clue as to how I can fix this?

---

