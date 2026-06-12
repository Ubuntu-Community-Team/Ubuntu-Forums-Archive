---
title: "Black screen at start up"
date: 2007-06-24
forum: General Help
---

### Post by Makaai on 2007-06-24
Hi everybody, I'm from Italy and I'm a newbie...I talked about this so much in the Italian Community, but we are trying to solve with no results.I explain you.I have an AMD Sempron 1800 GHz, 512 MB RAM and unluckly an Ati Radeon 9200 se...the problem is that at every reboot of the system (after, for example, a night with pc turned off) the logo of ubuntu and loading bar load correctly,than I have a black screen.The curious thing is that to solve this I have to login with the other partition with Windows XP,the reboot, and after this reboot Ubuntu loads correctly.I tryed some things:load open driver and official driver of ATI,change setting in xorg,in so many ways, and then I also unload 3D effect and Desktop effects like bouncing windows or cube workspace,but I got no results.After avery change (only ins me case the change doesn't work correclty) the situation was the same:log off;a long time with pc turned off;at re-start, black screen, so boot with XP, than reboot and correct loading of Ubuntu. So I think the problem is not on graphic card, because after the boot with xp I can see the desktop and everything works correctly.Any help???I'm going mad...

---

### Post by mybunche on 2007-06-24
I have had this happen 4 times  in the last 6 months. Fails to start, just a black screen and the hard drive whizzing. All I had to do is just press the enter key once or a couple of times and it starts. Hasn't bothered me though. 
Maybe yours is different. Hope you find the problem.

---

### Post by akudewan on 2007-06-24
That's really strange. When you get the blank screen, try going to one of the other terminals using Ctrl+Alt+F1 to Ctrl+Alt+F7. If you see the startup messages somewhere, make a note of it, and see if something is stuck. (Maybe a FAT partition running fsck... that can take a long time).

If not, you can login from one of the terminals, and run this command:
```

cat /var/log/boot

```
Thats a log file that has all the boot messages.

If nothing works, then this may be a more serious problem...

---

### Post by Makaai on 2007-06-24
Tomorrow I'll try this...hoping someone will find a solution for my (our) problem...I think it's a problem on Feisty...maybe

---

### Post by Makaai on 2007-06-24
@akudewan

I tried after blackscreen with alt+F2 since now, and it doesn't work.Tomorrow i'll also try that you say..tnx!

---

### Post by Makaai on 2007-06-24
I can say one thing;opening the file of log the response is this:
(Nothing has be logged yet)

---

### Post by Makaai on 2007-06-24
I do some things:i re-installed GDM, formatted th e only partition FAT32 to ntfs.Then my black screen was not solve by booting with windows,i tried so much times but the screen was everytime black.Also nothing appens pushing enter key.Then after some reboot of desperation, "fcsk died with exit status 3" so I edit rcS ans put yes in fcsk and verbose line,than at restart everything loads correctly...what a hell is going on my pc????some one could fix this?:confused:

---

### Post by Makaai on 2007-06-26
i tried to read the logs of the first start (failure) and then of second start (successful) afrter the win boot and reboot.
For the fisrt start that's are the only strange thing I found :

```

...
Jun 26 08:36:51 localhost kernel: No module symbols loaded - kernel modules not enabled.
...
Jun 26 08:36:51 localhost kernel: [   23.002338] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
...
Jun 26 08:36:55 localhost dhcdbd: Started up.
Jun 26 08:36:55 localhost dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jun 26 08:36:55 localhost dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
...
Jun 26 08:36:59 localhost kernel: [   74.676383] [drm] Loading R200 Microcode
Jun 26 08:36:59 localhost kernel: [   74.741673] [drm] writeback test failed
Jun 26 08:37:01 localhost dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
Jun 26 08:37:01 localhost dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Jun 26 08:37:01 localhost dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
...

```

for the second start the _logs are the same_,except for two rows:

```

Jun 26 08:42:27 localhost kernel: [   82.253140] [drm] Loading R200 Microcode
Jun 26 08:42:27 localhost kernel: [   82.253208] [drm] writeback test succeeded in 1 usecs

```

so this is a test that in the first case was failure,but not now...note,in the first case the boot stops at this line (after there is restart line)

```

Jun 26 08:37:12 localhost kernel: [   88.225717] Bluetooth: RFCOMM ver 1.8

```

so,that's it...any help????

---

