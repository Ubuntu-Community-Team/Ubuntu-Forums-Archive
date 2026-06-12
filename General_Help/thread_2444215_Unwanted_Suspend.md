---
title: "Unwanted Suspend?"
date: 2020-05-26
forum: General Help
---

### Post by mikey93898 on 2020-05-26
Hey friends,

Ever since I upgraded to Ubuntu 20.04 (this weekend), my computers are suddenly suspending, and I'm not sure why. Once I put "lock" the screen, or the screensaver locks it, it seems I have roughly 20 minutes until automatic suspend kicks in. This also happens on the gdm3 greeter when no user is logged in.

I'm running XFCE on all machines and believe I have suspend disabled in the XFCE power manager:
[ATTACH=CONFIG]286027[/ATTACH]
 (the "Suspend" is the only dropdown option and I'm unable to change it, but believe setting the sliders to "Never" should be sufficient)

Also in the gdm3 greeter.dconf-defaults file, I have the following in the "Automatic suspend" section, which I thought would disable the greeter from suspending:
```
# Automatic suspend
# =================
[org/gnome/settings-daemon/plugins/power]
# - Time inactive in seconds before suspending with AC power
#   1200=20 minutes, 0=never
# sleep-inactive-ac-timeout=1200
sleep-inactive-ac-timeout=0
# - What to do after sleep-inactive-ac-timeout
#   'blank', 'suspend', 'shutdown', 'hibernate', 'interactive' or 'nothing'
# sleep-inactive-ac-type='suspend'
# - As above but when on battery
# sleep-inactive-battery-timeout=1200
# sleep-inactive-battery-type='suspend'
```

I would like to avoid disabling/masking suspend/sleep in systemd, as I'd still like the ability to issue a sleep command remotely, or via the GUI on occasion.

This all worked fine for the whole time I ran Ubuntu 18 and 19. Any ideas?

---

### Post by mikey93898 on 2020-05-27
Nevermind. As it turns out, the display manager reverted to lightdm for some reason. Manually switching back to gdm3 solved the issue.

Now if I only could get those sweet background images working on the greeter screen

---

