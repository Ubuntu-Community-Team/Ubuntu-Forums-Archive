---
title: "multiple usesr autologon text + GUI"
date: 2015-12-11
forum: General Help
---

### Post by piotrasbl on 2015-12-11
Dear All,

Currently my xbuntu is booting in text mode as it supplies home network with storage and minidlna services.

Now, the machine is placed near tv i'd like it to be also youtube device which requires gui for another user.

At the moment grub in /etc/defaults/grub looks like below:
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="text"
GRUB_CMDLINE_LINUX="text"

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"


```

Now the tty1.conf is set as below:
```
# tty1 - getty
#
# This service maintains a getty on tty1 from the point the system is
# started until it is shut down again.

start on stopped rc RUNLEVEL=[2345] and (
            not-container or
            container CONTAINER=lxc or
            container CONTAINER=lxc-libvirt)

stop on runlevel [!2345]

respawn
exec /bin/login -f user1 < /dev/tty1 > /dev/tty1 2>&1
```

[B]Question:
[/B]What should I amend to log user2 [B]with gui session on different tty ?

[/B]I really appreciate all help.My xbuntu is 14.04.03 LTS

---

### Post by ian-weisser on 2015-12-11
I do not understand why user1 needs to be auto-login.
What services are running under user1 that cannot be provided by a system user?
Or is user1 logged in merely to display the status of those services?

---

### Post by piotrasbl on 2015-12-11
[**[COLOR=#DD4814][B]ian-weisser**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1841707"),
User one is running samba,minidlna and print server; the reason I do not want to have this atarted with user2 is because user2 will be available to everyone, thus I would not like to restore files,configs ect. User2 is to be available for everyone for internet access reasons.

---

### Post by ian-weisser on 2015-12-11
> **piotrasbl said:**
> User one is running samba,minidlna and print server

That's why I don't understand the login problem.

None of those services should be running under a login user. All of those should normally be running headless under different system (non-login) users. Is there a particular reason why you are running those services in a nonstandard way? It makes changes and support harder, as you are discovering.

Can your other 'user2' population use the existing Xubuntu 'guest' account? That would be simpler than setting up a generic user2, and avoids the autologin problem.

---

