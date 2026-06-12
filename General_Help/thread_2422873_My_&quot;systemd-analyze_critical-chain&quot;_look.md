---
title: "My &quot;systemd-analyze critical-chain&quot; looks like this. Is it normal?"
date: 2019-07-14
forum: General Help
---

### Post by pranav.bhattarai on 2019-07-14
```
pranav@inspiron-5548:~$ systemd-analyze critical-chain
The time after the unit is active or started is printed after the "@" character
The time the unit takes to start is printed after the "+" character.
graphical.target @54.230s
&#9492;&#9472;multi-user.target @54.230s
  &#9492;&#9472;kerneloops.service @28.129s +219ms
    &#9492;&#9472;network-online.target @28.069s
      &#9492;&#9472;network.target @28.068s
        &#9492;&#9472;NetworkManager.service @24.493s +3.574s
          &#9492;&#9472;dbus.service @24.479s
            &#9492;&#9472;basic.target @24.361s
              &#9492;&#9472;sockets.target @24.360s
                &#9492;&#9472;snapd.socket @24.357s +3ms
                  &#9492;&#9472;sysinit.target @24.267s
                    &#9492;&#9472;apparmor.service @20.465s +3.073s
                      &#9492;&#9472;local-fs.target @20.464s
                        &#9492;&#9472;boot-efi.mount @20.302s +162ms
                          &#9492;&#9472;systemd-fsck@dev-disk-by\x2duuid-8A05\x2dF7D6.servi
                            &#9492;&#9472;dev-disk-by\x2duuid-8A05\x2dF7D6.device @18.253s

```
**Question:** What can I do about?

---

### Post by cruzer001 on 2019-07-14
That output doesn't mean a lot to me.  Mine is different from yours, but I'm running different hardware and software so ofcourse it would be different.  Why are you looking at systemd?  

Slow boot?  If so, how long is it taking?
```
systemd-analyze
```
What hardware are you running?  Install inxi.
```
sudo apt install inxi
```
then run
```
inxi -F
```
if you want to know more about inxi
```
man inxi
```
What snap packages are you running?
```
snap list
```

Or is it something else?  I don't know, your post is a bit vague.

---

