---
title: "Mosquitto not working on 22.04.03  Error binding unix socket: Permission denied"
date: 2024-01-14
forum: General Help
---

### Post by fableman on 2024-01-14
I can't get **mosquitto  2.0.18**  (or ubuntu's latest version, same error) to work on **Ubuntu 22.04.3 LTS**

Everything is just apt installed.

Using the most simple configuration and trying different ports doesn't matter.

cat /etc/mosquitto/conf.d/mymqtt.conf

allow_anonymous true
listener port 18083



systemctl start mosquitto
Job for mosquitto.service failed because the control process exited with error code.
See "systemctl status mosquitto.service" and "journalctl -xeu mosquitto.service" for details.



cat /var/log/mosquitto/mosquitto.log

1705251695: mosquitto version 2.0.18 starting
1705251695: Config loaded from /etc/mosquitto/mosquitto.conf.
1705251695: Opening unix listen socket on path 18083.
1705251695: Error binding unix socket: Permission denied

Please help, I spent a lot of time reading and trying to find a solution but nothing....

---

### Post by The Cog on 2024-01-14
Are you sure you mean "listener port 18083"? All the examples I have seen just say "listener 1883" or similar - without the word "port". Binding a unix socket seems odd to me, I would expect it to bind a network socket. I wonder if the word port is upsetting it.
Just a guess.

---

### Post by fableman on 2024-01-14
I wrote "[COLOR=#000000]trying different ports doesn't matter."  and I took a port over 1024 to make it easy, port is just a number from 1 to 65535 and ports from 0 - 1024 is dedicated for some services (best practice) , but you can use them as you like..

[/COLOR]

---

### Post by fableman on 2024-01-14
> **The Cog said:**
> without the word "port".

**port** was the error.. omg... I must hade copy some mistyped config and never thought about that..  Thanks alot!

---

