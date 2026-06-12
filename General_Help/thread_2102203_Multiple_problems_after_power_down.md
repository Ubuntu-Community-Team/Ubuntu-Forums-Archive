---
title: "Multiple problems after power down"
date: 2013-01-06
forum: General Help
---

### Post by Statia on 2013-01-06
My girlfriend, who has a force field around her that makes hard disks lose data, computers crash and stops cellphones from working has worked her black magic on my system. Thinking the system was suspended, she pushed the power button, but the system was running with the monitor switched off. I found the system in a half switched off state: no more X, just console with shut-down messages, but no shut-down occurred. I had to use the MagicSysRq to bring the system down.
Since that happened the following things:

- console resolution looks like 640x480 or something, instead of my monitors 1680x1050.
- X runs on vt7 instead of on vt8
- when starting KDE, Kickoff Application Launcher does not work until an error message pops up: 
```
Error launching /home/statia/.kde/Autostart/xscreensaver.desktop. Either KLauncher is not running anymore, or it failed to start the application.
```- klipper and hp-systray have disappeared from the panel
- hp-systray is running (but not visible in the tray) and maxing out one of the CPU cores for a 100%
- the pager in the panel is on the right, while it used to be on the left
- from Kickoff, Shutdown, Restart and Log Out don't work any more.
- My script in ~/.kde/Autostart that maps the Windows key to F13 to use that as start button is no longer executed
- The scipt doesn't work any more when manually executed. It uses xmodmap
- No Plymouth when booting

The only way now to log out, restart or shut down is to use ctrl-alt-backspace (though I think before this happened that was disabled).
I know it should be possible to do something with the console resolution from the grub menu, unfortunately this menu comes up only about once in twenty boots or so by pushing the right shift key.

I want my working system back!
(And my girlfriend has been forbidden to ever touch the power switch again...)

Edit: log out works again.
Edit: now that log out works again, panel settings remain after manually restoring them
Edit: reboot / shut down works again
Edit: X back on vt7
Edit: put GRUB_GFXPAYLOAD_LINUX=1680x1050 in /etc/default/grub and ran update-grub. No result.

---

### Post by Statia on 2013-01-09
OK, most is fixed now, besides:

- console resolution looks like 640x480 or something, instead of my monitors 1680x1050.

How to get my console back in to high resolution?

---

### Post by Statia on 2013-01-10
Oh yeah, and the Plymouth screen is not showing any more. Already reinstalled, to no avail.

---

### Post by Statia on 2013-01-16
bump

---

### Post by Statia on 2013-01-26
bump

---

### Post by oldfred on 2013-01-26
Is it grub mode or system video?

With grub I thought it was this:
       Use this with your monitor size in /etc/default/grub:
GRUB_GFXMODE=1024x768
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/454993](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/454993)

    
If system what video chip do you have?

---

### Post by Statia on 2013-01-26
```
# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1680x1050x24
```

Nvidia GT430

---

### Post by oldfred on 2013-01-26
That should give you video in grub menu, but you then have to install the nvidia drivers in your install. Did you originally install from nVidia. You then have to reinstall on every kernel update. If you use the Ubuntu standard versions of nVidia driver it should update automatically.

---

### Post by Statia on 2013-01-27
I use the Ubuntu-supplied drivers, but the experimental one, 310-14.
But again: everything used to work, until my gf messed with the power button of my PC.
Now graphics mode on terminal is hosed, Plymouth gone and xmodmap no longer works.
All other symptoms I initially described have been fixed one way or the other.

---

### Post by oldfred on 2013-01-27
Power down almost always is the major cause of file corruption.  Have you run fsck on your system partition?

       #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

