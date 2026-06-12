---
title: "Hardy freeze on boot - quite serious"
date: 2008-04-25
forum: General Help
---

### Post by LK_gandalf_ on 2008-04-25
Hi, Some days ago I've installed Kubuntu Hardy 64bit on my Dell XPS M1530, using the RC version, live cd. I've done the updates released in these days, and everything works perfectly. But today I have a problem booting.

Kubuntu starts, I see the Kubuntu loading bar, but then appears the black screen with this:

Starting K display manager KDM [OK]
...
...
..
..
until this:
Running local boot scripts (/etc/rc.local) [OK]

Then nothing, everything remains the same.

At this point, if I press ctrl+alt+F1, F2 until F6, I can do a shell login, then write "startx" and the desktop loads well. But, obviously, this is a very bad problem and need to be fixed.

uname -a
Linux xxx-xxx 2.6.24-16-generic #1 x86_64 GNU/Linux

Ask me if you need other infos.
Thank you

---

### Post by Yoeri on 2008-04-25
- don't bother ... stupid answer

---

### Post by LK_gandalf_ on 2008-04-26
up

---

### Post by LK_gandalf_ on 2008-04-29
please, help me :(

---

### Post by der_joachim on 2008-04-29
You did not fiddle around with sysv-rc-conf or other startup managers, did you? I did some time ago and I've had no KDM for quite some time. If you do not know what I am talking about, that's probably the best. ;)

Another option may be to open up a konsole and issue the following command:
```

sudo dpkg-reconfigure kdm

```

---

### Post by LK_gandalf_ on 2008-04-30
Nothing changed :) And i0ve never modified any startup file, not manually of course. :(
this problem is very annoying...and nobody seems to know how to fix.

maybe it could be useful, I don't know: 
/etc/rc.local

```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0

```

and here the /etc/init.d/rc.local.

```

#! /bin/sh

PATH=/sbin:/bin:/usr/sbin:/usr/bin
[ -f /etc/default/rcS ] && . /etc/default/rcS
. /lib/lsb/init-functions

do_start() {
	if [ -x /etc/rc.local ]; then
		log_begin_msg "Running local boot scripts (/etc/rc.local)"
		/etc/rc.local
		log_end_msg $?
	fi
}

case "$1" in
    start)
	do_start
        ;;
    restart|reload|force-reload)
        echo "Error: argument '$1' not supported" >&2
        exit 3
        ;;
    stop)
        ;;
    *)
        echo "Usage: $0 start|stop" >&2
        exit 3
        ;;
esac


```

---

### Post by der_joachim on 2008-04-30
Your local scripts are OK. It's just that KDM doesn't start at all. Since your xorg seems fine, how about trying this: when in command line, issue the following command:
```

sudo /etc/init.d/kdm restart

```
If you get an error message, you can google around for what it means. I did not get any messages. KDM just started as it should have. It was quite annoying that KDM would not start at all. I fixed it by undoing the abuse of my startup files.

Good luck.

---

### Post by LK_gandalf_ on 2008-05-01
So I have to try this command where I normally write startx? 
I've just tried here, from the desktop. Kdm stopped but then blak screen, and nothing works, I had to shutdown manually.
I've tried the same command after the manual login, before I usually wirte "startx", and it works, kdm reloads and I have the login windows again. But the problem is still there, if I login appears the black screen like described in my first post.
I don't understand how kdm should be related to my problem...Kdm starts everytime, the freeze is after rc.local :(

---

### Post by der_joachim on 2008-05-01
I may have misunderstood, but as far as I know, rc.local is the last script that is being run while in runlevel 2. KDM runs in runlevel 3. Since you can login in the terminal (runlevel 2), you can safely assume that rc.local finished normally and that kdm is the problem. In a nutshell, that is why I think that KDM is the problem. 

As for why kdm crashes at boot, search me. Try the following: when your system displays the 'starting rc.local' message, press Alt+F7. Maybe, just maybe, you see an error message. If not, try reading /var/log/kdm.log . You may need root privileges.

Out of curiosity: what video driver are you using? Have you searched launchpad already for a possible fix?

---

### Post by LK_gandalf_ on 2008-05-01
thank you for the help :)

