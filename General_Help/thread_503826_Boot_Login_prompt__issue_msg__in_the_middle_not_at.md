---
title: "Boot: Login prompt / issue msg : in the middle not at the end of the boot"
date: 2007-07-18
forum: General Help
---

### Post by zimso on 2007-07-18
Hello,

I have gdm turned off. When I boot Feisty, I get the Login prompt at the middle,
look above. At the end it then stops with the last ok. When I press enter
I get the login again. But what I dislike, the first Login prompt with the
issue message comes somewhere before. Can I change this to come really
at the end with the Login: prompt and not having to press enter before ?

Thanks !
Tim

----------------------------------
:
* Starting portmap daemon...                                            [ OK ]
 * Setting up console font and keymap...                                 [ OK ]
 * Loading ACPI modules...
kyron Ubuntu 7.04 kyron tty1   <----------------------- HERE it comes

kyron login:                                                             [ OK ]

* Starting ACPI services...                                              [ OK ]

* Starting system log daemon...                                          [ OK ]

* Doing Wacom setup...                                                   [ OK ]

* Starting kernel log...                                                 [ OK ]

:
:
* Starting powernowd...
/etc/rc2.d/S20powernowd: 156: cannot create /sys/devices/system/cpu/cpu0//cpufreq/scaling_governor: Directory nonexistent
                                          * CPU frequency scaling not supported
                                                                         [ OK ]

* Starting Samba daemons...                                              [ OK ]

* Starting NFS common utilities                                          [ OK ]

* Starting anac(h)ronistic cron anacron                                  [ OK ]

* Starting periodic command scheduler crond                              [ OK ]

* Checking battery state...                                              [ OK ]

* Running local boot scripts (/etc/rc.local)

                                                                         [ OK ]
<-------------- here it stops

Now I press enter and get Login: again...

---

### Post by pointone on 2007-07-18
It might be possible to edit /etc/event.d/tty1 to sleep for a few seconds before running. This would allow the rest of the boot sequence to finish before starting the terminal. Not sure if this will mess up any other processes, though.

You could also add a line in /etc/rc.local to clear the screen or restart the terminal since it's the last script to be run.

---

### Post by Jose Catre-Vandis on 2007-09-24
Has anyone tried pointone's suggestion and if so is this the best way to ensure a server/commandline system boots up to a prompt, instead of sitting on "Running local boot scripts, requiring a return?

How to add a line in rc.local to clear the screen or restart terminal, please?

---

### Post by jalvesaq on 2007-10-31
While I'm waiting for a good solution, I created the script /etc/init.d/restart-tty1 with the following content:

```
#!/bin/sh

stop tty1
clear
start tty1 > /dev/null
```

Then, I turned it executable, went to rc2.d and created a symbolic link:

```
sudo chmod +x restart-tty1
cd ../rc2.d/
sudo ln -s ../init.d/restart-tty1 S99zrestart-tty1
```

I included the letter "z" in the symbolic link name to be sure that it will be the last script to be ran.

---

### Post by Theosa on 2007-11-27
Seems like **Jalvesaq** has already found the solution. Right command in the wrong file, however. First, Ubuntu checks /etc/rc.local script upon boot. When the script exits, it prints [OK] on the screen. This will create disposition. So, we cannot insert the clear command into the /etc/rc.local file

The fact is that when Linux boots up, it goes to 'init 3' level. That's the multiuser one. Every init level has a rc.local file stored in /etc/rcX.d (replace X with numbers of each level).

The solution is simply this:
(Warning: Be extremely careful. This is the bootscipt and if you screw something up, you might have to login with fallback option. So do make a backup of the file!!)

Edit **[COLOR="Red"]/etc/rc3.d/S99rc.local[/COLOR]** **as root** and make sure that the part with do_start seems like this (add the red text in the right location):

do_start() {
if [ -x /etc/rc.local ]; then
                log_begin_msg "Running local boot scripts (/etc/rc.local)"
                /etc/rc.local
                log_end_msg $?
                [COLOR="Red"]stop tty1
                clear
                start tty1 > /dev/null[/COLOR]
        fi
}

Note: The rest of the file should be untouched.

Now reboot and feel happy. =)

---

### Post by jalvesaq on 2007-11-27
Theosa, here, in my desktop, the output of the command "runlevel" is "N 2". But probably your suggestion works for any runlevel because /etc/rc3.d/S99rc.local is just a symbolic link to /etc/init.d/rc.local, which is the file that really is being edited.

Different solutions for this bug have being proposed here:
[https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/65230](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/65230)

---

### Post by Theosa on 2007-11-30
Thanks for the info. =)

---

