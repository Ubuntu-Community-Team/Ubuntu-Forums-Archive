---
title: "The script is correctly configured to be last command run before shutdown ?"
date: 2021-12-10
forum: General Help
---

### Post by aug7744 on 2021-12-10
Hello.

I have created a systemd file in /etc/systemd/system/ to run before shutdown and restart.

Flush.service

[Unit]
Description=Run command before shutdown
DefaultDependencies=no
Before=shutdown.target reboot.target

[Service]
Type=oneshot
User=root
Group=root
ExecStart=/home/user/flush.sh
TimeoutStartSec=0

[Install]
WantedBy=shutdown.target reboot.target

After run the command
sudo systemctl enable flush

I want to the service above run being the last command before system shutdown and restart.
The script is correct ?

Thanks for reply.

---

### Post by TheFu on 2021-12-11
Without actually seeing the script, hard to know.  That's the contents AND the permission.
Does it work?

BTW, having something running with the root account that gets pulled from some user's HOME is poor security. Once you get this working, move it somewhere under root's control.  /usr/local/sbin/ or /root/bin/ would be my choices.

As for what gets run, when, by systemd, I'd have to look in the documentation on freedesktop.org too. [https://www.freedesktop.org/software/systemd/man/systemd.special.html](https://www.freedesktop.org/software/systemd/man/systemd.special.html) has some specific targets that might be more appropriate. Depends on how bulletproof you'd like this process to be when unexpected things happen.

---

### Post by aug7744 on 2021-12-13
#!/bin/bash
dmsetup message /dev/mapper/rc-wb_sda3 0 flush
dmsetup message /dev/mapper/rc-wb_sda5 0 flush
dmsetup message /dev/mapper/rc-wb_sda6 0 flush

exit 0


Thanks for say the correct script path and link with informations.
The command run after OS unmount file system (/opt and /home).
I need configure the script to run before OS will unmount /opt and /home in shutdown.

---

### Post by TheFu on 2021-12-13
Always use the full path to all programs and data locations in scripts.
Also, please use 'code tags' when posting er ... code or terminal output.   [Https://ubuntuforums.org/misc.php?do=bbcode#code](Https://ubuntuforums.org/misc.php?do=bbcode#code)

Above, the dmsetup in the lines need to be 
/usr/sbin/dmsetup

That's the full path to the command. Don't expect environment variables to exist in any script.  Often they do not.

Whether those commands are useful of not, IDK.  I've never needed to do anything like it in multiple decades as an admin.

I guess we don't get to see the permissions?

---

