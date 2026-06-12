---
title: "fstab doesn't automount"
date: 2015-12-10
forum: General Help
---

### Post by kooldino on 2015-12-10
Running Kubuntu 15.10

I have the following in my fstab:

```
# Mount synology drive
# Requirements:
#  sudo apt-get install cifs-utils
#  Must have a credentials file: /home/dino/scripts/.smbcredentials
#  synology IP address must be 192.168.0.199
#  /media/europa must exist on local device with proper permissions set

//192.168.0.199/homes/kooldino  /media/europa cifs credentials=/home/kooldino/scripts/.smbcredentials,iocharset=utf8,sec=ntlm  0  0

```

When i boot the machine, it does not automount the NFS share.  If I try to access the share via Dolphin, it tells me
```

An error occurred while accessing 'homes/kooldino on 192.168.0.199', the system responded: mount: only root can mount //192.168.0.199/homes/kooldino  on /media/europa

```

If I do a sudo mount -a, everything works just fine.

Permissions for /media are default.  I tried changing them to 777 and it didn't help.

Permissions for /media/europa are 777

I'm really confused.  Why doesn't this automount on boot?

---

### Post by deadflowr on 2015-12-10
Is /homes the correct location?

---

### Post by kooldino on 2015-12-10
Yes.  Since it mounts just fine when I do a "sudo mount -a", it shows me that the contents of fstab are right...it's just some kind of odd permissions issues.

---

### Post by steeldriver on 2015-12-10
Is /home/kooldino/scripts/ available at boot time? (it wouldn't be if you have an encrypted home dir for example)

---

### Post by kooldino on 2015-12-10
It's not encrypted as far as I know.  

I put the username and password directly into the fstab file and it still won't automount at boot time.  That eliminates the external credentials file as the culprit.

---

### Post by kooldino on 2015-12-13
Bump

---

### Post by steeldriver on 2015-12-13
Any relevant error messages in the logs?

```

dmesg | grep mount

```

---

### Post by kooldino on 2015-12-13
```
mesg | grep mount
[    1.286373] EXT4-fs (sda4): mounted filesystem with ordered data mode. Opts: (null)
[    1.430114] systemd[1]: Set up automount Arbitrary Executable File Formats File System Automount Point.
[    1.531173] EXT4-fs (sda4): re-mounted. Opts: errors=remount-ro
[    1.798312] EXT4-fs (sda2): mounting ext2 file system using the ext4 subsystem
[    1.799953] EXT4-fs (sda2): mounted filesystem without journal. Opts: (null)
[    2.301198] CIFS VFS: cifs_mount failed w/return code = -101

```

Google says this about the 101 code...

[http://www.linuxforums.org/forum/ubuntu-linux/178251-cifs-vfs-cifs_mount-failed-w-return-code-101-a.html](http://www.linuxforums.org/forum/ubuntu-linux/178251-cifs-vfs-cifs_mount-failed-w-return-code-101-a.html)

So should I just put a "sudo mount -a" in my /etc/rc.local file?

---

### Post by kooldino on 2015-12-16
Bump

---

### Post by ian-weisser on 2015-12-16
The link you posted seemed to explain the problem pretty clearly.
It's a *network* filesystem, not a local storage device.
At 2.3 seconds after poweron, the network is not yet available.

In fstab, you can specify noauto for CIFS filesystems. You can still use shorthand to refer to them using 'mount', but the system will no longer try to automount them at the wrong time (waste of time and resources during boot).

One solution is to create a systemd (root) task that will mount the network share after the network is up.
Another solution is to create a Upstart (user) job that will mount the network share afer you login.
Another solution is to script the mount in your (user) autostart folder.

For user-level solutions, you might need to edit the sudoers file, so your script can 'sudo mount' without prompting for a password.
Or trigger a root script to do the mount using dbus or another clever way.

---

### Post by steeldriver on 2015-12-16
Another option might be to use autofs, so that it mounts the first time the user attempts to access it

I've done in the past that to mount an NFS home share from my NAS - I think it should work for cifs as well

---

### Post by kooldino on 2015-12-20
Those all sound like great solutions, but how do i do them?

---

### Post by ian-weisser on 2015-12-20
You mark your CIFS mount 'noauto'
Then you review all the options in Posts #10 and #11.
Then you make a tentative decision.
Then you learn how to implement your chosen solution. If, during the learning process, you conclude it's the wrong solution for you, then you change your decision.

There are an astonishingly large number of online resources to teach you how to master Upstart, systemd, autofs, and the other options.
We will happily share our favorites if you tell us which approach you want to try first.

---