I have already opened a bug [https://bugs.launchpad.net/ubuntu/+bug/221145](https://bugs.launchpad.net/ubuntu/+bug/221145) but nobody cares me.
I've searched all long internet, but no workings olution came out. I don't want and i can't absoluty format, I have just installed my system and I'd like a best performance from linux, not to format for a strange problem after a week :)

I'VE tried your trick, but nothing happened. When i press alt+F7 I see only a flashing _ in the top of the screen, I have to press alt+F6 or other to login, then startx. Here my kdm.log 

```


********************************************************************************
Note that your system uses syslog. All of kdm's internally generated messages
(i.e., not from libraries and external programs/scripts it uses) go to the
daemon.* syslog facility; check your syslog configuration to find out to which
file(s) it is logged. PAM logs messages related to authentication to authpriv.*.
********************************************************************************


This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9)
Current Operating System: Linux doc-laptop 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 x86_64
Build Date: 15 April 2008  05:41:18PM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri May  2 12:56:33 2008
(==) Using config file: "/etc/X11/xorg.conf"
(II) Module "ramdac" already built-in
expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc
Atom 4, CARD32 4, unsigned long 8
Synaptics Touchpad no synaptics event device found (checked 19 nodes)
Query no Synaptics: 6003C8
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"
expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
*** glibc detected *** -:0: double free or corruption (out): 0x00007f90792b3aa0 ***
======= Backtrace: =========
/lib/libc.so.6[0x7f9078fca08a]
/lib/libc.so.6(cfree+0x8c)[0x7f9078fcdc1c]
/usr/lib/libthinkfinger.so.0(libthinkfinger_set_file+0x25)[0x7f90774dfd65]
/lib/security/pam_thinkfinger.so[0x7f90776e3999]
/lib/libpthread.so.0[0x7f90772c83f7]
/lib/libc.so.6(clone+0x6d)[0x7f907902db2d]
======= Memory map: ========
00400000-00424000 r-xp 00000000 08:06 836248                             /usr/bin/kdm
00624000-00625000 rw-p 00024000 08:06 836248                             /usr/bin/kdm
00625000-00659000 rw-p 00625000 00:00 0                                  [heap]
41cb3000-41cb4000 ---p 41cb3000 00:00 0 
41cb4000-424b4000 rw-p 41cb4000 00:00 0 
424b4000-424b5000 ---p 424b4000 00:00 0 
424b5000-42cb5000 rw-p 424b5000 00:00 0 
7f907663d000-7f907664a000 r-xp 00000000 08:06 5431360                    /lib/libgcc_s.so.1
7f907664a000-7f907684a000 ---p 0000d000 08:06 5431360                    /lib/libgcc_s.so.1
7f907684a000-7f907684b000 rw-p 0000d000 08:06 5431360                    /lib/libgcc_s.so.1
7f907684b000-7f907684e000 r-xp 00000000 08:06 5431848                    /lib/security/pam_limits.so
7f907684e000-7f9076a4d000 ---p 00003000 08:06 5431848                    /lib/security/pam_limits.so
7f9076a4d000-7f9076a4e000 rw-p 00002000 08:06 5431848                    /lib/security/pam_limits.so
7f9076a4e000-7f9076a67000 r-xp 00000000 08:06 5431421                    /lib/libselinux.so.1
7f9076a67000-7f9076c67000 ---p 00019000 08:06 5431421                    /lib/libselinux.so.1
7f9076c67000-7f9076c69000 rw-p 00019000 08:06 5431421                    /lib/libselinux.so.1
7f9076c69000-7f9076c6a000 rw-p 7f9076c69000 00:00 0 
7f9076c6a000-7f9076c73000 r-xp 00000000 08:06 5431347                    /lib/libcrypt-2.7.so
7f9076c73000-7f9076e72000 ---p 00009000 08:06 5431347                    /lib/libcrypt-2.7.so
7f9076e72000-7f9076e74000 rw-p 00008000 08:06 5431347                    /lib/libcrypt-2.7.so
7f9076e74000-7f9076ea2000 rw-p 7f9076e74000 00:00 0 
7f9076ea2000-7f9076eae000 r-xp 00000000 08:06 5431869                    /lib/security/pam_unix.so
7f9076eae000-7f90770ad000 ---p 0000c000 08:06 5431869                    /lib/security/pam_unix.so
7f90770ad000-7f90770ae000 rw-p 0000b000 08:06 5431869                    /lib/security/pam_unix.so
7f90770ae000-7f90770ba000 rw-p 7f90770ae000 00:00 0 
7f90770ba000-7f90770c1000 r-xp 00000000 08:06 5431438                    /lib/libusb-0.1.so.4.4.4
7f90770c1000-7f90772c0000 ---p 00007000 08:06 5431438                    /lib/libusb-0.1.so.4.4.4
7f90772c0000-7f90772c2000 rw-p 00006000 08:06 5431438                    /lib/libusb-0.1.so.4.4.4
7f90772c2000-7f90772d8000 r-xp 00000000 08:06 5431413                    /lib/libpthread-2.7.so
7f90772d8000-7f90774d8000 ---p 00016000 08:06 5431413                    /lib/libpthread-2.7.so
7f90774d8000-7f90774da000 rw-p 00016000 08:06 5431413                    /lib/libpthread-2.7.so
7f90774da000-7f90774de000 rw-p 7f90774da000 00:00 0 
7f90774de000-7f90774e1000 r-xp 00000000 08:06 838625                     /usr/lib/libthinkfinger.so.0.0.0
7f90774e1000-7f90776e1000 ---p 00003000 08:06 838625                     /usr/lib/libthinkfinger.so.0.0.0
7f90776e1000-7f90776e2000 rw-p 00003000 08:06 838625                     /usr/lib/libthinkfinger.so.0.0.0
7f90776e2000-7f90776e5000 r-xp 00000000 08:06 5431929                    /lib/security/pam_thinkfinger.so
7f90776e5000-7f90778e4000 ---p 00003000 08:06 5431929                    /lib/security/pam_thinkfinger.so
7f90778e4000-7f90778e5000 rw-p 00002000 08:06 5431929                    /lib/security/pam_thinkfinger.so
7f90778e5000-7f90778e8000 r-xp 00000000 08:06 5431839                    /lib/security/pam_env.so
7f90778e8000-7f9077ae7000 ---p 00003000 08:06 5431839                    /lib/security/pam_env.so
7f9077ae7000-7f9077ae8000 rw-p 00002000 08:06 5431839                    /lib/security/pam_env.so
7f9077ae8000-7f9077ae9000 r-xp 00000000 08:06 5431856                    /lib/security/pam_nologin.so
7f9077ae9000-7f9077ce8000 ---p 00001000 08:06 5431856                    /lib/security/pam_nologin.so
7f9077ce8000-7f9077ce9000 rw-p 00000000 08:06 5431856                    /lib/security/pam_nologin.so
7f9077ce9000-7f9077cf3000 r-xp 00000000 08:06 5431385                    /lib/libnss_files-2.7.so
7f9077cf3000-7f9077ef3000 ---p 0000a000 08:06 5431385                    /lib/libnss_files-2.7.so
7f9077ef3000-7f9077ef5000 rw-p 0000a000 08:06 5431385                    /lib/libnss_files-2.7.so
7f9077ef5000-7f9077eff000 r-xp 00000000 08:06 5431395                    /lib/libnss_nis-2.7.so
7f9077eff000-7f90780fe000 ---p 0000a000 08:06 5431395                    /lib/libnss_nis-2.7.so
7f90780fe000-7f9078100000 rw-p 00009000 08:06 5431395                    /lib/libnss_nis-2.7.so
7f9078100000-7f9078116000 r-xp 00000000 08:06 5431379                    /lib/libnsl-2.7.so
7f9078116000-7f9078315000 ---p 00016000 08:06 5431379                    /lib/libnsl-2.7.so
7f9078315000-7f9078317000 rw-p 00015000 08:06 5431379                    /lib/libnsl-2.7.so
7f9078317000-7f9078319000 rw-p 7f9078317000 00:00 0 
7f9078319000-7f9078321000 r-xp 00000000 08:06 5431381                    /lib/libnss_compat-2.7.so
7f9078321000-7f9078520000 ---p 00008000 08:06 5431381                    /lib/libnss_compat-2.7.so
7f9078520000-7f9078522000 rw-p 00007000 08:06 5431381                    /lib/libnss_compat-2.7.so
7f9078522000-7f9078527000 r-xp 00000000 08:06 836972                     /usr/lib/libXfixes.so.3.1.0
7f9078527000-7f9078726000 ---p 00005000 08:06 836972                     /usr/lib/libXfixes.so.3.1.0
7f9078726000-7f9078727000 rw-p 00004000 08:06 836972                     /usr/lib/libXfixes.so.3.1.0
7f9078727000-7f9078730000 r-xp 00000000 08:06 836992                     /usr/lib/libXrender.so.1.3.0
7f9078730000-7f907892f000 ---p 00009000 08:06 836992                     /usr/lib/libXrender.so.1.3.0
7f907892f000-7f9078930000 rw-p 00008000 08:06 836992                     /usr/lib/libXrender.so.1.3.0
7f9078930000-7f9078939000 r-xp 00000000 08:06 836964                     /usr/lib/libXcursor.so.1.0.2
7f9078939000-7f9078b39000 ---p 00009000 08:06 836964                     /usr/lib/libXcursor.so.1.0.2
7f9078b39000-7f9078b3a000 rw-p 00009000 08:06 836964                     /usr/lib/libXcursor.so.1.0.2
7f9078b3a000-7f9078b55000 r-xp 00000000 08:06 837958                     /usr/lib/libxcb.so.1.0.0
7f9078b55000-7f9078d54000 ---p 0001b000 08:06 837958                     /usr/lib/libxcb.so.1.0.0
7f9078d54000-7f9078d55000 rw-p 0001a000 08:06 837958                     /usr/lib/libxcb.so.1.0.0
7f9078d55000-7f9078d56000 r-xp 00000000 08:06 837954                     /usr/lib/libxcb-xlib.so.0.0.0
7f9078d56000-7f9078f55000 ---p 00001000 08:06 837954                     /usr/lib/libxcb-xlib.so.0.0.0
7f9078f55000-7f9078f56000 rw-p 00000000 08:06 837954                     /usr/lib/libxcb-xlib.so.0.0.0
7f9078f56000-7f90790ae000 r-xp 00000000 08:06 5431335                    /lib/libc-2.7.so
7f90790ae000-7f90792ae000 ---p 00158000 08:06 5431335                    /lib/libc-2.7.so
7f90792ae000-7f90792b1000 r--p 00158000 08:06 5431335                    /lib/libc-2.7.so
7f90792b1000-7f90792b3000 rw-p 0015b000 08:06 5431335                    /lib/libc-2.7.so
7f90792b3000-7f90792b8000 rw-p 7f90792b3000 00:00 0 
7f90792b8000-7f90792ba000 r-xp 00000000 08:06 5431440                    /lib/libutil-2.7.so
7f90792ba000-7f90794b9000 ---p 00002000 08:06 5431440                    /lib/libutil-2.7.so
7f90794b9000-7f90794bb000 rw-p 00001000 08:06 5431440                    /lib/libutil-2.7.so
7f90794bb000-7f90794cd000 r-xp 00000000 08:06 5431417                    /lib/libresolv-2.7.so
7f90794cd000-7f90796cd000 ---p 00012000 08:06 5431417                    /lib/libresolv-2.7.so
7f90796cd000-7f90796cf000 rw-p 00012000 08:06 5431417                    /lib/libresolv-2.7.so
7f90796cf000-7f90796d1000 rw-p 7f90796cf000 00:00 0 
7f90796d1000-7f907970c000 r-xp 00000000 08:06 837141                     /usr/lib/libdbus-1.so.3.4.0
7f907970c000-7f907990c000 ---p 0003b000 08:06 837141                     /usr/lib/libdbus-1.so.3.4.0
7f907990c000-7f907990e000 rw-p 0003b000 08:06 837141                     /usr/lib/libdbus-1.so.3.4.0
7f907990e000-7f9079910000 r-xp 00000000 08:06 5431352                    /lib/libdl-2.7.so
7f9079910000-7f9079b10000 ---p 00002000 08:06 5431352                    /lib/libdl-2.7.so
7f9079b10000-7f9079b12000 rw-p 00002000 08:06 5431352                    /lib/libdl-2.7.so
7f9079b12000-7f9079b1c000 r-xp 00000000 08:06 5431402                    /lib/libpam.so.0.81.6
7f9079b1c000-7f9079d1b000 ---p 0000a000 08:06 5431402                    /lib/libpam.so.0.81.6
7f9079d1b000-7f9079d1c000 rw-p 00009000 08:06 5431402                    /lib/libpam.so.0.81.6
7f9079d1c000-7f9079d21000 r-xp 00000000 08:06 836968                     /usr/lib/libXdmcp.so.6.0.0
7f9079d21000-7f9079f20000 ---p 00005000 08:06 836968                     /usr/lib/libXdmcp.so.6.0.0
7f9079f20000-7f9079f21000 rw-p 00004000 08:06 836968                     /usr/lib/libXdmcp.so.6.0.0
7f9079f21000-7f9079f23000 r-xp 00000000 08:06 836957                     /usr/lib/libXau.so.6.0.0
7f9079f23000-7f907a122000 ---p 00002000 08:06 836957                     /usr/lib/libXau.so.6.0.0
7f907a122000-7f907a123000 rw-p 00001000 08:06 836957                     /usr/lib/libXau.so.6.0.0
7f907a123000-7f907a222000 r-xp 00000000 08:06 836953                     /usr/lib/libX11.so.6.2.0
7f907a222000-7f907a421000 ---p 000ff000 08:06 836953                     /usr/lib/libX11.so.6.2.0
7f907a421000-7f907a426000 rw-p 000fe000 08:06 836953                     /usr/lib/libX11.so.6.2.0
7f907a426000-7f907a443000 r-xp 00000000 08:06 5431315                    /lib/ld-2.7.so
7f907a625000-7f907a62a000 rw-p 7f907a625000 00:00 0 
7f907a63f000-7f907a643000 rw-p 7f907a63f000 00:00 0 
7f907a643000-7f907a645000 rw-p 0001d000 08:06 5431315                    /lib/ld-2.7.so
7fff8262f000-7fff82644000 rw-p 7ffffffea000 00:00 0                      [stack]
7fff827fe000-7fff827ff000 r-xp 7fff827fe000 00:00 0                      [vdso]
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vsyscall]


```

