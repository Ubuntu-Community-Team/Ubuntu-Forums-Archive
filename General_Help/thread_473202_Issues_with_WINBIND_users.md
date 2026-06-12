---
title: "Issues with WINBIND users"
date: 2007-06-13
forum: General Help
---

### Post by BevanFindlay on 2007-06-13
Hi,
I am trying to set up Linux boxes on some old hardware we have at our College here for students to use to browse the 'Net and type up documents etc.  We run an almost-solely Windows Active Directory domain, so I am setting up the Linux machines to use WINBIND to use the same logons as they use on the Windows computers.  I have them mostly sorted out, but a few things do not work.  At the moment I am working on either Ubuntu or Kubuntu without any particular preference except that one works.  As I couldn't get anything to connect to the MSN Messenger network under Gnome, but have got it working under KDE, I am thinking Kubuntu at the moment (see [http://ubuntuforums.org/showthread.php?t=459687](http://ubuntuforums.org/showthread.php?t=459687) for that issue).
Anyway, this is what I still need to achieve:

(1) For some reason, sound does not work when I log in as a Windows Active Directory user.  This happens on both Kubuntu and Ubuntu - the volume control icon says "Mixer cannot be found" if I mouseover.  It also happens on a user who is able to sudo, so it seems to be something not being set up rather than a permissions issue.

(2) Is it possible to have it allow the Windows Domain Adminis to be sudoers?  Can this be done by groups somehow?  What about an easy way to do it by individual users?  (This is not so much of a major issue as I can just log on as the local user or manually add that user as a sudoer).

(3) How do I set up a script to create shortcuts and configure the user profiles when they log in?  In particular, I want to put links to server-side folders on the user's desktop, but knowing how to configure their desktop and set up launchers, modify settings, etc would be useful.

(4) Is it possible (on identical hardware, and on non-identical hardware) to replicate a setup exactly without needing to reinstall?  Would [Ghost for Linux]("http://sourceforge.net/projects/g4l") work for this?  What about making a modified install CD so that it includes all my changes?

Thanks in advance,
  - Bevan F.

---

### Post by BevanFindlay on 2007-06-19
Hi,
Does anyone have any suggestions on any of this?

Thanks,
  - Bevan F.

---

### Post by dsent on 2007-06-25
Hi, Bevan.
I'm currently trying to get this whole thing working and had advanced slightly further than you )
The key is to add your mapped domain user to local groups.

I reckon there are at least two ways to do it: the more advanced one via pam_groups.so and the more straightforward - via /etc/group.
I decided do not mess with pam_groups. Simply adding your domain users to /etc/group:
```
audio:x:17:DOMAIN+myuser
cdrom:x:20:DOMAIN+myuser
dialout:x:16:DOMAIN+myuser
etc.
```
will do (considering that winbind is configured well and your winbind separator is '+' - apparently it's better than '\' - I had some nasty issues with latter)

It will probably work with sudoers too - I didn't try it yet.

Also, I think it's possible to add whole domain groups to local groups - I found some traces of it in monstrous-1000-page Samba-HOWTO )) - but I haven't tried it.

On the 3rd issue I only managed to set up home directory autocreating, but there are some settings related with login scripts in Samba - I think it's worth rtfming )))

Furthermore I ran into another issue - automatic media mounting doesn't work with domain user (problem is hal/dbus-related).

Post in this thread, pls if you have anything new on these issues!

**UPDATE:**
I've got rid of mounting problems:
1. Switched to '-' winbind separator instead of '+'. It looks like neither '\' nor '+' are acceptable - each has its own problems related.
2. Created a new group 'plugdev', added root user and my domain user to it:
```
/etc/group:
...
plugdev:!:10059:root,DOMAIN-myuser
...
```
3. Edited /etc/dbus-1/system.d/hal.conf:
changed the first line of the block near the file end:
```
<!-- You can change this to a more suitable user, or make per-group -->
  <policy user="0">
    <allow send_interface="org.freedesktop.Hal.Device.SystemPowerManagement"/>
    <allow send_interface="org.freedesktop.Hal.Device.VideoAdapterPM"/>
    <allow send_interface="org.freedesktop.Hal.Device.LaptopPanel"/>
    <allow send_interface="org.freedesktop.Hal.Device.Volume"/>
    <allow send_interface="org.freedesktop.Hal.Device.Volume.Crypto"/>
  </policy>
```
to
```
<policy group="plugdev">
```

My smb.conf:
```
[global]
server string = Security-Zen
workgroup = PARALLAX
security = ads
realm = PARALLAX.LOCAL
domain master = no

client ntlmv2 auth = yes
acl compatibility = win2k
server signing = Auto
preferred master = no

winbind separator = -
idmap gid = 10000-20000
idmap uid = 10000-20000
winbind enum groups = yes
winbind enum users = yes
template shell = /bin/bash
template homedir = /home/%D/%U
winbind use default domain = no
winbind offline logon = yes
winbind refresh tickets = yes
winbind nested groups = yes

include = /etc/samba/dhcp.conf

dos charset = CP866
display charset = UTF-8
unix charset = UTF-8

usershare max shares = 100
usershare allow guests = Yes
guest ok = yes
printcap name = cups
cups options = raw
```

'dos charset = CP866' is because of my Cyrillic Windows network.

---

### Post by BevanFindlay on 2007-09-30
I just thought others may be looking at similar things and that it was worth posting how I finally got all this sorted.

(1) The sound issue was solved by making /etc/pam.d/common-auth look like this:
```

auth    sufficient      pam_unix.so
auth    required        pam_group.so use_first_pass
auth    required        pam_winbind.so use_first_pass krb5_auth krb5_ccache_type=FILE

```
The trick was swapping the order of pam_unix.so and pam_winbind.so.
The krb5 stuff is also useful, as it sets up a Kerberos ticket at logon, meaning that the user doesn't need to retype their password every time they connect to a Windows file share.

Also this:
File: /etc/security/group.conf
```

.....(a lot of commented stuff) ....
#xsh; tty* ;sword;!Wk0900-1800;sound, play
#xsh; tty* ;*;Al0900-1800;floppy

* ; * ; * ; Al0000-2400 ; floppy, video, audio, cdrom, dip, plugdev, users, scanner

#
# End of group.conf file
#

```

Answers from here:
[http://ubuntuforums.org/showthread.php?t=77469](http://ubuntuforums.org/showthread.php?t=77469)

(2) To allow Domain Admins to sudo simply requires adding the following to the bottom of the sudoers file (run "visudo" from a terminal):
```

%Domain\ Admins ALL=(ALL) ALL

```

(3) To set up desktop stuff, create a folder in /etc/skel/ called "Desktop", then put things in there and they will appear whenever a new user logs in for the first time.

(4) Still working on this one :)
If anyone knows how to image a Linux partition to a drive of slightly different size, this would be really useful (in particular, I am using an old machine with a 10GB hard drive, but another 10GB drive I have for another machine is just ever so slightly smaller - a few MB - and so Ghost for Linux won't image it) :(  Any thoughts would be appreciated.

Thanks to all those who contributed these items on the forums and all.

Also, if anyone knows of a Wiki or something that the process of joining a Windows domain should be consolidated into, I am willing to help out a little.

Thanks,
  - Bevan.

---

### Post by nullimage on 2007-10-08
> **BevanFindlay said:**
> 
(4) Still working on this one :)
If anyone knows how to image a Linux partition to a drive of slightly different size, this would be really useful (in particular, I am using an old machine with a 10GB hard drive, but another 10GB drive I have for another machine is just ever so slightly smaller - a few MB - and so Ghost for Linux won't image it) :(  Any thoughts would be appreciated.

Have you tried Clonezilla? [http://clonezilla.sourceforge.net/](http://clonezilla.sourceforge.net/)

There's a Live CD version which works well. I know there's an option to resize the partitions, but I haven't tried it with a smaller hard drive.

---

