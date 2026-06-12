---
title: "Resuming from hibernation brings up GRUB boot menu but resume works after that"
date: 2022-05-20
forum: General Help
---

### Post by frankvw on 2022-05-20
I've got a weird problem here.

I've got hibernation working on my Dell Inspiron 3576, but when I resume from hibernate the GRUB boot menu is being displayed. I simply select the default option (Ubuntu) or wait for the GRUB menu timeout, and the resume from hibernation continues without any further problems.

In the syslog it says that:
```

May 20 15:30:28 dellfvw systemd[1]: Reached target Sleep.
May 20 15:30:28 dellfvw systemd[1]: Starting Restart Syncthing after resume...
May 20 15:30:28 dellfvw systemd[1]: Starting Hibernate...
```

Based on entry lines, this is where I think the system actually hibernates and the timestamps below don't have the proper time code on it, and the lines below indicate resuming from hibernation:

```
May 20 15:30:28 dellfvw kernel: [20550.861681] PM: Starting manual resume from disk
May 20 15:30:28 dellfvw kernel: [20550.861686] PM: Image not found (code -16)
May 20 15:30:28 dellfvw systemd[1]: Started Restart Syncthing after resume.
May 20 15:30:28 dellfvw systemd-sleep[30868]: Suspending system...
May 20 15:30:28 dellfvw kernel: [20551.394369] PM: hibernation entry
May 20 15:30:28 dellfvw kernel: [20551.413653] PM: Syncing filesystems ...
```

Here's a gap in the time stamps but otherwise the resume seems to proceed normally:

```
May 20 15:38:47 dellfvw kernel: [20552.931122] PM: done.
May 20 15:38:47 dellfvw kernel: [20552.931128] Freezing user space processes ... (elapsed 0.006 seconds) done.
May 20 15:38:47 dellfvw kernel: [20552.937383] OOM killer disabled.
May 20 15:38:47 dellfvw kernel: [20552.937643] PM: Marking nosave pages: [mem 0x00000000-0x00000fff]
May 20 15:38:47 dellfvw kernel: [20552.937647] PM: Marking nosave pages: [mem 0x00058000-0x00058fff]
```

And so on.

The output of sysctl shows a similar picture:

```
May 20 15:30:28 dellfvw systemd[1]: Starting Hibernate...
May 20 15:30:28 dellfvw kernel: PM: Starting manual resume from disk
May 20 15:30:28 dellfvw kernel: PM: Image not found (code -16)
May 20 15:30:28 dellfvw systemd[1]: Started Restart Syncthing after resume.
May 20 15:30:28 dellfvw systemd-sleep[30868]: Suspending system...
May 20 15:30:28 dellfvw kernel: PM: hibernation entry
May 20 15:30:28 dellfvw kernel: PM: Syncing filesystems ...
May 20 15:38:48 dellfvw kernel: PM: done.
May 20 15:38:56 dellfvw kernel: Freezing user space processes ... (elapsed 0.006 seconds) done.
May 20 15:38:57 dellfvw kernel: OOM killer disabled.
May 20 15:38:57 dellfvw kernel: PM: Marking nosave pages: [mem 0x00000000-0x00000fff]
May 20 15:38:57 dellfvw kernel: PM: Marking nosave pages: [mem 0x00058000-0x00058fff]
```

Lots of stuff here, ultimately followed by:

```
May 20 15:39:06 dellfvw kernel: PM: Basic memory bitmaps freed
May 20 15:39:06 dellfvw kernel: OOM killer enabled.
May 20 15:39:06 dellfvw kernel: Restarting tasks ... done.
May 20 15:39:06 dellfvw kernel: PM: hibernation exit
```

I can't find much about the **PM: Image not found (code -16)** error. I've seen several posts where -16 was -22 but in these cases resume failed. According to [this]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1962359") the -16 code means EBUSY which could suggest that the harddisk is not ready or busy when the image is accessed, but why this could be the case I have no idea.

What can I do to further troubleshoot this issue? All suggestions appreciated!

// FvW

---

