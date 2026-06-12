---
title: "SSH Connections"
date: 2013-01-14
forum: General Help
---

### Post by Stephan H on 2013-01-14
Hello,

Just as this has developed into a slightly different topic: It's the continuation of [http://ubuntuforums.org/showthread.php?t=2094432](http://ubuntuforums.org/showthread.php?t=2094432)

I've setup a SSH server on a machine running on Kubuntu 12.04 LTS.
There are two main issues remaining now:

1. access restrictions: Currently all three authorised users (as specified in sshd_config) can access each other's /home/<user> directory.
There is a second HDD with three partitions on it. I'd like to move /home/<user> to each assigned partition and restric access for each user to his own partition. How would one do this?

2. Accessing via SSH:
- from a WinXP machine (net): Tried Putty which does open a terminal session (all in /home/<user>). But can't access a user's desktop nor can I access files in Win Explorer (e.g. via mapping a new drive).
- from another Kubuntu machine (LAN): Can access terminal and all folders in /home/<user>, using fish://... or sftp://... in Dolphin or Nautilus- no problem.
But how can one open a desktop session? Remmina just wouldn't connect when I use 'VNC'. It does open a terminal again though.

Does anyone have any ideas?

Stephan

---

### Post by LewisTM on 2013-01-14
1. You can setup a chroot jail for your users that will restrict them to their home directory and allow them to run only a subset of commands when logged in. Here's a nice tutorial
[http://www.howtoforge.com/chrooted-ssh-sftp-tutorial-debian-lenny](http://www.howtoforge.com/chrooted-ssh-sftp-tutorial-debian-lenny)
Personally, I would just run 
```
sudo chmod 700 /home/<user>
``` so that each home directory can only be accessed by its owner. It may still be a good idea to move each home directory to its own partition but that's hardly necessary for security.

2. You can use FileZilla or WinSCP to access remote files by SFTP in Windows. You cannot map a remote SFTP server to a drive letter in Windows. You cannot access the remote desktop with SSH alone. You need to setup a VNC (or NX, X2Go, RDP) server first on that machine. What you can do is run X applications remotely through SSH with a X11 tunnel (-X parameter).

Cheers!

---

### Post by SeijiSensei on 2013-01-14
> **Stephan H said:**
> [noparse][FONT="Comic Sans MS"][/noparse]

Please stick to the default font unless you have a specific reason for using something else.

> 1. access restrictions: Currently all three authorised users (as specified in sshd_config) can access each other's /home/<user> directory.
There is a second HDD with three partitions on it. I'd like to move /home/<user> to each assigned partition and restric access for each user to his own partition. How would one do this?

You don't need to give users separate partitions.  In fact this would be a problem if one user has a lot of files and needs more space than another.  

To ensure that users can only see their own directories, make sure that /home/user has 700 permissions.  Then only the user can read and write files in his or her directory.  

```
cd /home
chmod 700 *

```

If you want to move all the home directories to the other drive, create a single partition and and mount it as /home like this:

1)  Format the other drive with ext4.  Use Applications > System > "Partition Editor" to create a single partition on the drive, then format it with ext4.  You should end up with a single filesystem on device /dev/sdb1.

2)  Mount the drive in a temporary location like /mnt and copy the existing /home over with rsync like this:

```

sudo mount /dev/sdb1 /mnt
cd /home
sudo rsync -av . /mnt

```

Now edit /etc/fstab as root with sudo and add the line:

```
/dev/sdb1 /home ext4 defaults 0 0
```

I recommend using nano as the editor with the command "sudo nano /etc/fstab".  Nano uses "control" characters that are represented with a tilde.  For instance, ^X means to hold down the Ctrl key and type X.  That will exit the nano editor.

Now when you reboot, the users' home directories will be on the new drive.  If everything works correctly, you can reboot into recovery mode, choose the option to get a root shell, and run the commands:

```

mount -o remount,rw /
umount /home
cd /home
rm -rf *
reboot

```

This will remove the old home directories from the primary filesystem.

Note that there is no security-based reason for doing this.  I only suggest it if you want to use the second hard drive to hold the users' data.  

> 2. Accessing via SSH:

SSH is primarily designed to operate in text mode.  You can use "ssh -X user@host" to create an X tunnel to the remote machine.  Then if you run an X application on the remote, the output will display on the client.  Try this:

