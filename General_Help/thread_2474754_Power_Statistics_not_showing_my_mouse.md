---
title: "Power Statistics not showing my mouse"
date: 2022-05-07
forum: General Help
---

### Post by chaz5698 on 2022-05-07
Hello everyone,

I am on Ubuntu 22.04 lts.
My wireless mouse (Logitech Pro superlight) is not showing in power statistics. I am unsure of what this device below is. I have used uPower as well.
Any suggestions on how I can see the battery life on my mouse?



```
upower --dump
Device: /org/freedesktop/UPower/devices/DisplayDevice
  power supply:         no
  updated:              Sat 07 May 2022 08:14:16 BST (999 seconds ago)
  has history:          no
  has statistics:       no
  unknown
    warning-level:       none
    percentage:          0%
    icon-name:          ''

Daemon:
  daemon-version:  0.99.17
  on-battery:      no
  lid-is-closed:   no
  lid-is-present:  no
  critical-action: HybridSleep
```


[SIZE=3][B]UPDATE:
[/B][Solved]
[SIZE=2]Installing Solaar helped me find my Logitech wireless receiver, I can now see the battery status of my mouse.[/SIZE]
[/SIZE]

---

### Post by chaz5698 on 2022-05-07
Sorry, I am new to forums, but here is the screenshot for Power Statistics

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290409&stc=1[/IMG]

---

