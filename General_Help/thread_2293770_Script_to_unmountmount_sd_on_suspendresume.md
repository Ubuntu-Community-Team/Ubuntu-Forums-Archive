---
title: "Script to unmount/mount sd on suspend/resume"
date: 2015-09-07
forum: General Help
---

### Post by dhogandrexler on 2015-09-07
Hi there! I have a Dell XPS 13 2015 Developer Edition running 14.04. To augment the small ssd I've installed a 64gb sd card & symlinked some directories to it. It works fine except when I suspend the computer & resume it. Upon resume, the card unmounts and is unable to be mounted again until reboot. It works fine if I manually unmount it before suspending & remount it after resume. From what I've seen in my searching, I should be able to accomplish this with a 'simple' script placed in /etc/pm/sleep.d. However I am a complete noob when it comes to scripting & I was wondering If anyone could help me with a solution =]

The card mounts at /mnt/mmc-SL64G_0x01497fe1-part1/

I found a couple of links with scripts that are close to what I would need, but I'm not sure if they'd work. It looks like this one remounts all devices, but I just need it to mount this specific one: [http://www.laptop-forums.com/threads/sd-card-unmounting-when-suspending.9122/](http://www.laptop-forums.com/threads/sd-card-unmounting-when-suspending.9122/)

The second one looks like it relies on automount to remount it, but that won't work here since the card does not automount on resume:
[http://superuser.com/questions/36296/troubleshooting-failure-to-standby-suspend-with-ubuntu-netbook-remix-on-acer-asp](http://superuser.com/questions/36296/troubleshooting-failure-to-standby-suspend-with-ubuntu-netbook-remix-on-acer-asp)

I also don't know if these apply to ubuntu specifically or how exactly to adapt them to fit this case. Any help on the matter would be much appreciated! Cheers!

---