```

[you@client]$ ssh -X you@your.ssh.server
[you@remote]$ firefox &

```

The Firefox browser window should now appear on the client's desktop.

---

### Post by Stephan H on 2013-01-15
Hello,

Thanks for zour help. Much appreciated.
I got one step further I guess (pls see answers below):

> **SeijiSensei said:**
> Please stick to the default font unless you have a specific reason for using something else.


Sorry. The default font appeared quite small to me in the preview and the letters were quite condensed. The intention was to make it easier to read. I used a relatively small laptop, maybe that's why it appeared like this.

--- snip ---

> SSH is primarily designed to operate in text mode.  You can use "ssh -X user@host" to create an X tunnel to the remote machine.  Then if you run an X application on the remote, the output will display on the client.  Try this:

```

[you@client]$ ssh -X you@your.ssh.server
[you@remote]$ firefox &

```

The Firefox browser window should now appear on the client's desktop.

Still working on this one. ```
ssh -X you@your.ssh.server
``` did not work.

Meanwhile I tried to follow the instructions here [https://help.ubuntu.com/community/VNC#accessing-your-pc]("https://help.ubuntu.com/community/VNC#accessing-your-pc") where it is suggested to use a VNC client to connect to an SSH server.
Connection is quite slow, no reliable results yet.
Clients like TightVNC returned a "protocol error" (probably doesn't do SSH), VNCViewer keeps "connecting" for hours (cf. [https://help.ubuntu.com/community/VNC/Clients]("https://help.ubuntu.com/community/VNC/Clients")).


What I'm basically looking for is a remotely accessible user profile on this machine where every user can send own files as a backup but which can also be used as a proxy occasionally.
Should be a GUI and if not a full GUI then at least a graphical file manager interface.
I'm sure Ubuntu would offer this as Windows can via RDC.
Looked into Owncloud.org but it seems limited to just this.

Stephan

---

### Post by SeijiSensei on 2013-01-15
> **Stephan H said:**
> Still working on this one. ```
ssh -X you@your.ssh.server
``` did not work.

I presume you knew to replace "you" and "your.ssh.server" with the appropriate values for your setup. 

One possibility is that there is no X implementation on the remote server.  Both the server and the client need to have X installed to make any of this work.  You might try installing a lightweight desktop environment like [LXDE]("http://lxde.org/") or [XFCE]("http://www.xfce.org/") which will bring along the X libraries.  You can install LXDE by simply running

```
sudo apt-get install lxde
```

To install XFCE instead, replace "lxde" with "xfce4".

---

### Post by lisati on 2013-01-15
> **SeijiSensei said:**
> Please stick to the default font unless you have a specific reason for using something else.

Taken care of

> **Stephan H said:**
> 

Sorry. The default font appeared quite small to me in the preview and the letters were quite condensed. The intention was to make it easier to read. I used a relatively small laptop, maybe that's why it appeared like this.

Not a problem. You can usually use "Ctrl +" or Ctrl+<mousewheel> to make what appears in your browser bigger.

---

### Post by Stephan H on 2013-01-19
> **SeijiSensei said:**
> I presume you knew to replace "you" and "your.ssh.server" with the appropriate values for your setup. 

One possibility is that there is no X implementation on the remote server.  Both the server and the client need to have X installed to make any of this work.  You might try installing a lightweight desktop environment like [LXDE]("http://lxde.org/") or [XFCE]("http://www.xfce.org/") which will bring along the X libraries.  You can install LXDE by simply running

```
sudo apt-get install lxde
```

To install XFCE instead, replace "lxde" with "xfce4".


Brilliant! LXDE works. I can start applications of the other machine on my desktop now.

However, it also got me confused a bit. I rebooted my machine after installing LXDE:
Thought there'd be a choice menue but it went straight into the KDE plasma desktop again (...which is good. But where is the LXDE environment hiding?)
What's the command for the GUI system settings, partition manager etc.? Is there an overview somewhere? I now also installed LXDE on the other machine.
I prefer working in a GUI environment and this is mainly for maintenance purposes as for the NAS function I found a different way: There is a SSH plugin for Firefox. Works fine so far but will yet have to try from a Windows machine and another distribution.

Stephan




Stephan

---

