---
title: "/etc/init.d/gdm missing and, when found, totally screwed up"
date: 2008-07-02
forum: General Help
---

### Post by acambre on 2008-07-02
I am running Ubuntu 8.04. I have gnome installed. The GDM package verison 2.20.6-0 is currently installed per aptitude.

Despite this, there is no **gdm** inside /etc/init.d.

I've tried reinstalling the gdm package using **sudo apt-get install --reinstall gdm**. I've also tried downgrading to 2.20.4 via Aptitude and later going back to the current version, but neither worked.

According to [http://packages.ubuntu.com/hardy/i386/gdm/filelist](http://packages.ubuntu.com/hardy/i386/gdm/filelist), /etc/init.d/gdm is definitely supposed to exist.

So I download the gdm_2.20.5-0ubuntu3_i386.deb package manually and (.5 was the latest listed at packages.ubuntu.com), and extracted all files using **dpkg-deb -x gdm_2.20.6-0ubuntu3_i386.deb x** (using a directory named x in my home directory), and copied ~/x/etc/init.d/gdm to /etc/init.d. Now when I run gdm, I get this nonsense:
```
gdm[9641]: WARNING: GDM file gdm-daemon-config.c: line 2033 (): Cannot run seteuid to 0: Operation not permitted
GDM file gdm-daemon-config.c: line 2033 (): Cannot run seteuid to 0: Operation not permitted
gdm[9641]: GLib-GObject-CRITICAL: g_object_unref: assertion `G_IS_OBJECT (object)' failed
```

If I run gdm as root, I get no output.

And here's something even more strange: if I run sudo gdm restart as root:
[LIST=1]
[*]the first time I run it, I get no output
[*]the second time I run it, I get this nonsense:
```
gdm[9696]: WARNING: GDM already running. Aborting!
GDM already running. Aborting!
gdm[9696]: GLib-GObject-CRITICAL: g_object_unref: assertion `G_IS_OBJECT (object)' failed

```
[*]the third time, I get no output
[*]the fourth time, I get the above nonsense
[*]...
[/LIST]

What is going on with this system?

In case it matters, this was originally a Ubuntu 8.04 server install, and I installed the UI using apt-get ubuntu-desktop.

My ultimate goal is to get VNC working per [https://help.ubuntu.com/community/VNC#Tightvncserver%20Server%20with%20Login%20Screen%20Via%20GDM](https://help.ubuntu.com/community/VNC#Tightvncserver%20Server%20with%20Login%20Screen%20Via%20GDM) (well, actually per [http://ubuntuforums.org/showpost.php?p=4963842&postcount=1](http://ubuntuforums.org/showpost.php?p=4963842&postcount=1)) so I can have a GUI administration console to complement the terminal.

---

