---
title: "Serial Console connection on Ubuntu 16.04 or higher..."
date: 2016-11-17
forum: General Help
---

### Post by paulstaf on 2016-11-17
I needed to be able to connect to an Ubuntu server via a serial cable.  I have had such a hard time getting this to work, and to automatically run on startup that I thought I would post it here for anyone else needing this functionality.

This doesn't work through grub or the whole boot process, it is just for connecting via a serial cable after the server boots up.

I used a serial cable from my server to another computer.  The server serial port is ttyS0

I created a file under /lib/systemd/system/ called:  ttyS0.service  it has permissions of 644 as such:  -rw-r--r--  1 root root  152 Nov 17 11:33 ttyS0.service

This is what is in the file:

cat /lib/systemd/system/ttyS0.service
------------------------------------------------------------------

[B][Unit]
Description=Serial Console Service

[Service]
ExecStart=/sbin/getty -L 115200 ttyS0 vt102
Restart=always

[Install]
WantedBy=multi-user.target[/B]

------------------------------------------------------------------

After creating, saving, and setting the permissions, I then reloaded systemctl, enabled that service, and then started it:
[B]
sudo systemctl daemon-reload
sudo systemctl enable ttyS0
sudo systemctl start ttyS0[/B]

Then to be on the safe side, I rebooted the server and made sure it came up automatically on bootup.

You can then use any terminal program with a serial cable to connect to the command line of your server.

There are many solutions showing you how to use getty to do this, but the real problem I had was getting it to startup automatically on boot up because of the upstart to systemd change in the newer version of Ubuntu.  That is why I am posting this, in case others had the same frustrations...

---

