---
title: "cdemu: Can't connect to daemon"
date: 2008-01-18
forum: General Help
---

### Post by Rahu on 2008-01-18
I'm attempting to get cdemu working.

Everything seemed to install properly and is working fine alone, but the client won't recognize the daemon.

Problem 1: Starting the daemon in local mode won't work. Error about dbus. Dbus is installed an I've never had any other program complain about it.
```
Starting daemon locally with following parameters:
 - num_devices: 1
 - ctl_device: /dev/vhba_ctl
 - audio_backend: (null)
 - audio_device: (null)
 - system_bus: 0
cdemud: cdemud_daemon_initialize: failed to get session bus!
Daemon initialization failed: Failed to connect to D-BUS bus.

```

I got around this by running in daemon mode, but the client gives me this error

note: The extra cd drives appear in /dev/, so I'm fairly certain that the daemon is running properly.

```
$ cdemu status
ERROR: Failed to connect to CDEmu daemon: org.freedesktop.DBus.Error.ServiceUnknown: The name net.sf.cdemu.CDEMUD_Daemon was not provided by any .service files
ERROR: Failed to connect to daemon!

```

Also, following an install guide for the preview release, an entry was supposed to exist in /etc/init.d/, but nothing about cdemu is there.


Any ideas on what could be causing this? All packages were installed from source today with no errors.

---

### Post by _Stevie_ on 2008-02-02
have the same problem, any help appreciated!

---

### Post by _Stevie_ on 2008-02-04
found it!
you have to put the -s option for system bus
cdemud -s [......]

---

### Post by Beholder87 on 2008-02-06
hi i just installed cdemu here and i have the same problems here.......
i downloaded the packages for ubuntu: [http://sourceforge.net/project/showfiles.php?group_id=93175&package_id=256719](http://sourceforge.net/project/showfiles.php?group_id=93175&package_id=256719)

and then executed it. so it installed automatically(GDebi Package Installer)....

then in the terminal, when i tried to use:
```
cdemu status
```
i gives me the same error:
```
ERROR: Failed to connect to CDEmu daemon: org.freedesktop.DBus.Error.ServiceUnknown: The name net.sf.cdemu.CDEMUD_Daemon was not provided by any .service files
**ERROR: Failed to connect to daemon!**

```

can anyone help me here???

i tried also to use the code with the "-s" take a look:
```
monster@monster:~$ cdemud
Starting daemon locally with following parameters:
 - num_devices: 1
 - ctl_device: /dev/vhba_ctl
 - audio_backend: (null)
 - audio_device: (null)
 - system_bus: 0
cdemud: cdemud_daemon_initialize: failed to open control device /dev/vhba_ctl!
**Daemon initialization failed: Failed to open control device.**
monster@monster:~$ cdemud -s
Starting daemon locally with following parameters:
 - num_devices: 1
 - ctl_device: /dev/vhba_ctl
 - audio_backend: (null)
 - audio_device: (null)
 - system_bus: 1
cdemud: cdemud_daemon_initialize: failed to open control device /dev/vhba_ctl!
Daemon initialization failed: Failed to open control device.
monster@monster:~$ cdemu status
ERROR: Failed to connect to CDEmu daemon: org.freedesktop.DBus.Error.ServiceUnknown: The name net.sf.cdemu.CDEMUD_Daemon was not provided by any .service files
ERROR: Failed to connect to daemon!
monster@monster:~$ 

```

---

### Post by _Stevie_ on 2008-02-06
sudo mate, sudo!  :eek:

---

### Post by Beholder87 on 2008-02-06
```
monster@monster:~$ sudo cdemud
[sudo] password for monster:
Starting daemon locally with following parameters:
 - num_devices: 1
 - ctl_device: /dev/vhba_ctl
 - audio_backend: (null)
 - audio_device: (null)
 - system_bus: 0
cdemud: cdemud_daemon_initialize: failed to open control device /dev/vhba_ctl!
Daemon initialization failed: Failed to open control device.
monster@monster:~$ sudo cdemud -s
Starting daemon locally with following parameters:
 - num_devices: 1
 - ctl_device: /dev/vhba_ctl
 - audio_backend: (null)
 - audio_device: (null)
 - system_bus: 1
cdemud: cdemud_daemon_initialize: failed to open control device /dev/vhba_ctl!
Daemon initialization failed: Failed to open control device.
monster@monster:~$ 

```

same thing with sudo......

---

### Post by _Stevie_ on 2008-02-06
hmm thats strange, sudo cdemud -s should work. i guess you didnt activate the daemon (that one is responsible for the vhba_ctl).
activate it by typing this and reboot:

```
sudo update-rc.d -f cdemu-daemon defaults 
```

but then you are as far as i am at the moment.
i want to give the arguments (alsa support, 1 device) during boot time.
but i have no clue how to achieve that. any tips appreciated.

---

### Post by Beholder87 on 2008-02-07
thanks _stevie_ i'll try that
=)

