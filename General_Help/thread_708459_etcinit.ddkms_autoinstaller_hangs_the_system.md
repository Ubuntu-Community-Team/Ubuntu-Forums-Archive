---
title: "/etc/init.d/dkms_autoinstaller hangs the system"
date: 2008-02-26
forum: General Help
---

### Post by clemme on 2008-02-26
Hello there,

I recently installed Ubuntu 7.10 on my fabulous new computer, consisting of

- Shuttle sp35p2
- Asus 8800GT (nvidia card)
- 320GB Samsung disc
- 2GB DDR2-1066 RAM
- Celeron 420 @ 1.60GHz (i know, I'm waiting for a Core 2 duo E8400).

I used the text mode install to be able to create the system on an encrypted LVM.

After the install, I used envy to install the nvidia drivers for my graphics card, and I installed truecrypt by using the .deb package on truecrypt.org. It was working for a couple of days, but now there's trouble in paradise.

On boot:
When the system is done starting all the services, the terminal just shows
"* Starting OpenBSD Secure Shell server sshd      [ OK ]" and a blinking cursor. I can login in using alt+f1 and get a shell.

On shutdown/reboot:
If i issue a "reboot", "shutdown" or "shutdown -h now" it starts to shut down, but never finishes, i have to shut down the computer the hard way.

I tracked it down to the fact that upon bootup and shutdown, a process is hanging, the culprit is:

```

/etc/rc2.d/S20dkms_autoinstaller

```
which is a symlink to
```

/etc/init.d/dkms_autoinstaller

```

I tried to debug this script from the commandline using 

```

root@fido:/etc/init.d# bash -x ./dkms_autoinstaller start
+ test -f /usr/sbin/dkms
+ output_loc=/dev/console
+ '[' -n '' ']'
++ uname -r
+ kernel=2.6.22-14-generic
++ rpm -qf /lib/modules/2.6.22-14-generic
++ grep -v 'not owned by any package'
++ grep kernel
++ head -1

```

It seems that it's hanging at the following line in the file:

```

kernelver_rpm=`rpm -qf "/lib/modules/$kernel" 2>/dev/null | grep -v "not owned by any package" | grep kernel | head -1`

```

And now I am stuck, I have tried to remove the package (dkms) with apt-get, but I can not remove it. I've searched through the forums, googled for it and asked people on my neighborhood #linux irc channel. Has anyone experience this before or have any idea how I can fix this? I would really like to avoid having to reinstall.

Best Regards
Martin

---

### Post by clemme on 2008-02-26
Hi again, I played a bit more around with this, when I run
```
rpm -qf /lib/modules/2.6.22-14-generic
```

manually from a shell this hangs, and has to be killed the hard way (kill -9 PID).

I tried reinstalling it manually with
```
apt-get --reinstall install rpm
```
but that did not have any effect whatsoever :(

---

### Post by clemme on 2008-02-26
(kinda feel like I'm talking to myself ;) )

I did some googling and found out that by deleting the files:
```

/var/lib/rpm/__db.001
/var/lib/rpm/__db.002
/var/lib/rpm/__db.003

```

rpm does not hang anymore, weeeee :) I have no idea what caused this though, it must have been little green men from Mars? :D

---

### Post by LowDepth on 2008-03-09
Hi, happy not to be the only one experiencing that problem. Do you know, what those /var/lib/rpm files were intended for? In my case the actual problem was  I aborted the installation of fglrx-kernel-source so that it obviously could not be added to DKMS build system any more.



Greets

---

### Post by clemme on 2008-03-12
> **LowDepth said:**
> Hi, happy not to be the only one experiencing that problem. Do you know, what those /var/lib/rpm files were intended for?

No, I don't know what they are used for, but I just experienced it again because I had to cut the power when truecrypt made my system lock up. Maybe I should file a bug report somehow?

---

### Post by LowDepth on 2008-03-13
Yup, I think a bug report would be fine. In my case it also was TrueCrypt that crashed my computer -when I tried to copy data. Strange, that it seems just us two to have those problems. In the German Ubuntu forum I´m actually active in was no other incident like this posted.

---

