---
title: "Blinking cursor after boot"
date: 2008-01-08
forum: General Help
---

### Post by linkenobi on 2008-01-08
Huge problem :confused:

I was playing around trying to get my wii remote to connect to use as a mouse and part of the how-to said to edit the xorg.conf file. So after editing the xorg.conf file i saved and then pressed ctrl+alt+backspace. The screen went to all black and only a blinking cursor was left. I waited a few minutes and tried to shut down or use ctrl+alt+backspace again but it didn't work so i had to hold the button till powerloss. I then started the laptop up again and it booted normally until the point at which the login screen would usually appear just the blinking cursor appeared. I don't know what to do. Anybody have any ideas? This probably has something to do with the xorg.conf file and there is probably a solution on this forum but after hours of searching i couldn't find any. Any help would be greatly appreciated.

Thank you,
linkenobi

---

### Post by PeterJS on 2008-01-08
It's relatively common. Looks like you've picked up on the core of the problem, your xorg.conf is shot. This presents a problem when Xorg (the underlying graphical environment) tries to load. Go a head and log in at the prompt and think of it as one big giant terminal, that's actually the physical console that the terminal is emulating. Once logged in backup you're old Xorg config
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

```
And then have the system generate a new Xorg config:
```

sudo dpkg-reconfigure xserver-xorg

```
Reboot and off you go.

---

### Post by linkenobi on 2008-01-08
> **PeterJS said:**
> It's relatively common. Looks like you've picked up on the core of the problem, your xorg.conf is shot. This presents a problem when Xorg (the underlying graphical environment) tries to load. Go a head and log in at the prompt and think of it as one big giant terminal, that's actually the physical console that the terminal is emulating. Once logged in backup you're old Xorg config
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

```
And then have the system generate a new Xorg config:
```

sudo dpkg-reconfigure xserver-xorg

```
Reboot and off you go.

Thank you but i don't know how to login from the blinking cursor. It doesn't seem to be accepting character input. Any key combination?

---

### Post by PeterJS on 2008-01-08
It's always the details. Ctrl+Alt+F1 to get to the first terminal, I assumed it would drop you there when X failed to load.

---

### Post by linkenobi on 2008-01-08
> **PeterJS said:**
> It's always the details. Ctrl+Alt+F1 to get to the first terminal, I assumed it would drop you there when X failed to load.

i tried pressing that command while it was loading and it sent me to the same screen. it doesn't have options for logging on.Just the black screen with the blinking cursor. I try typing anything in and there is no response.Any other ideas?

Sorry and thanks for the help,
linkenobi

---

### Post by PeterJS on 2008-01-08
You switched to the console while it was loading? You need to wait for X to fail or it will pull you over to it's console when it tries to load.

I also hope you aren't suffering from the console not loading bug as well.

---

### Post by linkenobi on 2008-01-08
> **PeterJS said:**
> You switched to the console while it was loading? You need to wait for X to fail or it will pull you over to it's console when it tries to load.

I also hope you aren't suffering from the console not loading bug as well.


Well I guess I am. Thank you for all the help and could you perhaps lead me in the way to fix this bug?

---

### Post by PeterJS on 2008-01-08
Here's the bug report on it
[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910)
And this seems to be the most complete and active thread
[http://ubuntuforums.org/showthread.php?t=582962](http://ubuntuforums.org/showthread.php?t=582962)

Looks like it's a problem the the console frame buffer and ATI cards. Your best bet would be using recovery mode to get a root shell and fix X from there.

---

