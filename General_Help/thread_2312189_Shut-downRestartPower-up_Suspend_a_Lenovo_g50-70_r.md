---
title: "Shut-down/Restart/Power-up Suspend a Lenovo g50-70 running  15.10"
date: 2016-02-02
forum: General Help
---

### Post by athan2 on 2016-02-02
As the title suggests; when it comes to *shut-down/restart* both suspend the laptop unless I go with ```
sudo poweroff
```or```
sudo reboot
``` which work as expected. When *powering-up*,  it goes through the GRUB (since I'm dualbooting), and then the MATE  loader appears. Seconds later the laptop is suspended. A mouse-click  will then prompt me to the account-password interface, and after  entering the password, another suspend. This often happens a third time,  but it seems random. MATE updated today (see below) and since then the laptop only runs through the advanced GRUB options (Ubuntu with linux 4.2.0-27-generic, otherwise gets stuck in a "lit" black screen), and now goes into suspend at least 6 times till I reach the desktop.  In addition, no wireless networks would show up (post-update)- this resolved by ```
sudo apt-get install bcmwl-kernel-source
```

  
[LIST]
[*](status installed) linux-image-4.2.0-27-generic:amd64 4.2.0-27.32 
[*]linux-image-extra-4.2.0-27-generic:amd64 4.2.0-27.32 
[*]linux-image-generic:amd64 4.2.0.27.30 status 
[*]linux-headers-4.2.0-27:all 4.2.0-27.32 
[*]linux-headers-4.2.0-27-generic:amd64 4.2.0-27.32 
[*]linux-headers-generic:amd64 4.2.0.27.30 
[*]linux-generic:amd64 4.2.0.27.30 
[*]linux-signed-image-4.2.0-27-generic:amd64 4.2.0-27.32 
[*]linux-signed-image-generic:amd64 4.2.0.27.30 
[*]linux-signed-generic:amd64 4.2.0.27.30 
[*]linux-libc-dev:amd64 4.2.0-27.32 
[/LIST]

*03/02/16* Haven't applied any changes since last update.  Third power-up attempt and what seems to be random now is actually  booting (took ~30mins of *-loading-suspend-"lit" black screen-*  loops). I pressed the power-off button while stuck in a black screen and  for a while some commands appeared including something about **ascii [OK]** and **failing to start login service**  (didn't have enough time to note more than that before getting into  another black screen). The web connectivity also drops from time to  time, while my other devices have proper access.
  
Ideas? :)

---