p.s.= i was trying to setup cdemu only to play warcraft III without cd, using a no-cd image (mds file type), but yesterday the blizzard released the patch 1.21b that is no longer necessary to use the cd to play the game!!!! now i can play [DotA]("http://www.dota-allstars.com") without using the CD!!!!!!! =)

i'll use the command that you posted just in case in the future i need cdemu =)
^^

the output from your code: 
```
monster@monster:~$ sudo update-rc.d -f cdemu-daemon defaults
[sudo] password for monster:
 Adding system startup for /etc/init.d/cdemu-daemon ...
   /etc/rc0.d/K20cdemu-daemon -> ../init.d/cdemu-daemon
   /etc/rc1.d/K20cdemu-daemon -> ../init.d/cdemu-daemon
   /etc/rc6.d/K20cdemu-daemon -> ../init.d/cdemu-daemon
   /etc/rc2.d/S20cdemu-daemon -> ../init.d/cdemu-daemon
   /etc/rc3.d/S20cdemu-daemon -> ../init.d/cdemu-daemon
   /etc/rc4.d/S20cdemu-daemon -> ../init.d/cdemu-daemon
   /etc/rc5.d/S20cdemu-daemon -> ../init.d/cdemu-daemon
monster@monster:~$ 

```

now i'll reboot and see what happens

EDIT:

ok take a look what happened after i rebooted:
```
monster@monster:~$ sudo cdemud
[sudo] password for monster:
Starting daemon locally with following parameters:
 - num_devices: 1
 - ctl_device: /dev/vhba_ctl
 - audio_backend: (null)
 - audio_device: (null)
 - system_bus: 0
cdemud: cdemud_daemon_initialize: failed to get session bus!
Daemon initialization failed: Failed to connect to D-BUS bus.
monster@monster:~$ sudo cdemud -s
Starting daemon locally with following parameters:
 - num_devices: 1
 - ctl_device: /dev/vhba_ctl
 - audio_backend: (null)
 - audio_device: (null)
 - system_bus: 1


```
the terminal stopped there blinking... it should open a new line like this after finished to start cdemud: "monster@monster:~$"
 now when i try to use the othe command, it gives me the same error:
```
monster@monster:~$ cdemu status
ERROR: Failed to connect to CDEmu daemon: org.freedesktop.DBus.Error.ServiceUnknown: The name net.sf.cdemu.CDEMUD_Daemon was not provided by any .service files
ERROR: Failed to connect to daemon!
monster@monster:~$ 

```

when i use the command: sudo cdemud -s, the terminal don't give me an answer..... i can't use other commands if i don't open other tabs....

---

### Post by _Stevie_ on 2008-02-07
> ok take a look what happened after i rebooted:

```
monster@monster:~$ sudo cdemud
[sudo] password for monster:
Starting daemon locally with following parameters:
 - num_devices: 1
 - ctl_device: /dev/vhba_ctl
 - audio_backend: (null)

 - audio_device: (null)
 - system_bus: 0
cdemud: cdemud_daemon_initialize: failed to get session bus!
Daemon initialization failed: Failed to connect to D-BUS bus.
monster@monster:~$ sudo cdemud -s
Starting daemon locally with following parameters:
 - num_devices: 1
 - ctl_device: /dev/vhba_ctl
 - audio_backend: (null)
 - audio_device: (null)
 - system_bus: 1


```

yup, thats how far i get, too when entering sudo cdemud -s.
the cursor blinks. thats also my problem.
but i think when the cursor blinks, the daemon changed the settings already.
not sure tho.

when you start the daemon with 
```

sudo update-rc.d -f cdemu-daemon defaults
```

there must be a way to start the daemon with the desired settings.
unfortuneately i couldnt find out how yet.



> the terminal stopped there blinking... it should open a new line like this after finished to start cdemud: "monster@monster:~$"
 now when i try to use the othe command, it gives me the same error:
```
monster@monster:~$ cdemu status
ERROR: Failed to connect to CDEmu daemon: org.freedesktop.DBus.Error.ServiceUnknown: The name net.sf.cdemu.CDEMUD_Daemon was not provided by any .service files
ERROR: Failed to connect to daemon!
monster@monster:~$ 

```

when i use the command: sudo cdemud -s, the terminal don't give me an answer..... i can't use other commands if i don't open other tabs....

to get the status you have to tell cdemu as well to use the system bus for 
communication. to do this type the following:
 type the following:

cdemu -b system status



greets,

stevie

---

