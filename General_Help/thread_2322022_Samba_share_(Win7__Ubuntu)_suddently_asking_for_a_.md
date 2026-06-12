---
title: "Samba share (Win7 / Ubuntu) suddently asking for a non-existent password. What to do?"
date: 2016-04-25
forum: General Help
---

### Post by 777funk on 2016-04-25
My wife's Win7 machine is the host to our home network's printers. Suddenly it's asking for a username and password to reach this share. Neither her nor I have changed any network settings. Where do I begin to look?

---

### Post by 777funk on 2016-04-26
to the top. Anyone else have this problem?

---

### Post by 777funk on 2016-04-26
I've even copied the parameters from an:
/etc/samba/smb.conf

file on the Home Theater machine on the network with the same Xubuntu version (which works) and still not working on my main machine.

---

### Post by 777funk on 2016-04-27
I guess we have major crickets chirping on this one. Must be either a common issue/bug or one not easily solved.

One more bump please.

---

### Post by 777funk on 2016-04-28
[IMG]http://scienceblogs.com/startswithabang/files/2013/10/FieldCricket.png[/IMG]

Anyone have a suggestion? Thanks in advance!

---

### Post by Morbius1 on 2016-04-28
Try passing "guest" when you access the printer. See item #14 in this bug report: [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1572876](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1572876)

---

### Post by bswarm2 on 2016-04-28
Check Windows firewall. I had mine turned off because I have a hardware firewall, but Windows turned it back on (after an update?) causing my file and printer shares to start asking for non existent credentials.

---

### Post by 777funk on 2016-04-28
Thanks Morbius1 and bswarm2. 

I will check the firewall on Windows. I don't think this is it though because I can reach the Win7 computer from a nearly identical (to my machine) Ubuntu machine on the network. And to Morbius, it's not just cups (printing shares), it's all network shares on the Win7 computer that are unreachable (and after about 2 minutes asking for a password) from my Xubuntu machine.


EDIT: I just noticed this error when I open the smb.conf file:

> ** (gedit:27827): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-1RBWBKSuxj: Connection refused

(gedit:27827): IBUS-WARNING **: The owner of /home/nick/.config/ibus/bus is not root!

---

### Post by Morbius1 on 2016-04-28
Accessing Windows file shares as guest is pretty much broken since samba was updated to 4.3.8.

You need to do a manual cifs mount and pass the user guest there as well: [http://ubuntuforums.org/showthread.php?t=2321029&p=13474661#post13474661](http://ubuntuforums.org/showthread.php?t=2321029&p=13474661#post13474661)

---

### Post by 777funk on 2016-04-28
Ahhh! It's a bug. Makes sense now. I did an apt-get upgrade (instead of update) a few days ago. I think that's what broke my system. Any way to go back to the earlier samba?

It's a real bummer since I can't print to the network nor reach the other computer when needed. It's almost enough to force me to return to MS Win although I've really grown to love Linux since 2012.

---

### Post by Linuxisfast on 2016-04-28
Samba is working fine in Arch that uses latest package. If you have updated to 16.04, libpam-smbpass is not supported. Edit your samba password with sudo pdbedit -a -u user(your name originally used to access) and set a password and restart smbd.service and nmbd.service

---

### Post by 777funk on 2016-04-29
Found my solution here:
[https://forums.linuxmint.com/viewtopic.php?f=157&p=1159792#p1159792](https://forums.linuxmint.com/viewtopic.php?f=157&p=1159792#p1159792)
Post #14-ish by xenopeek

```

sudo aptitude install samba-libs=2:4.1.6+dfsg-1ubuntu2  libsmbclient=2:4.1.6+dfsg-1ubuntu2 libwbclient0=2:4.1.6+dfsg-1ubuntu2  python-samba=2:4.1.6+dfsg-1ubuntu2 samba=2:4.1.6+dfsg-1ubuntu2  samba-common=2:4.1.6+dfsg-1ubuntu2  samba-common-bin=2:4.1.6+dfsg-1ubuntu2  samba-dsdb-modules=2:4.1.6+dfsg-1ubuntu2  samba-vfs-modules=2:4.1.6+dfsg-1ubuntu2 smbclient=2:4.1.6+dfsg-1ubuntu2  libldb1=1:1.1.16-1 python-ldb=1:1.1.16-1

```

After direction from Morbius on this bug:
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1572876](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1572876)

This was the first of the two links provided with solutions.

---

### Post by 777funk on 2016-05-01
Ahhhh... oh no! It's broken again. The fix was good for a day. Now I'm getting the bogus authentication bugs again. This is a real head scratcher.

---

### Post by 777funk on 2016-05-02
Anyone have any other suggestions?

---

