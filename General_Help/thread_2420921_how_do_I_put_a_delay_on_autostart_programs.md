---
title: "how do I put a delay on autostart programs?"
date: 2019-06-13
forum: General Help
---

### Post by ardouronerous on 2019-06-13
I'm running Lubuntu 18.04.

I placed Software Updater within [FONT=system]/.config/autostart/[/FONT] so every time I booted my machine, Software Updater would start and update my system, but I'm getting a problem at startup though, there seems to be a 10 second delay on connecting to my WIFI and so Software Updater would fail, making me click on try again when the WIFI is connected.

So, I'd like to put a 15 second delay on Software Updater autostarting, how can I do this?

Thanks.

---

### Post by ajgreeny on 2019-06-13
I do not use Lubuntu and have forgotten all I knew back when I tried it, but you probably need to change the command used in the autostart  system to something similar to **sleep 15; update-manager**, using whatever the updater command really is.

---

### Post by yetimon_64 on 2019-06-13
> **ardouronerous said:**
> ....

So, I'd like to put a 15 second delay on Software Updater autostarting, how can I do this?

Thanks.
Write a simple bash script and store it in your home folder, eg in /home/$USER/bin/. Give it a name you can then use in the [FONT=system]~/.config/autostart file.[/FONT]
In that script include a 15 second sleep command then the command to initiate the software updater.

As an example I use Xubuntu 18.04 and in the startup list I have an entry that calls a script in my $HOME/bin folder called "DPMS_OFF-startup". This script shown in the next code box uses a 20 second delay on startup then it turns off all DPMS settings so I have no screen blanking or monitor turning off occurring in the new session.
```
#!/bin/bash

sleep 20 && \
xset s 0 0; xset s noblank; xset dpms 0 0 0; xset -dpms;

exit 0
```
I don't know the exact command you use with the software updater but changing the above script to 15 seconds and replacing the xset commands line above to that for the software updater should work for you. Whatever you call the script is what you call with the autostart file entry. The location $HOME/bin should be in your users system path so this idea should work ok for your needs.

Regards, yeti.

Edit: ninja'd by ajgreeny :-)

---

### Post by ardouronerous on 2019-06-13
Hi, after searching the forums further, I've found this solution: [https://ubuntuforums.org/showthread.php?t=2327423&p=13502344#post13502344](https://ubuntuforums.org/showthread.php?t=2327423&p=13502344#post13502344)

```
Exec=sh -c "sleep 15 && /usr/bin/update-manager"
```

It works!

---

