---
title: "X11 remote application"
date: 2015-03-29
forum: General Help
---

### Post by Richard_Romick on 2015-03-29
I have two computers, a laptop running Ubuntu 14.04 64-bit and a desktop running Linux Mint 17.1 (virtualbox).  I am working on being able to run both RSSOwl and Evolution on the laptop, but being displayed on the desktop.  I can do this with RSSOwl just fine, but Evolution is much more difficult.  This is what happens:

#sorry that senlis is my username on both computers, may make this somewhat difficult to follow.

senlis@senlis-VirtualBox ~ $ sudo ssh -Y senlis@192.168.8.6
[sudo] password for senlis: 
[...]
Warning: Permanently added '192.168.8.6' (ECDSA) to the list of known hosts.
senlis@192.168.8.6's password: 
Welcome to Ubuntu 14.04.2 LTS (GNU/Linux 3.13.0-48-generic x86_64)

 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

Last login: Sat Mar 28 08:41:29 2015 from 192.168.8.24
senlis@senlis-Galago-UltraPro:~$ evolution

** (evolution:17171): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-hwkbPrwx0z: Connection refused

(evolution:17171): GLib-GObject-CRITICAL **: g_object_unref: assertion 'G_IS_OBJECT (object)' failed


Cannot start Evolution: Another Evolution instance may be unresponsive.  System error: Could not connect: Connection refused

Does anyone know why this may be happening.  Thank you,

---

### Post by tgalati4 on 2015-03-29
What are the permissions of /tmp/dbus-hwkbPrwx0z?  Perhaps loosening them up:

```
sudo chmod 777 /tmp/dbus-hwkbPrwx0z
``` 

and then try again.  Of course this is temporary as /tmp gets wiped with each boot.  Seems like an accessibility framework problem.  Perhaps a Use Case where accessiblity is does not work correctly over an X-forwarded, ssh connection.

---

### Post by TheFu on 2015-03-30
I think it is an x/windows permission issue - don't use sudo to remote into the other machine. Run ssh as the normal userid.
If you have been running GUI applications with sudo, there can be other permissions issues that have been caused by that too. You may need to clean up all permissions in the HOME on both computers.

---

### Post by Richard_Romick on 2015-03-30
> **TheFu said:**
> I think it is an x/windows permission issue - don't use sudo to remote into the other machine. Run ssh as the normal userid.
If you have been running GUI applications with sudo, there can be other permissions issues that have been caused by that too. You may need to clean up all permissions in the HOME on both computers.

I run it without sudo and it does the same thing.  I have been running Thunderbird recently, since it works over the ssh connection.  However, it does so with its share of errors, though it seems to work fine otherwise.

(process:25378): GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size == 0' failed

(thunderbird:25378): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::sm-connect after class was initialised

(thunderbird:25378): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::show-crash-dialog after class was initialised

(thunderbird:25378): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::display after class was initialised

(thunderbird:25378): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::default-icon after class was initialised

(thunderbird:25378): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
Failed to connect to socket /tmp/dbus-MKWZcYhWjH: Connection refused

(thunderbird:25378): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
Failed to connect to socket /tmp/dbus-ESyCcB5lrd: Connection refused

(thunderbird:25378): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
Failed to connect to socket /tmp/dbus-lsDeFIbtJb: Connection refused

(thunderbird:25378): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
Failed to connect to socket /tmp/dbus-pp7Bsk9G10: Connection refused

(thunderbird:25378): libunity-CRITICAL **: unity-launcher.vala:154: Unable to connect to session bus: Could not connect: Connection refused

** (thunderbird:25378): WARNING **: unable to connect to session bus: Could not connect: Connection refused

(thunderbird:25378): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
Failed to connect to socket /tmp/dbus-cnoh95jJUM: Connection refused

(thunderbird:25378): LIBDBUSMENU-GLIB-WARNING **: Unable to get session bus: Could not connect: Connection refused

(thunderbird:25378): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
Failed to connect to socket /tmp/dbus-BrNFGqGY0G: Connection refused

(thunderbird:25378): libnotify-WARNING **: Failed to connect to proxy
senlis@senlis-Galago-UltraPro:~$ evolution

** (evolution:25524): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-dEO8iLTSPj: Connection refused

(evolution:25524): GLib-GObject-CRITICAL **: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
senlis@senlis-Galago-UltraPro:~$ thunderbird

(process:25538): GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size == 0' failed

(thunderbird:25538): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::sm-connect after class was initialised

(thunderbird:25538): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::show-crash-dialog after class was initialised

(thunderbird:25538): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::display after class was initialised

(thunderbird:25538): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::default-icon after class was initialised

(thunderbird:25538): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
Failed to connect to socket /tmp/dbus-RogxpZaPDk: Connection refused

(thunderbird:25538): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
Failed to connect to socket /tmp/dbus-xMcb34PWSS: Connection refused

(thunderbird:25538): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
Failed to connect to socket /tmp/dbus-lMchs6Er9P: Connection refused

(thunderbird:25538): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
Failed to connect to socket /tmp/dbus-2ZgDAoLVUp: Connection refused

(thunderbird:25538): libunity-CRITICAL **: unity-launcher.vala:154: Unable to connect to session bus: Could not connect: Connection refused

** (thunderbird:25538): WARNING **: unable to connect to session bus: Could not connect: Connection refused

(thunderbird:25538): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
Failed to connect to socket /tmp/dbus-MsVZVJTTMv: Connection refused

(thunderbird:25538): LIBDBUSMENU-GLIB-WARNING **: Unable to get session bus: Could not connect: Connection refused

(thunderbird:25538): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
Failed to connect to socket /tmp/dbus-RcnWHpWfVA: Connection refused

message: An error occurred while loading or saving configuration information for thunderbird.  Some of your configuration settings may not work properly.

---

