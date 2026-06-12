---
title: "extremely slow boot"
date: 2021-02-28
forum: General Help
---

### Post by cmcanulty on 2021-02-28
My dell desktop booted in less than 30 seconds in 18.04 but now takes over 2 minutes. Once it boots things run at normal speed. I am pasting below the code output. But I don't know how to fix the really slow loading items or if there is a safe way to speed them up. Thank you

```
sudo systemd-analyze critical-chain
The time when unit became active or started is printed after the "@" character.
The time the unit took to start is printed after the "+" character.

graphical.target @30.436s
&#9492;&#9472;multi-user.target @30.436s
  &#9492;&#9472;postfix.service @30.434s +1ms
    &#9492;&#9472;postfix@-.service @20.734s +9.697s
      &#9492;&#9472;network-online.target @20.671s
        &#9492;&#9472;NetworkManager-wait-online.service @14.802s +5.868s
          &#9492;&#9472;NetworkManager.service @11.005s +3.795s
            &#9492;&#9472;dbus.service @11.002s
              &#9492;&#9472;basic.target @10.967s
                &#9492;&#9472;sockets.target @10.967s
                  &#9492;&#9472;snapd.socket @10.950s +1ms
                    &#9492;&#9472;sysinit.target @10.811s
                      &#9492;&#9472;snapd.apparmor.service @10.484s +325ms
                        &#9492;&#9472;apparmor.service @9.700s +782ms
                          &#9492;&#9472;local-fs.target @9.699s
                            &#9492;&#9472;home.mount @9.611s +87ms

```

---

### Post by VMC on 2021-02-28
You might temporarily stop the mail service 'postfix' and reboot to see if it improves.

---

### Post by CatKiller on 2021-02-28
The default timeout when starting or stopping a service is 90 seconds. You could either see which service is stalling at boot and fix it, or make that timeout period shorter.

---

### Post by HermanAB on 2021-02-28
Well, why boot?  Suspend is much faster.

---

### Post by cmcanulty on 2021-02-28
I eliminated  a few services at boot but still takes over 2 min. This same machine in 18.04 booted in <30sec

---

