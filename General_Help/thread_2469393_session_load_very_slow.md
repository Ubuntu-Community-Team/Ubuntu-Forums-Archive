---
title: "session load very slow"
date: 2021-11-27
forum: General Help
---

### Post by alain.roger on 2021-11-27
Hi,

I run Ubuntu 21.04 with KDE 5.22.5.
Computer boots quite fast but when it's about user session it's very slow once I type my user password (about 1m30), while several months ago it was about 10s.
I checked with command line "systemd-analyze" and here is the result:
```
[FONT=monospace][COLOR=#000000]Startup finished in 3.271s (kernel) + 7.852s (userspace) = 11.124s  [/COLOR]
graphical.target reached after 7.846s in userspace[/FONT]
```

When I run "systemd-analyze critical-chain", it returns:
```
[FONT=monospace][COLOR=#000000]The time when unit became active or started is printed after the "@" character. [/COLOR]
The time the unit took to start is printed after the "+" character. 

graphical.target @7.846s 
&#9492;&#9472;multi-user.target @7.846s 
  &#9492;&#9472;[COLOR=#ff5454]**teamviewerd.service @7.766s +79ms**[/COLOR][COLOR=#000000] [/COLOR]
    &#9492;&#9472;network-online.target @7.762s 
      &#9492;&#9472;[COLOR=#ff5454]**NetworkManager-wait-online.service @4.362s +3.399s**[/COLOR][COLOR=#000000] [/COLOR]
        &#9492;&#9472;[COLOR=#ff5454]**NetworkManager.service @4.133s +227ms**[/COLOR][COLOR=#000000] [/COLOR]
          &#9492;&#9472;dbus.service @4.130s 
            &#9492;&#9472;dbus.socket @4.119s 
              &#9492;&#9472;basic.target @4.119s 
                &#9492;&#9472;sockets.target @4.119s 
                  &#9492;&#9472;[COLOR=#ff5454]**snapd.socket @4.118s +898us**[/COLOR][COLOR=#000000] [/COLOR]
                    &#9492;&#9472;sysinit.target @4.112s 
                      &#9492;&#9472;[COLOR=#ff5454]**systemd-timesyncd.service @4.015s +96ms**[/COLOR][COLOR=#000000] [/COLOR]
                        &#9492;&#9472;[COLOR=#ff5454]**systemd-tmpfiles-setup.service @3.883s +125ms**[/COLOR][COLOR=#000000] [/COLOR]
                          &#9492;&#9472;local-fs.target @3.876s 
                            &#9492;&#9472;[COLOR=#ff5454]**home.mount @3.785s +90ms**[/COLOR][COLOR=#000000] [/COLOR]
                              &#9492;&#9472;dev-sdb1.device @3.784s[/FONT]
```

But times written are far from what I experience each time I log into system.

When I edited my /etc/systemd/system.conf and uncomment the following lines:
```
#DefaultTimeoutStartSec=90s
#DefaultTimeoutStopSec=90s
```

and write:
```
#DefaultTimeoutStartSec=10s
#DefaultTimeoutStopSec=10s
```

It seems that nothing changed.

---

### Post by VMC on 2021-11-27
Check output of ```
journalctl -b
``` Look for anything suspicious. Also edit out "quiet" and "splash" to see where it hangs up

---

### Post by alain.roger on 2021-11-28
The problem is after login, so I do not understand why editing the grub quiet/splash would change something... Maybe I wrong, so in this case please can you explain me in what such changes could help me ?

---

### Post by VMC on 2021-11-28
You were showing the critical-chain on boot up, so on that note removing quiet,splash might reveal some error while booting.

---

