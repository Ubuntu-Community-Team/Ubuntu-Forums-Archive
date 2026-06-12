---
title: "Enabled Automatic Mount Options, now it won't boot"
date: 2019-09-20
forum: General Help
---

### Post by zarniwoopvannharl on 2019-09-20
I was trying to mount an external drive that it wasn't recognising for some reason. I then went into disk utility, found a drive I thought was that one, went into the mount options for that drive and changed the option for it to use the automatic mount options. This was not the main drive my OS is on, but probably a remnant of the previous one I had or the home directory. I am currently in safe mode trying to revert that setting using the root command prompt.

Using the latest Ubuntu version.

I changed the first option in the Disk Utility menu, under mount options, in what I thought was the ext drive.

So basically what I need is a command to switch off automatic mount options.

Ran:
/# cat /etc/fstab

(...)

/boot was on /dev/sda1 during installation UUID=9762da9f-b9f0-4a9f-9796-ab14d69b3f5f /boot ext4 defaults 0 2

/dev/mapper/ubuntu--vg-swap_1 none swap sw 0 0

And yes, I'm aware this was silly of me. Note to self, never change settings when tired.

---

### Post by coffeecat on 2019-09-20
[Duplicate](https://ubuntuforums.org/showthread.php?t=2427332).

Thread closed.

---

