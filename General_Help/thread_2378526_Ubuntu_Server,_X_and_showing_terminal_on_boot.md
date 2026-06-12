---
title: "Ubuntu Server, X and showing terminal on boot"
date: 2017-11-24
forum: General Help
---

### Post by herbion on 2017-11-24
Hi, I'm fairly newly to ubuntu however, I'm been using linux as a hobby for some time now.

Recently, I'm trying to play around with ubuntu server.

What I'm trying to achieve is this:

I'm trying to start X server on boot, but to show the terminal screen.

Everything installed fine, and I start my X server by editing the /etc/rc.local file and adding:

X :0
sleep 5
export DISPLAY=:0
exit 0

computer boots up fine and I'm being shown a blank screen on boot which is I assume is normal as I do not have any desktop environment installed nor desktopmanager.
checking the Xorg.0.log file, there's no error shown.

What I want is to have X running and show me a terminal instead of a blank screen.  I can get to terminal by presing ctrl+alt+f1 but I want it to happen on boot.

Any help is greatly appreciated.

---

### Post by irv on 2017-11-29
Have you ever thought about running a headless server, Headless, in this context, basically means that the computing device has no monitor or peripherals, such as a keyboard and mouse. I do this on my server. I remote into it and do all from my laptop. Using a terminal you can do this using the command:```
sudo ssh username@servername

``` you can use the server's IP address as well.
To do file transfers I use Filezilla. This works great for me and makes it easy to maintain my server.

---