### Post by Beholder87 on 2008-02-08
well.... i am uninstalling it. like i said, i was going to use it play warcraft dota, but i don't need it anymore....
and after i installed it, my OSS sound stopped working, (cedega has a system tests and the options to sound are: OSS and ALSA. the OSS failed to the cedega test...., however i can listen songs, mp3, videoclips, etc.... but when i try to play warcraft, there is no sound at all in the game...) maybe it is because i installed cdemu ..... i didn't installed anything after cdemu, and my warcraft had perfect sound before....

well thanks for everything anyway
=)

---

### Post by _Stevie_ on 2008-02-08
duh, try if it works with wine. for some games cedega is not even necessary.

---

### Post by Ferrat on 2008-02-13
I found the problem, it's the module for vhba that gets jammed for some reason 

try 

```

$ sudo /etc/init.d/cdemu-daemon restart

```

most likely you will get 
>      * Stopping CDEmu daemon                                [ OK ]                                                          
     * Killing daemon...                                   [[COLOR="Red"]fail[/COLOR]]                                  
     * Removing kernel module (vhba)...                   [[COLOR="Red"]fail[/COLOR]]

So just run 

```

sudo modprobe vhba

```

and then try 


```

$ sudo /etc/init.d/cdemu-daemon restart

```

again and you should get a restart of cdemu

---

### Post by bharadwaj on 2008-04-02
```

sudo modprobe vhba

```

and then try 


```

$ sudo /etc/init.d/cdemu-daemon restart

```

again and you should get a restart of cdemu[/QUOTE]

But when I do that I end up with this result...and the same as before..
```
 sudo /etc/init.d/cdemu-daemon restart
 * Stopping CDEmu daemon                                                         * Killing daemon...                                                     [ OK ] 
 * Removing kernel module (vhba)...                                      [ OK ] 
                                                                         [ OK ]
 * Starting CDEmu daemon                                                         * Inserting kernel module (vhba)...                                     [ OK ] 
 * Waiting for /dev/vhba_ctl to be created: ...                          [ OK ] 
 * Starting daemon...                                                    [fail] 
                                                                         [fail]

```

---

### Post by prometh on 2008-06-19
When I type "sudo modprobe vhba", I get this:

```
FATAL: Module vhba not found.
```

Hell, if I type "sudo modprobe cdemu", I get:

```
FATAL: Module cdemu not found.
```

Hopefully you can help me, as there is no documentation on cdemu.

---

### Post by scrawl on 2008-06-21
I had installed cdemu and it worked fine for a year. But today I got the same problem:

$ sudo /etc/init.d/cdemu-daemon restart
* Stopping CDEmu daemon                         [ OK ]                                     * Killing daemon...                             [fail] 
* Removing kernel module (vhba)...              [fail]   
                                                             
$ sudo update-rc.d -f cdemu-daemon defaults
System startup links for /etc/init.d/cdemu-daemon already exist.

$ sudo modprobe vbha
FATAL: Module vbha not found.

I'm remembering, it didn't work just after the kernel update. Any suggestions?

---

### Post by orbisvicis on 2008-07-06
probably the module is incompatible with the new kernel, so youll have to rebuild it.
If you installed from package, that means uninstall/reinstall

---

### Post by noabody on 2008-07-20
I was messing around with this and kept noticing and errors related to either "system" or "session" bus (Ubuntu 8.04 LTS Hardy).

$ cdemu load 0 test.cue
ERROR: Failed to connect to CDEmu daemon: org.freedesktop.DBus.Error.ServiceUnknown: The name net.sf.cdemu.CDEMUD_Daemon was not provided by any .service files
ERROR: Failed to connect to daemon (bus: 'session')!

A snippet of the cdemu usage below:
Usage: cdemu [options] <command> <command parameters>

Options:
  -b, --bus                 sets D-BUS bus type to use; valid values are 'session' and 'system'


After awhile I realized I needed to run:
$ sudo cdemud -d

So now I try:
$ cdemu status
ERROR: Failed to connect to CDEmu daemon: org.freedesktop.DBus.Error.ServiceUnknown: The name net.sf.cdemu.CDEMUD_Daemon was not provided by any .service files
ERROR: Failed to connect to daemon (bus: 'session')!

Then I try:
$ cdemu status -b system
Devices' status:
DEV   LOADED     TYPE       FILENAME

It seems like we are slaved to the "system" bus. so I try:
$ cdemu load 0 test.cue -b system

This time it works fine.

Starting the cdemu daemon in the session bus doesn't seem to work.  Maybe this will be helpful to someone.

---

### Post by lukemack on 2008-07-21
use acetoneiso instead. much more intuitive and user friendly

[http://www.acetoneiso.netsons.org/viewpage.php?page_id=2](http://www.acetoneiso.netsons.org/viewpage.php?page_id=2)

---