---

### Post by LK_gandalf_ on 2008-05-03
up

---

### Post by LK_gandalf_ on 2008-05-03
up :)

---

### Post by LK_gandalf_ on 2008-05-04
up :(

---

### Post by dannyboy1121 on 2008-05-04
I have the same problem trying to boot the live cd on my Samsung R40 plus laptop. I get to running local boot scripts and then it just hangs ..... :(

So .. at least you know you're not on your own.

This isn't the same experience I've had with the last three versions of the distro. I wonder what's going on.

NB - this is a straight Ubuntu installtion for me .. not Kubuntu.

---

### Post by pat5star on 2008-05-04
I have the exact same problem the original poster is describing. Very interested in a fix for this as I'm stumped myself.

This started for me last night after I upgraded to heron.

---

### Post by LK_gandalf_ on 2008-05-06
up up up

'm asking for a fix since weeks, on two forums :) NO answers yet. I'm really thinking to come back to windows as protest. :mad:

---

### Post by LK_gandalf_ on 2008-05-07
SOLVED.
I don't know exactly how, two things solved it:

1) a daily update, maybe, one of the package was the problem

2) most probably: I uninstalled the biometric finger reader (on my laptop), this caused the problem probably.

GG

---

### Post by pat5star on 2008-05-11
Solved for me now too, I think an update did it.

---

